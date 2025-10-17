# Captcha Solver (Browser, Tesseract.js)

MIT-licensed single-page web app that loads a captcha image from the `?url=` query parameter, preprocesses it in-canvas, and performs OCR in the browser using Tesseract.js to display the solved text. If no URL is provided, a built-in sample image is used.

## Overview

- Loads image from `?url=https://.../image.png` (or any supported image format/URL).
- Displays both the original and a preprocessed version (grayscale, optional denoise, binarization, invert).
- Solves using Tesseract.js with:
  - Language: `eng`
  - Page segmentation mode: single line
  - Character whitelist: A–Z, a–z, 0–9
- Attempts to show a result within ~15 seconds.
- No server required; runs entirely in the browser.

## Setup

- No build required. This is a static web app.
- Files:
  - index.html
  - README.md (this file, includes the MIT license)

You can open `index.html` directly in a browser or serve it with any static server.

Examples:
- Python: `python3 -m http.server 8080`
- Node: `npx serve .`
- Bun: `bunx serve .`

## Usage

- Navigate to: `http://localhost:8080/index.html?url=https://example.com/captcha.png`
- The page will:
  1. Show the image.
  2. Preprocess it.
  3. Run OCR and display the solved text.

Controls:
- URL input: paste a new image URL and click Solve.
- Sample: loads a built-in sample captcha if you don’t have a URL.
- Preprocessing toggles:
  - Invert: invert black/white if necessary.
  - Binarize: Otsu thresholding for cleaner foreground/background separation.
  - Denoise: simple median filter to reduce small noise.
  - Scale: upscales image to help OCR.

Notes and tips:
- Cross-origin images must allow CORS for pixel access when preprocessing/OCR. If the image server doesn’t set permissive CORS headers, the app may not be able to process the image. Use same-origin or CORS-enabled URLs.
- For best results, pass relatively clean, single-line captchas comprised of alphanumeric characters.
- The app initializes Tesseract in the background on load to reduce latency before the first solve.

## License

MIT License

Copyright (c) 2025

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.