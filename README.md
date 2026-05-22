# Migasfree Golden Image (MGI) Project Templates

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

This repository serves as the official registry for **Migasfree Golden Image (MGI)** project templates. These templates allow administrators to bootstrap fully-configured operating system platforms (such as Debian, Ubuntu, etc.) with pre-defined deployments, stores, and applications.

---

## 📂 Repository Structure

The repository is modular and structured as a catalog. The top-level `catalog.yml` acts as the index, while each directory corresponds to a specific template:

```text
project-templates/
├── LICENSE                 # GNU GPL v3 License
├── README.md               # This documentation file
├── catalog.yml             # Global templates registry
└── [template_id]/          # Specific template directory (e.g. fwm)
    ├── deployments.yml     # Deployments, package sets, and properties configuration
    ├── applications.yml    # Applications associated with the project
    ├── dockerfile.j2       # Jinja2 template for the Golden Image Dockerfile
    ├── partition.yml       # Disk partitioning configuration
    ├── packages.yml        # Package meta-information
    ├── stores.yml          # Package sources/stores registration
    ├── stores/             # Additional store assets
    └── icons/              # Media and desktop application icons
```

### Key Files Explained:

*   **`catalog.yml`**: The main index file fetched by the Migasfree manager. It maps template identifiers (`id`) to their respective base operating systems (`base_os`).
*   **`deployments.yml`**: Defines target client groups, dependencies, custom properties, and package states.
*   **`dockerfile.j2`**: The template file used to construct the custom base image layer. It can contain environment variables, custom package installations, and repository configurations.
*   **`partition.yml`**: Declares target disk architectures, volume groups, and mounting points.

---

## 🛠️ Catalog Registry (`catalog.yml`)

The root `catalog.yml` must list all active templates with the following format:

```yaml
templates:
  - id: fwm
    base_os: debian:13.4
```

---

## 🚀 How to Request or Add a New Template

To ensure the highest security, performance, and stability standards across all managed fleets, the official catalog is **strictly curated and maintained directly by the Migasfree Core Team**.

### 🏠 For Local/Private Templates (Zero Friction)
If you want to use a custom, private, or experimental template for your own server, **you do not need to submit any request to GitHub**.
Simply design and test your project in the Migasfree administration interface, then export it. The system automatically places the generated template folder directly in your server's local storage pool:
```text
/pool/project-templates/[template_id]/
```
This registers the template under the `local` origin, making it instantly visible, editable, and usable on your server with zero friction.

### 🌐 Requesting an Official Template (GitHub Issues)
If you have created a stable, generic template (e.g. bootstrapping support for a new operating system release) and want it to be included in the official global catalog:

1.  **Open an Issue**: Open a new **Issue** in this repository.
2.  **Provide the Configuration**: Share the configuration files (`deployments.yml`, `dockerfile.j2`, `partition.yml`) as text block snippets or attach a compressed file containing the template directory.
3.  **Strict Security Audit**: The Migasfree Core Team will thoroughly audit the code to ensure it meets our safety and performance guidelines.
4.  **Official Release**: Once verified, the team will package and publish the template to the official repository.

---

## 🛡️ Security & Vetted Assets Policy

To prevent any distribution of malicious payloads while providing a satisfying and educational out-of-the-box experience:

*   **Essential Core Packages**: To help users bootstrap their projects from scratch, our official templates include pre-configured support for essential Migasfree core software (`migasfree-client`, `migasfree-agent`, and `migasfree-play`).
*   **"Fun with Migasfree" Learning Assets**: We include a highly curated set of official application icons (`.png` files) specifically designed to support the practical examples and tutorials in the companion book *"Fun with Migasfree"*, enhancing the onboarding and learning journey.
*   **Strict Team Custody**: For absolute security, **no external, untrusted binary packages or image files are ever accepted**. All binary definitions and graphic assets are strictly managed, verified, and pushed exclusively by the **Migasfree Core Team** to guarantee a fully secure chain of trust.

---

## 📄 License


This project is licensed under the **GNU General Public License v3 (GPL-3.0)** - see the [LICENSE](LICENSE) file for details.
