# Project Description:

Financial institutions process and store a large volume of consumer
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

2) After the document is classified and split, create a library that accepts split
   documents and extracts the data from them.

The library built should be scalable and secure enough to process millions of files.

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

# Steps:
### 1) Taking inputs of documents in different formats (Image / PDF / Word) and 
### converting them to single type of format (Image)
```
function:
(Image / PDF / Word) --> (Image)
```

### 2) Image Processing:
Preparing the images for text extraction:
```
function: 
(Image) --> (Extractable Image [EI], Reference to original image [OI])
```

### 3) Text Extraction:
Using text extraction technologies to extract text from images:
```
function: 
([EI], [OI]) --> (Extracted Text [ET], Reference to [OI])
```

### 4) Classifying Images:

---
prerequisite:
- Unique words extracted either (manually or using TD-IDF over training dataset)
- This step is totally independent of the main process.
- This step is to be performed before using the main program or library
- This step should be the prerequisite without which step 4 and above are not 
possible.
- This step requires manual labelling of the type of images being fed.
- Example: For Aadhar Images input Aadhar Card, Pan Card for Pan Card Images, 
and so on.
```
function:
(TD-IDF(list[OI], list[ET], DT)) --> ([UK] -- DT)
```
---

Classifying the [OI] based on [ET] and the unique keywords [UK] corresponding to
the document types [DT].
```
function:
(
Loop above for list of ([UK] -- DT):
  [ET] * [UK] --> Percentage DT;
Loop above for list of [DT]
  DT = Max(Percentage)
) --> (DT, Reference to [ET], Reference to [OI])
```

### 5) Extract Data:
prerequisite:
Unique algorithms [UA] to extract document specific data.

Extracting crucial data from [ET] based on DT and then attaching the same to
the OI and pack them into a dictionary data type
```
function:
(UA(DT, ET, OI)) --> (DICT)
```

# Footnote:
[^1]: The image processing step is one of the most crucial and bottleneck steps in the project.

[^2]: For accurate results, text extraction technologies require clean inputs.
For this particular project, this represents another bottleneck.

[^3]: For classifying images we first have to feed the algorithm with unique words. These unique words are specific to each document. To extract such unique words two methods are possible (manual input or using TD-IDF).

[^4]: Crucial data are subjective and differ from document to document. However, this data is common to the same type of document.
The Aadhar number, name, DOB, etc, are crucial to the Aadhar card document.. 
Pan Card Number is specific to the Pan document. 
Driving License number is specific to driving license document, and so on.
