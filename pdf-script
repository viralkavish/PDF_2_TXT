#!/usr/bin/env python3
#!/usr/bin/env python2

import io
from PIL import Image
from pytesseract import *
from wand.image import Image as wi

pdf = wi(filename = "test_pdf_777.pdf", resolution = 300)
pdfImg = pdf.convert('jpeg')

imgBlobs = []

for img in pdfImg.sequence:
	page = wi(image = img)
	imgBlobs.append(page.make_blob('jpeg'))

extracted_text = []

for imgBlob in imgBlobs:
	im = Image.open(io.BytesIO(imgBlob))
	text = pytesseract.image_to_string(im, lang = 'eng')
	extracted_text.append(text)

print(extracted_text[0])
