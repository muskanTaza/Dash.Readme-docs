---
title: Upload Document to Tazapay
excerpt: This lets you generate a temporary pre-signed URL to upload your document
api:
  file: sandbox.json
  operationId: get_v3metadatadocupload
deprecated: false
hidden: false
metadata:
  robots: index
---
Once you have pre-signed URL, you can use a PUT request to upload your file on this URL. The document size should be under 50 MB.

### Supported File Types

We currently support the following file formats for upload:

#### 🖼️ Images

* `.jpg`, `.jpeg`, `.png`, `.bmp`, `.tif`, `.gif`, `.ico`, `.webp`

#### 📄 Documents

* `.csv`, `.pdf`, `.doc`, `.docx`, `.odt`, `.ott`, `.rtf`, `.txt`, `.md`, `.tex`

#### 📊 Spreadsheets

* `.xls`, `.xlsx`, `.ods`, `.ots`

#### 📽️ Presentations

* `.ppt`, `.pptx`

#### 📦 Compressed Archives

* `.zip`, `.tar`, `.gz`, `.bz2`, `.xz`, `.7z`, `.rar`

#### 🗂️ Data Formats

* `.json`, `.xml`, `.yaml`, `.yml`