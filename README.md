# SBOMaker

A Software Bill of Materials (SBOM) generator and vulnerability scanner.

## Key Features
- **Automatic Component Discovery**: Automatically finds Web UI, Mobile, and Docker components.
- **Multi-language Support**: Supports various ecosystems including Node.js, Python, Go, Rust, and Java.
- **Vulnerability Scanning**: Integrates with Grype to identify security vulnerabilities.
- **Combined Project Reports**: Generates a unified SBOM and a comprehensive Markdown report.

## Quick Start
To generate an SBOM for your project, run, in the project's folder:
```bash
chmod +x SBOMaker.sh
./SBOMaker.sh
```

## Documentation
For detailed information on configuration and usage, please refer to the [Documentation](docs/sbom-update.md).
