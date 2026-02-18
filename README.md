# Documentation for Origo

[Documentation](https://origo-map.github.io/origo-documentation/latest/) for the [Origo](https://github.com/origo-map/origo) web map framework.

## Writing documentation

Documentation is written as Markdown files in the `docs` directory. The structure of the documentation site is configured in the `mkdocs.yml` file.

## Development

Requirements:
* Python 3.x
* Pip

To run the site locally:

1. Clone this repository:
   ```bash
   git clone https://github.com/origo-map/origo-documentation.git
   ```

2. Create and activate a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   # Windows
   .\venv\Scripts\activate
   # Linux/macOS
   source venv/bin/activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Start the development server:
   ```bash
   mkdocs serve
   ```

5. Open [http://127.0.0.1:8000/](http://127.0.0.1:8000/)

## Deployment

To build the static site (generated in the `site/` directory):
```bash
mkdocs build
```

To deploy to GitHub Pages:
```bash
mkdocs gh-deploy
```

After deployment, go to the repository settings on GitHub, navigate to the "Pages" section, and ensure that the source is set to the `gh-pages` branch and the folder is set to `/ (root)`.

## Notes

The Origo documentation is built using [MkDocs](https://www.mkdocs.org/) and the [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) theme.
