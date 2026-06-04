# Make Slide Deck from Markdown to PDF

## Prompt History

These are the prompts used to create the slide deck from `index.md`:

### 1. Create slide deck (HTML)
```
create slide deck. one slide per section. html format.
```

### 2. Remove nav buttons + change color theme
```
Remove nav buttons and change color theme to crimson.
```

### 3. Adjust page number placement
```
page number on the bottom takes too much space. remove it and add page number on the bottom left.
```

### 4. Apply styling suggestions
```
Can you provide styling suggestion? font size, layout, etc.
```
```
yes
```

### 5. Save to PDF
```
can you save the content of slide deck to pdf format?
```

### 6. Fix Chrome dependencies
```
install Chroma dependencies
```
Then run in terminal:
```bash
sudo apt-get install -y libnspr4 libnss3 libatk1.0-0 libatk-bridge2.0-0 libcups2 libdrm2 libxkbcommon0 libxcomposite1 libxdamage1 libxrandr2 libgbm1 libasound2t64 libpango-1.0-0 libcairo2 libxshmfence1
```

### 7. Regenerate PDF
```
save to pdf again
```

### 8. Use 16:9 ratio
```
use 16:9 screen ratio
```

### 9. Fix clipped content
```
내용이 16:9 비율보다 길어서 짤리네요. pdf 로 만들기 전에 내용 크기 조절 필요. 다시 pdf 만들어줘요.
```
(Content was clipped because it was longer than 16:9 ratio. Need to adjust content size before making PDF. Please make the PDF again.)

### 10. Fix broken layout
```
pdf 파일의 내용이 레이아웃이 엉망인데 원은 무엇인가
```
(Why is the PDF layout broken?)

**Root cause**: `page.pdf()` conflicts with CSS `position: absolute` slides and injected print CSS overrides. **Solution**: Use screenshot + pdf-lib method instead.

---

## Prerequisites

```bash
# Install Node.js dependencies
npm install puppeteer pdf-lib
```

## Step 1: Create HTML Slide Deck

Create an HTML file (`slide_deck.html`) with one `<div class="slide">` per section.

### Key HTML Structure

```html
<div class="slide-container">
  <div class="slide title-slide active" data-index="0">...</div>
  <div class="slide" data-index="1">...</div>
  ...
</div>
```

### JavaScript for Slide Navigation

```javascript
const slides = document.querySelectorAll('.slide');
let current = 0;

function showSlide(index) {
  slides.forEach((s, i) => {
    s.classList.remove('active', 'exit-left');
    if (i === index) s.classList.add('active');
    else if (i < index) s.classList.add('exit-left');
  });
  document.getElementById('slideCounter').textContent = `${index + 1} / ${slides.length}`;
  document.getElementById('progressBar').style.width = ((index + 1) / slides.length * 100) + '%';
}

// Keyboard navigation
document.addEventListener('keydown', e => {
  if (e.key === 'ArrowLeft' && current > 0) showSlide(--current);
  if (e.key === 'ArrowRight' && current < slides.length - 1) showSlide(++current);
});
```

## Step 2: Generate PDF

### Method: Screenshot + pdf-lib (Recommended)

This method captures each slide as a screenshot image and combines them into a PDF. It preserves the exact HTML layout without CSS conflicts.

### Script (`generate_pdf.mjs`)

```javascript
import puppeteer from 'puppeteer';
import { PDFDocument } from 'pdf-lib';
import { writeFileSync } from 'fs';

const htmlPath = '/path/to/slide_deck.html';
const outputPath = '/path/to/slide_deck.pdf';

const browser = await puppeteer.launch({
  headless: true,
  args: ['--no-sandbox', '--disable-setuid-sandbox']
});

const page = await browser.newPage();

// Set viewport to 16:9 ratio with 2x DPI
await page.setViewport({ width: 1920, height: 1080, deviceScaleFactor: 2 });
await page.goto(`file://${htmlPath}`, { waitUntil: 'networkidle0' });

const totalSlides = await page.evaluate(
  () => document.querySelectorAll('.slide').length
);

// Capture each slide as a PNG screenshot
const screenshots = [];
for (let i = 0; i < totalSlides; i++) {
  await page.evaluate((idx) => window.showSlide(idx), i);
  await new Promise(r => setTimeout(r, 500)); // wait for transition
  const buf = await page.screenshot({
    type: 'png',
    clip: { x: 0, y: 0, width: 1920, height: 1080 }
  });
  screenshots.push(buf);
}
await browser.close();

// Combine screenshots into PDF with 16:9 page size
const pdfDoc = await PDFDocument.create();
for (const buf of screenshots) {
  const pngImage = await pdfDoc.embedPng(buf);
  const page = pdfDoc.addPage([256, 144]); // 16:9 in mm
  page.drawImage(pngImage, {
    x: 0,
    y: 0,
    width: 256,
    height: 144,
  });
}

const pdfBytes = await pdfDoc.save();
writeFileSync(outputPath, pdfBytes);
console.log(`PDF saved to ${outputPath}`);
```

### Run

```bash
node generate_pdf.mjs
```

## Page Size Options

| Ratio | Width x Height (mm) |
|-------|---------------------|
| 16:9  | 256 x 144           |
| 16:10 | 256 x 160           |
| 4:3   | 256 x 192           |
| A4 Landscape | 297 x 210  |

Change `addPage([256, 144])` and viewport to match your desired ratio.

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Chrome shared library errors | `sudo apt-get install -y libnspr4 libnss3 libatk1.0-0 libatk-bridge2.0-0 libcups2 libdrm2 libxkbcommon0 libxcomposite1 libxdamage1 libxrandr2 libgbm1 libasound2t64 libpango-1.0-0 libcairo2 libxshmfence1` |
| Content gets clipped in PDF | Use the screenshot method (above), not `page.pdf()` directly |
| Layout broken in PDF | The `page.pdf()` method conflicts with CSS `position: absolute` slides. Screenshot method avoids this |
| Slides overlap | Each slide must have `window.showSlide(idx)` exposed globally for the script to navigate |
