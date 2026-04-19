# Automated CV Deployment Pipeline 🚀

This repository serves as the single source of truth for my professional resume. 

Instead of manually updating PDFs on my portfolio, I built a GitOps-driven CI/CD pipeline. Pushing a new `resume.pdf` to this repository triggers a serverless workflow that deploys the update globally.

## The Architecture
`Mac (Git Push)` ➔ `GitHub Actions` ➔ `OIDC (Keyless Auth)` ➔ `AWS S3` ➔ `AWS CloudFront`

## Key Engineering Highlights
* **Zero-Trust Security:** Uses OpenID Connect (OIDC) to authenticate GitHub Actions with AWS IAM via short-lived STS credentials. No hardcoded passwords or long-lived access keys.
* **Edge Delivery:** Utilizes Amazon CloudFront to invalidate caches and distribute the CV globally with ultra-low latency.
* **Decoupled Architecture:** Separates the CV data layer from the frontend portfolio application.