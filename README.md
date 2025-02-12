# CommonDocsAssets

**CommonDocsAssets** is a centralized repository containing shared assets for
maintaining consistent design and functionality across the documentation
repositories of various projects within the EasyScience organization.

## Contents

This repository includes:

- **Stylesheets**: Shared CSS files for consistent and unified styling of
  documentation pages.
- **JavaScript**: Scripts for adding interactivity and dynamic features to
  documentation.
- **Icons**: A collection of commonly used icons to ensure visual consistency
  across projects.
- **HTML Templates**: Reusable templates to streamline the setup and
  standardization of documentation.

## Building Documentation with MkDocs

Follow these steps to build and deploy documentation for projects within the
EasyScience organization using MkDocs:

### 1. Set Up the Documentation Repository

- Ensure the repository includes a `.github/workflows/build-docs.yml` file for
  GitHub Actions.
- Refer to this
  [GitHub workflow example](https://github.com/EasyScience/EasyDiffractionLibDocs/blob/master/.github/workflows/build-docs.yml)
  from the EasyDiffractionLibDocs project.

### 2. Set Up Python and MkDocs (static site generator)

- **Create a virtual environment (optional)**:
  ```bash
  python -m venv .venv
  source .venv/bin/activate
  ```
- **Upgrade pip (optional)**:
  ```bash
  pip install --upgrade pip
  ```
- **Install MkDocs and plugins**: Install the
  [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/getting-started/)
  framework and additional plugins such as the
  [Jupyter plugin for MkDocs](https://github.com/danielfrg/mkdocs-jupyter):
  ```bash
  pip install mkdocs mkdocs-material mkdocs-jupyter mkdocs-plugin-inline-svg
  ```

### 3. Copy Common Docs Assets

- Include the necessary files from the `CommonDocsAssets` repository into your
  documentation repository. Add the following step in your GitHub Actions
  workflow to automate this:
  ```bash
  git clone https://github.com/EasyScience/CommonDocsAssets.git
  cp CommonDocsAssets/docs/assets/javascripts/extra.js docs/assets/javascripts/
  cp CommonDocsAssets/docs/assets/stylesheets/extra.css docs/assets/stylesheets/
  cp CommonDocsAssets/overrides/main.html overrides/
  cp CommonDocsAssets/overrides/partials/logo.html overrides/partials/
  cp CommonDocsAssets/overrides/.icons/google-colab.svg overrides/.icons/
  ```

### 4. Copy Branding Assets

- Add branding resources from the `BrandingResources` repository into your
  documentation repository. Automate this step with the following commands:
  ```bash
  git clone https://github.com/EasyScience/BrandingResources.git
  cp BrandingResources/EasyDiffraction/logos/edl-logo_dark.svg docs/assets/images/easydiffractionlib_dark.svg
  cp BrandingResources/EasyDiffraction/logos/edl-logo_light.svg docs/assets/images/easydiffractionlib_light.svg
  cp BrandingResources/EasyDiffraction/icons/ed-icon_256x256.png docs/assets/images/favicon.png
  cp BrandingResources/EasyDiffraction/icons/ed-icon_bw.svg overrides/.icons/easydiffraction.svg
  cp BrandingResources/EasyScienceOrg/icons/eso-icon_bw.svg overrides/.icons/easyscience.svg
  ```

### 5. Build the Static Website

- Use the following command to generate the static site from the content in the
  `docs/` directory. The output will be placed in the `site/` directory:
  ```bash
  mkdocs build
  ```

### 6. Deploy the Documentation

- The deployment process is typically handled by the GitHub Actions workflow.
  The static site is deployed to a hosting service such as GitHub Pages.
