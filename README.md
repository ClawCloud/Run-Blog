# Contribute to ClawCloud Run Blog ✍️

This repository serves as the submission platform for the **ClawCloud Run Blog**, accepting technical articles, tutorials, case studies, and other content related to **cloud computing, development tools, and DevOps**. Submissions are made via GitHub Pull Requests and are automatically deployed after approval.

------

### Blog：

#### https://blog.run.claw.cloud

## **Submission Process**

### 1. Prepare Your Article

- **Format**: Articles must be written in **Markdown** with **Front Matter** metadata (see template below).
- **Assets**: Place images/attachments in an `assets/` subdirectory. Use relative paths (e.g., `![Figure1](./assets/image1.png)`).

### 2. Submit via Pull Request

1. **Fork this repository**.
2. Create a folder under `posts/` with the naming convention:   `YYYY-MM-DD-your-post-title` (e.g., `2025-03-05-cloud-run-tutorial`).
3. Inside the folder:
   - Create an `Readme.md` file using this template:

```
---
title: "Your Article Title"
author: "Your Name or Alias"
author website: "Your Website or Github Profile"
date: YYYY-MM-DD
tags: [tag1, tag2]  # e.g., [Cloud Computing, Tutorial]
---

<!-- Begin your content -->
## Introduction  
Your article starts here...
```

- Add an `assets/` directory for images (optional).
- Submit a **Pull Request** to the `main` branch.

**Example Structure**:

```
├── posts/                 # Draft submissions (via PR)
│   └── 2025-03-05-sample-post/
│       ├── Readme.md        # Article content (Markdown + Front Matter)
│       └── assets/         # Associated resources
│           └── diagram.png
```

### 3. Review & Publication

- **Review**: Maintainers will verify technical relevance, formatting, and originality.
- **Approval**: Posts that accept the merge will be published to the Blog platform.
- **Revisions**: Feedback will be provided for adjustments if needed.

------

## **Guidelines**

- **Original Content**: Plagiarism is prohibited. Translations require explicit attribution.
- **Clear Formatting**:
  - Use proper Markdown syntax.
  - Add language labels to code blocks (e.g., ```python).
- **Technical Focus**: Topics must align with cloud technologies, DevOps, or software development.

------

## **License**

By submitting, you agree to publish your work under the [**CC BY-SA 4.0 License**](https://creativecommons.org/licenses/by-sa/4.0/).

------

## **Questions?**

Reach out via:

- Comments on your Pull Request
- [GitHub Issues](https://github.com/ClawCloud/Run-Blog/issues)
- Email: `support@run.claw.cloud`

------

**Happy writing!** 🚀 Share your expertise with the global developer community.

https://blog.run.claw.cloud