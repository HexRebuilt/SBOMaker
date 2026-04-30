# SBOMaker Documentation

## Overview
SBOMaker is a professional tool designed to generate a Software Bill of Materials (SBOM) and scan for vulnerabilities across multiple project components (Web UI, Mobile, Docker, and Generic apps).

## Installation
### Prerequisites
- **syft**: For SBOM generation.
- **grype**: For vulnerability scanning.
- **jq**: For JSON processing.

The script will attempt to install `syft` and `grype` automatically if they are missing (via Homebrew on macOS or curl on Linux).

### Setup
1. Clone the repository.
2. Make the script executable:
   ```bash
   chmod +x update-sbom.sh
   ```

## Usage
Run the script from the project root:
```bash
./update-sbom.sh [OPTIONS]
```

### Options
- `--webui`: Generate SBOM for Web UI only.
- `--mobile`: Generate SBOM for Mobile App only.
- `--docker`: Generate SBOM for Docker Image only.
- `--all`: Generate SBOM for all components (default).
- `--no-fail`: Do not exit with error if vulnerabilities or outdated dependencies are found.
- `--docker-image <image>`: Specify a custom Docker image name.

## Configuration
You can create a `.sbom-config.json` file in the project root to customize paths and exclusions.

### Example `.sbom-config.json`
```json
{
  "sbom_dir": "sbom_reports",
  "webui": {
    "path": "src/web",
    "excludes": ["**/node_modules/**", "**/dist/**"]
  },
  "mobile": {
    "path": "src/mobile",
    "ios_path": "src/mobile/ios",
    "excludes": ["**/node_modules/**"]
  },
  "docker": {
    "image": "my-app:latest"
  },
  "generic": {
    "python-app": "src/backend"
  }
}
```

## Output
The script generates reports in the `sbom/` directory (or the directory specified in config):
- `sbom-combined-[date].json`: A merged SBOM of all components.
- `REPORT-[date].md`: A comprehensive Markdown report including vulnerability summaries and outdated dependency lists.
- `webui/`, `mobile/`, `docker/`, `generic/`: Component-specific SBOMs and scan results.
