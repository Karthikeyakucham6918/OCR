# OCR Model Usage
This Python script demonstrates how to use a pre-trained OCR model to extract text from a PDF document.

# Installation
Make sure you have Python installed on your system. You can install the required packages using pip:

```bash
pip install doctr
```
#Usage

Import the necessary modules:

```python
from doctr.io import DocumentFile
from doctr.models import ocr_predictor
import json
```
Initialize a pre-trained OCR model:

```python
model = ocr_predictor(pretrained=True)
```
Load a PDF document:

```python
doc = DocumentFile.from_pdf("your_pdf_file.pdf")
```
Perform OCR analysis on the document:

```python
result = model(doc)
```
Display the OCR result:

```python
result.show()
```
Export the result to JSON:

```python
json_response = result.export()
Extract words from the JSON response:
python
Copy code
def extract_words(data):
    words = []
    for page in data["pages"]:
        for block in page["blocks"]:
            for line in block["lines"]:
                for word in line["words"]:
                    words.append(word["value"])
    return words

extracted_words = extract_words(json_response)
print(extracted_words)
```
# Requirements
Python 3.6+

doctr

Other dependencies as required by the OCR model