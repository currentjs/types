# GitHub Actions Workflows

## Publish to NPM

This workflow builds, versions, and publishes the `@currentjs/types` package to the NPM registry.

### Triggers

- **Automatic**: On push to `main` or `master` branch (bumps patch version)
- **Manual**: Via GitHub UI with custom version bump type

### Required Secrets

Before using this workflow, you need to configure the following secret in your GitHub repository:

- `NPM_TOKEN`: NPM authentication token with publish permissions
  - Generate at: https://www.npmjs.com/settings/tokens
  - Make sure to select "Automation" token type
  - Grant "Publish" permission for the `@currentjs/types` package

### Usage

#### Automatic Publishing

Simply push to the main branch. The workflow will:
1. Build the package
2. Bump the patch version
3. Create a git commit and tag
4. Publish to NPM

#### Manual Publishing

1. Go to the "Actions" tab in your GitHub repository
2. Select "Publish to NPM" workflow
3. Click "Run workflow"
4. Choose version bump type:
   - `patch`: 1.0.0 → 1.0.1
   - `minor`: 1.0.0 → 1.1.0
   - `major`: 1.0.0 → 2.0.0
5. Optionally enable "Dry run" to test without actually publishing

### What the workflow does

1. **Build verification**: Compiles TypeScript and verifies all outputs exist
2. **Version management**: Updates package.json version based on chosen bump type
3. **Git integration**: Commits version changes and creates tags
4. **Publishing**: Publishes to NPM registry (unless dry run is enabled)

### Configuration

The workflow uses Node.js 18 and the build script defined in `package.json`. Make sure your package is properly configured before publishing.