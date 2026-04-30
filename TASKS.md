# Tasks: Remove Hardcoded Docker Image Default

## Goal
Remove the hardcoded `sbomaker:latest` default for `DOCKER_IMAGE` in `update-sbom.sh` and improve error reporting when no image is specified.

## Plan

### 1. Implementation
- [ ] Remove hardcoded default value for `DOCKER_IMAGE` in `update-sbom.sh` (set to `""`).
- [ ] Update `--help` text in `update-sbom.sh` to remove `(default: sbomaker:latest)`.
- [ ] Update `generate_docker_sbom` function in `update-sbom.sh`:
    - After attempting to find the image in a compose file, check if `DOCKER_IMAGE` is still empty.
    - If empty, log error: "No Docker image specified and no docker-compose file found. Please use --docker-image <image_name>." and return 1.

### 2. Pipeline
- [ ] **Build**: Ensure script is still executable and syntax is correct.
- [ ] **Test**: 
    - Run with `--docker` without specifying an image and without a compose file $\rightarrow$ verify error message.
    - Run with `--docker-image <image>` $\rightarrow$ verify it works.
    - Run with a compose file $\rightarrow$ verify it finds the image.
- [ ] **Visual-Confirm**: Verify help output is updated.
- [ ] **Review**: Final check of the changes.
- [ ] **Security**: Ensure no secrets or dangerous patterns were introduced.
- [ ] **Docs**: Update any relevant documentation if necessary.

## Status
- [ ] In Progress
