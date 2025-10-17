# Captcha Solver (Browser, Tesseract.js) — MIT

## Overview
This is a single-page, browser-based captcha solver that uses Tesseract.js to OCR text from an image. It accepts a captcha image URL via the query parameter ?url=https://.../image.png, displays the image, performs light preprocessing, and shows the solved text. If no URL is provided, it defaults to a generated sample captcha.

Key features:
- URL parameter support: pass ?url=...
- In-browser OCR via Tesseract.js (no server required)
- Image preprocessing (grayscale + Otsu threshold + scaling)
- Solves most simple single-word/line captchas within ~15 seconds
- Copy-to-clipboard for solved text

Note: Cross-origin images must permit CORS for preprocessing (and OCR worker fetch) to work.

## Setup
- No build step is required.
- Open index.html in a modern browser.
- Internet access is required to download the OCR engine and English language data from CDNs.

CDNs used:
- Tesseract.js: https://cdn.jsdelivr.net/npm/tesseract.js
- Trained data (eng): https://tessdata.projectnaptha.com/4.0.0

To run fully offline, host those assets yourself and update the script/paths accordingly.

## Usage
- Navigate to: index.html?url=https://example.com/captcha.png
- The page will:
  - Display the specified captcha image
  - Preprocess it for OCR
  - Solve and display the recognized text and approximate confidence

Controls:
- Input: Paste a captcha URL.
- Solve: Starts OCR on the provided URL.
- Sample: Generates and solves a local sample captcha if you don’t have a URL.
- Copy: Copies the solved text.

Tips for best results:
- Provide a clear, high-contrast image with one word/line of text.
- Avoid animated images or multi-line captchas.
- Ensure the remote server sets appropriate CORS headers (Access-Control-Allow-Origin) so the browser can load/process the image.

## License
MIT License

Copyright (c) 2025

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.