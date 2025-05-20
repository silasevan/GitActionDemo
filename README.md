# GitActionDemo
A project to demonstrate CI/CD using Git action

This project demonstrates a Node.js setup with Continuous Integration (CI) using **GitHub Actions**. It includes:

- Matrix testing across different Node.js environments.
- Dependency caching to optimize workflow speed.
- Code quality enforcement with **ESLint**.

## 📁 CI Workflow

The CI workflow is defined in the [`.github/workflows/ci.yml`](.github/workflows/ci.yml) file.

### CI Features:

- ✅ **Matrix Testing:** Runs tests across multiple versions of Node.js (e.g., 14.x, 16.x, 18.x).
- 🚀 **Caching Dependencies:** Uses GitHub Actions caching to store and restore `node_modules` for faster runs.
- 🧪 **Linting with ESLint:** Enforces code quality using ESLint.

---

## 🧪 Running Locally

Clone the repo and install dependencies:

```bash
git clone <your-repo-url>
cd <your-project>
npm install
```

### Lint Your Code

```bash
npm run lint
```

### Run Tests

```bash
npm test
```

---

## ✅ GitHub Actions CI Config

Below is an example of the `.github/workflows/ci.yml` file you should include:

```yaml
name: Node.js CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [14.x, 16.x, 18.x]

    steps:
      - uses: actions/checkout@v3

      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v3
        with:
          node-version: ${{ matrix.node-version }}
          cache: 'npm'

      - run: npm install
      - run: npm run lint
      - run: npm test
```

---

## 📦 Scripts

Ensure your `package.json` includes the following scripts:

```json
"scripts": {
  "lint": "eslint .",
  "test": "jest"
}
```

---

## 📦 ESLint Setup

Install ESLint and initialize it if not already done:

```bash
npm install eslint --save-dev
npx eslint --init
```

---


