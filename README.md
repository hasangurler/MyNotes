# MyNotes

A lightweight, responsive, and installable notes application built with standard web technologies.

MyNotes demonstrates how a modern web application can provide a **cross-platform application experience from a single codebase**, without requiring a native application framework or backend infrastructure.

The application can be used directly in a web browser, while supported browsers can also install it as a standalone application on desktop and mobile devices.

## Features

* Create, edit, and delete notes
* Search notes by title or content
* Sort notes by:

  * Last updated
  * Creation date
  * Title
  * Manual order
* Drag and drop manual note ordering
* Light and dark themes
* Responsive design for desktop, tablet, and mobile devices
* Character counters for note title and content
* Form validation
* Confirmation dialogs for important and destructive actions
* Toast notifications
* Keyboard shortcuts
* Local data storage using `localStorage`
* Backup notes to a JSON file
* Restore notes from a JSON backup
* Installable as a Progressive Web App (PWA)
* Offline-capable application architecture
* No backend or database required

## Why MyNotes?

MyNotes is more than a simple notes application.

The project is intended to demonstrate an important capability of modern web development:

> A web application can be built once and delivered across multiple platforms without maintaining separate native applications.

The same application can run in a browser and, when installed as a PWA, provide an application-like experience on supported desktop and mobile platforms.

This approach can significantly reduce development and maintenance costs for applications that do not require platform-specific native functionality.

## Technologies

MyNotes is built using standard web technologies and a small number of frontend libraries:

* HTML5
* CSS3
* JavaScript (ES6+)
* Bootstrap
* Bootstrap Icons
* Web Storage API
* File API
* Web Share API
* Service Worker API
* Progressive Web App (PWA) technologies

The application does not use a frontend framework such as React, Angular, or Vue.

There is also no server-side component or external database.

### Local Vendor Dependencies

The project includes the required Bootstrap and Bootstrap Icons files locally in the `vendor/` directory.

```text id="6d6n3h"
vendor/
├── bootstrap.bundle.min.js
├── bootstrap.min.css
├── bootstrap-icons.css
└── fonts/
    ├── bootstrap-icons.woff
    └── bootstrap-icons.woff2
```

Keeping these dependencies locally allows the application to load its frontend resources without relying on an external CDN.

This is particularly useful for a PWA because the application is intended to remain functional even when network connectivity is unavailable.

## Project Structure

```text id="q3m4n7"
MyNotes/
│
├── index.html
├── style.css
├── app.js
│
├── manifest.json
├── service-worker.js
│
├── icons/
│   ├── icon-192.png
│   └── icon-512.png
│
├── vendor/
│   ├── bootstrap.bundle.min.js
│   ├── bootstrap.min.css
│   ├── bootstrap-icons.css
│   └── fonts/
│       ├── bootstrap-icons.woff
│       └── bootstrap-icons.woff2
│
├── README.md
├── LICENSE
└── .gitignore
```

### `index.html`

Defines the application's user interface and document structure.

It contains the main application layout, toolbar, search and sorting controls, note cards container, note editing form, confirmation modal, and notification container.

It also connects the application to the PWA manifest and required frontend resources.

### `style.css`

Contains the application's custom styling.

Bootstrap provides the general UI framework, while `style.css` defines the MyNotes-specific visual layer, including:

* Application themes
* Note card appearance
* Responsive behavior
* Empty states
* Modal styling
* Note colors
* Drag and drop states
* Mobile-specific layout adjustments

### `app.js`

Contains the application's core functionality and business logic.

The JavaScript layer manages:

* Application state
* Note creation, editing, and deletion
* Local storage
* Searching and sorting
* Manual ordering
* Drag and drop
* Backup and restore
* Theme selection
* Form validation
* Character counters
* Confirmation dialogs
* Toast notifications
* Keyboard interaction

### `manifest.json`

Defines the Progressive Web App metadata, including:

* Application name
* Application icon
* Start URL
* Display mode
* Orientation
* Theme color
* Background color

This allows supported browsers to install MyNotes as an application.

### `service-worker.js`

Provides the service worker layer required for the application's offline-capable architecture.

It allows application resources to be cached so that MyNotes can continue to work when network connectivity is unavailable.

