# QR Code Generator

<div align="center">
  <img src="https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
  <img src="https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge" alt="MIT License">
</div>

<p align="center">
  <img src="https://raw.githubusercontent.com/Soham1250/QR_Code_generator/main/qr_img.png" width="200" alt="QR Code Example">
</p>

<p align="center">
  <b>A simple CLI tool to generate QR codes from URLs</b>
</p>

## Overview

> **⚠️ Learning Project Notice**
> 
> This project was developed as a learning exercise to practice Node.js development and working with npm packages. It is a simple demonstration project intended for educational purposes and may not include all the features or optimizations of a production-ready application.

QR Code Generator is a lightweight, command-line Node.js application that allows you to quickly generate QR codes from any URL. The application prompts you for a URL, generates a QR code image, and saves both the image and the URL for future reference.

### Key Features

- **Simple CLI Interface**: Easy-to-use command-line interface
- **QR Code Generation**: Convert any URL into a QR code image
- **Automatic Saving**: Saves both the QR code image and URL text file
- **Fast & Lightweight**: Minimal dependencies for quick execution

## Technology Stack

- **Node.js**: JavaScript runtime environment
- **inquirer**: Interactive command-line user interface
- **qr-image**: QR code generation library
- **fs**: Native Node.js file system module

## Project Structure

```
qr-code-generator/
├── index.js           # Main application file
├── package.json       # Project dependencies and configuration
├── qr_img.png         # Generated QR code image (example)
├── URL.txt            # Saved URL (example)
└── README.md          # Project documentation
```

## Getting Started

### Prerequisites

- Node.js (v14.0.0 or higher)
- npm (v6.0.0 or higher)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Soham1250/QR_Code_generator.git
   ```

2. Navigate to the project directory:
   ```bash
   cd QR_Code_generator
   ```

3. Install dependencies:
   ```bash
   npm install
   ```

### Usage

1. Run the application:
   ```bash
   node index.js
   ```

2. When prompted, enter the URL you want to convert to a QR code:
   ```
   ? Enter your url: https://example.com
   ```

3. The application will generate:
   - A QR code image (`qr_img.png`) in the project directory
   - A text file (`URL.txt`) containing the URL you entered

4. You'll see a confirmation message:
   ```
   QR code saved as qr_img.png and URL saved as URL.txt
   ```

## Code Example

Here's how the application works:

```javascript
import qr from 'qr-image';
import fs from 'fs';
import inquirer from 'inquirer';

inquirer
    .prompt([
        {
            message: "Enter your url: ",
            name: "url",
        }
    ])
    .then((answers) => {
        const url = answers.url;
        var qr_svg = qr.image(url);
        qr_svg.pipe(fs.createWriteStream("qr_img.png"));

        fs.writeFile("URL.txt", url, (err)=>{
            if(err){throw err;}
            console.log("QR code saved as qr_img.png and URL saved as URL.txt");
        })
    });
```

## Future Enhancements

- **Customization Options**: Allow users to customize QR code colors and size
- **Multiple Formats**: Support for different image formats (SVG, PDF, etc.)
- **Batch Processing**: Generate multiple QR codes from a list of URLs
- **Web Interface**: Add a simple web interface for non-technical users
- **QR Code Reading**: Add functionality to read and decode QR codes

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributors

- Soham Pansare - Project Creator & Developer

---

<p align="center">
  <i>Made with ❤️ for quick and easy QR code generation</i>
</p>
