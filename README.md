# Book-reading-platform
# 📚 Smart PDF Library

A lightweight, browser-based PDF reader and manager built with Vanilla JavaScript, HTML, and CSS. This application allows you to read, highlight, and manage your PDFs entirely offline, with built-in tools for dictionary lookups and translations. 

Your files and reading progress are stored locally in your browser using IndexedDB, ensuring complete privacy and fast loading times.

## ✨ Features

* **🗄️ Local Library Management:** Upload PDFs directly into the browser. Files are stored locally via IndexedDB, meaning they persist even if you close the tab.
* **🖍️ Persistent Highlighting:** Select text to highlight it. Highlights are saved to the database and will be there the next time you open the document.
* **📥 Download Highlighted PDFs:** Export your original PDF with all your custom highlights embedded permanently into the file.
* **📖 Smart Tooltip Interactions:** Select any text to instantly:
    * Get dictionary definitions and phonetic pronunciations (via Dictionary API).
    * Search the web for the selected phrase.
    * Translate the text using Google Translate.
* **🌗 Dark Mode:** Toggle between light and dark themes for comfortable reading in any environment.
* **📱 Responsive UI:** Features a collapsible sidebar and scalable canvas elements to work on both desktop and mobile screens.
* **🔖 State Memory:** Remembers your exact zoom level and the last page you were reading for every individual book in your library.

## 🛠️ Technologies Used

* **Frontend:** HTML5, CSS3, Vanilla JavaScript
* **PDF Rendering:** [PDF.js (v2.16.105)](https://mozilla.github.io/pdf.js/) by Mozilla
* **PDF Manipulation:** [PDF-lib (v1.17.1)](https://pdf-lib.js.org/) for injecting highlights and exporting documents
* **Storage:** Browser `IndexedDB` API
* **Dictionary Data:** [Free Dictionary API](https://dictionaryapi.dev/)

## 🚀 Getting Started

Because this application relies on client-side technologies and CDN-hosted libraries, there is no build step or server required.

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/Fourier-Laplace-0/Book-reading-platform.git
    ```
2.  **Open the application:**
    Simply double-click the `index.html` file to open it in your preferred modern web browser (Chrome, Firefox, Edge, Safari).
    
    *Alternatively, you can serve it via a simple local server if you prefer:*
    ```bash
    # If using Python 3
    python -m http.server 8000
    ```
    Then navigate to `http://localhost:8000` in your browser.

## 🧠 How it Works

1.  **Storage:** When a user uploads a PDF, it is converted to an `ArrayBuffer` and saved in an IndexedDB database named `SmartPDFDB`.
2.  **Rendering:** `PDF.js` fetches the `ArrayBuffer` from the database, renders the PDF pages onto HTML `<canvas>` elements, and overlays an invisible text layer to allow for text selection.
3.  **Highlighting:** When text is selected, the app calculates the DOM coordinates, creates visual `div` highlights, and saves the relative coordinates to the database.
4.  **Exporting:** When the "Download" button is clicked, `PDF-lib` loads the original PDF binary, scales the saved highlight coordinates to match the raw PDF coordinate system (bottom-left origin), draws the yellow rectangles, and triggers a file download.

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! 
Feel free to check the [issues page](https://github.com/Fourier-Laplace-0/Book-reading-platform/issues) if you want to contribute.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.
