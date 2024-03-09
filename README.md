# File Upload Handling Package

This package provides a simple file upload handling functionality for Node.js applications using Express.js and Multer.

## Installation

Install the package using npm:

```bash
npm install file-upload-handler
```

## Usage

1. Require the package in your Node.js application:

```javascript
const express = require('express');
const fileUploadHandler = require('file-upload-handler');
const app = express();
const port = 3000;
```

2. Set up a route for file upload using the `upload` method provided by the package:

```javascript
app.post('/upload', fileUploadHandler.upload.single('file'), (req, res) => {
  if (!req.file) {
    return res.status(400).send('No files were uploaded.');
  }
  res.send('File uploaded successfully!');
});
```

3. Serve the form for file upload:

```javascript
app.get('/', (req, res) => {
  res.sendFile(path.join(__dirname, 'index.html'));
});
```

4. Start the server:

```javascript
app.listen(port, () => {
  console.log(`Server listening at http://localhost:${port}`);
});
```

## HTML Form

You need to create an HTML form for file upload. Here's a sample form:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>File Upload</title>
</head>
<body>
  <h2>File Upload Form</h2>
  <form action="/upload" method="post" enctype="multipart/form-data">
    <input type="file" name="file">
    <button type="submit">Upload</button>
  </form>
</body>
</html>
```

## License

This package is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
