# Häxhatten

![PHP](https://img.shields.io/badge/PHP-8.1-blue)
![License](https://img.shields.io/badge/License-GNU-green)

GNU GENERAL PUBLIC LICENSE
                       Version 3, 29 June 2007

Copyright (C) 2026 Monica Hart

Everyone is permitted to copy and distribute verbatim copies
of this license document, but changing it is not allowed.

[Full license text follows — you can copy from https://www.gnu.org/licenses/gpl-3.0.txt]

Häxhatten is a security-first PHP framework designed for modular applications, dynamic templates, and safe integration of third-party plugins. It assumes all code may be hostile and enforces both static and runtime security checks, while keeping HTML output clean and structured.

---

## Problem

Building secure, modular PHP applications often requires trusting third-party code, which can introduce vulnerabilities. Many PHP frameworks lack fine-grained runtime checks, AST-based security scanning, and structured template management. This can lead to duplicated output, malformed HTML, and potential security risks.

## Solution

Häxhatten enforces a **security-first approach** by:

- Using AST parsing to detect unsafe PHP function calls
- Configurable Blacklist/Whitelist policies for PHP code
- Centralized error logging and localized messages
- A modular template system for `Body`, `Footer`, `SideNav`, `TopNav`, `Meta`, `Title`, and more
- Automatic template creation and dynamic template selection
- Safe, pluggable application integration

This allows developers to build complex PHP applications with confidence, avoiding common pitfalls like duplicate output or unsafe third-party scripts.

---

## Features

- **Secure Template Engine** – Multi-section templates with placeholder replacement
- **AST-based PHP Security Scanner** – Detects and blocks disallowed functions
- **Error Logging & Localization** – Centralized, traceable, and language-aware
- **Dynamic Application Loader** – Auto-detects and integrates apps from a directory
- **Content and Navigation Separation** – Supports `Body`, `SideNav`, `TopNav`, `Footer`, etc.
- **Template Auto-Generation** – Prevents runtime errors by creating default templates
- **Development Mode** – Live template generation and testing
- **Pluggable App Architecture** – Applications extend the `application` base class
- **JavaScript & Script Sections** – Separate handling for header, body, and footer scripts
- **Session-based Template Selection** – Allows per-session UI/theme choice
- **Logging & Audit Trail** – Automatic log files for errors and violations

---

## Coming Soon

- **Database Integration** – Full `DBConnect()` and query support
- **Application Installer & Updater** – Install trusted apps from tarballs, manage versions
- **AST-based JavaScript Scanner** – Detect unsafe client-side scripts
- **UI Theme Manager** – Switch between multiple templates dynamically
- **Enhanced Error Pages** – Styled, user-friendly error outputs
- **Plugin Sandbox** – Safe execution of third-party plugins
- **Menu Builder** – Visual interface for `SideNav` and `TopNav`
- **Mobile Optimization** – Responsive menus and layouts
- **Script Dependency Management** – Auto-inclusion of JS/CSS files with versioning

---

## Installation

1. Clone the repository to your web server:

```bash
git clone https://github.com/yourusername/Haxhatten.git
Ensure your server runs PHP 8.1+.
Create a config.ini file in the document root with your system configuration:
[System]
DevMode=true
DefaultLang=en-US
Blockmode=Blacklist
LogDir=logs
ApplicationsDirectory=apps

[UI]
Default=FreyjaOne

[BlockmodeList]
PHP=exec,shell_exec,system
HTML=<script>
SQL=DROP,DELETE
Set permissions for the Templates and logs directories to allow PHP read/write.
Access index.php in your browser to see Häxhatten in action.
Usage
Extend the application class to create new apps.
Implement the section methods:
class MyApp extends application {
    public static function Body(): string { return 'Hello World'; }
    public static function SideNav(): array { return []; }
    // Other sections... see app./test.inc for examples.
}
Place your app .inc files in the configured ApplicationsDirectory.
Häxhatten automatically loads apps, parses templates, and renders output safely.
Contributing

Contributions are welcome! Please fork the repo, create a branch for your feature or bugfix, and submit a pull request.

License

MIT License © 2026 Monica Hart
