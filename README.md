# AWS Portfolio Website

My personal portfolio at [ekeneeche.com](https://ekeneeche.com), hosted on AWS and deployed automatically from this repo.

## How it works

- **S3** stores the site in a private bucket
- **CloudFront** serves it over HTTPS using Origin Access Control, so the bucket is never public
- **ACM** provides the TLS certificate, **Cloudflare** handles DNS for the domain
- **GitHub Actions** syncs `site/` to S3 and clears the CloudFront cache on every push to `main`
- **OIDC** gives the workflow temporary AWS credentials, so no access keys are stored in GitHub

While setting up OIDC I hit an `AssumeRoleWithWebIdentity` failure, traced it in CloudTrail, and fixed the IAM role trust policy.

## Layout

```
site/                         HTML, CSS and project pages
.github/workflows/            Deploy workflow
```

**Technologies:** AWS, S3, CloudFront, ACM, IAM, Cloudflare, HTML, CSS, GitHub Actions

**Status:** Live
