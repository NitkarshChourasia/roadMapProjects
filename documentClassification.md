# Project Description:

Financial institutions will process and keep a massive volume of consumer
documents. These documents are crucial to the company's operations, and there
are statutory obligations on how they must be processed and stored. To identify
the documents and extract data from them, a significant amount of human
processing is required.

1) Based on the input file, the documents must be identified, classified, and 
divided into multiple groups. The user can submit a single file (image/pdf/word 
document) that contains many documents. Create a library that accepts a user 
supplied file and recognises and splits numerous documents existing in the file.
Documents to be classified and split are:

| Documents | Organization |
| ----------- |  ----------- |
| PAN | Government |
| Aadhaar (Aadhaar front, Aadhaar back) | Government |
| Bank Statement | Financial |
| ITR/Form 16 | Financial |
| Customer Photograph (Selfie) | Personal |
| Utility Bill (Power, Water, Gas, Landline etc) | Financial |
| Cheque Leaf | Financial |
| Salary Slip/Certificate | Financial |
| Driving License | Government |
| Voter ID | Government |
| Passport | Government |

2) Once document is classified and split, create a library which accepts split
document and extracts the data from it.

The library built should be scalable and secure to process millions of files.

# Objectives:

1) Input Document
2) Classify
3) Extract

# Roadmap:

1) Taking inputs of documents in different formats: Image / PDF / Word
2) Converting the inputs to single type of format: Image
3) Process the Image. [^1]
4) Use OCR to extract text. [^2]
5) Classify the Image based on extracted text. [^3]
6) Use the extracted text to further extract crucial data. [^4]

# Footnote:
[^1]: Image processing is the most crucial and bottleneck step of the project.

[^2]: Text Extraction technologies expect clean inputs for accurate results.
This is another bottleneck step for this particular project.

[^3]: For classifying Images we first have to feed the algorithm with
unique words. This unique words are document specific. To extract such unique
words two methods are possible (manual input or using TD-IDF)

[^4]: Crucial data are subjective and differ from document to document. But this
data is common around same type of document.
Example: Aadhar number, Name, DOB, etc. are crucial for Aadhar document. Pan Card
Number is specific to Pan document. Driving License number is specific to driving 
license document, and so on.