## Data Storage

MyNotes does not require a backend or database.

Notes are stored locally in the browser using the Web Storage API (`localStorage`).

This design has several advantages:

* No server is required
* No account is required
* No database configuration is required
* Data remains available offline
* The application can be hosted as a static website

The trade-off is that data is associated with the browser/device where it was created.

For this reason, MyNotes includes **JSON backup and restore functionality**.

Users can export their notes to a JSON file and restore them later on another supported browser or device.

## Cross-Platform Approach

One of the primary goals of MyNotes is demonstrating how a single web application can target multiple environments.

The same source code can be used through:

```text id="7y8r2m"
Web Browser
     │
     ├── Desktop
     ├── Tablet
     └── Mobile
     
        +
        
Progressive Web App
        │
        ├── Installable
        ├── Standalone experience
        └── Offline-capable
```

Instead of developing separate applications for different operating systems, the application uses standard web APIs and responsive design to adapt to different environments.

This does not mean that PWAs replace native applications in every scenario. Applications requiring extensive platform-specific capabilities may still benefit from native development or specialized cross-platform frameworks.

For applications such as notes, task management, documentation, lightweight productivity tools, and many business applications, however, a PWA can be a practical alternative.

## Running Locally

MyNotes is a static web application.

For basic development, the project can be served using any local HTTP server.

For example, with Python installed:

```bash id="7u0d2s"
python -m http.server 8000
```

Then open:

```text id="2q8y4c"
http://localhost:8000
```

> A local HTTP server is recommended instead of opening `index.html` directly with `file://`, especially when testing service workers and PWA functionality.

## Installing MyNotes

When served from a supported secure context, compatible browsers can offer an option to install MyNotes.

After installation, the application can appear as a standalone application rather than a normal browser tab.

Installation support and available PWA features depend on the browser and operating system.

## Offline Usage

The application is designed to support offline usage through the combination of:

* Local Storage
* Service Worker
* Cached application resources
* Client-side application logic

The application also keeps its Bootstrap and Bootstrap Icons dependencies locally rather than loading them from a CDN.

Once the required resources have been cached, MyNotes can operate without an active internet connection.

## Backup and Restore

Because notes are stored locally, MyNotes provides a built-in backup mechanism.

Users can:

1. Export their notes as a JSON file.
2. Keep the backup file independently.
3. Restore their notes from the JSON file when needed.

This also provides a simple mechanism for transferring notes between devices.

## Security and Privacy

MyNotes does not send note contents to a remote server.

The application is designed around client-side storage, meaning that note data remains within the browser's local storage unless the user explicitly exports it.

However, local browser storage should not be considered a replacement for encrypted storage or a secure password manager.

Users should also keep independent backups of important information.

## Browser Compatibility

MyNotes uses modern web platform features such as:

* ES6+ JavaScript
* Web Storage API
* File API
* Service Workers
* Web Share API
* CSS responsive features

Browser support therefore depends on the implementation of these features.

The Web Share API is used when available, with a traditional file-download mechanism provided as a fallback.

## Development Goals

The project was created with several goals in mind:

1. Build a useful application rather than a purely theoretical example.
2. Demonstrate how standard web technologies can be combined into a complete application.
3. Explore the Progressive Web App model.
4. Provide a responsive experience across different screen sizes.
5. Avoid unnecessary backend infrastructure.
6. Keep the source code understandable and accessible to developers.
7. Demonstrate how browser APIs can provide functionality traditionally associated with installed applications.
8. Keep essential frontend dependencies locally available for offline use.

## Future Improvements

Potential future improvements may include:

* Additional note organization features
* Tags and categories
* More advanced search
* Import/export format improvements
* Additional PWA capabilities
* Enhanced accessibility
* Automated testing
* Performance improvements

## Contributing

Contributions, suggestions, and improvements are welcome.

If you find a bug or have an idea for improving the application, feel free to open an issue or submit a pull request.

When submitting changes, please try to keep the code consistent with the existing project structure and coding style.

## License

MyNotes is released under the MIT License.

See the [LICENSE](LICENSE) file for details.

## Author

Developed as an example of building a practical, cross-platform web application using modern web standards.
