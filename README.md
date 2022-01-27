# Cookie cutter lab notebook using Jupyter-Book

This project directory format 

## Documentation for Jupyter-book

Find instructions here: https://jupyterbook.org/

My suggestions on setting up a labnotebook are here: https://github.com/executablebooks/jupyter-book/issues/732

## Building the Table of Contents

You must do this after adding a new page or re-arranging the file structure of your notebook.

Run the following code from the root directory of your project.

```
jb toc from-project labnotebook -e .md -e .ipynb > labnotebook/_toc.yml
```

The option `-e [FILETYPE]` tells jupyter-book which file types found in your project to include in the built book.

## Building your notebook

To get a nicely formatted HTML notebook, run the following command from the root directory of your project AFTER your `_toc.yml` is updated:

```
jb build labnotebook
```

That should spit out a link to an HTML page to your console, which you can copy/paste into your browser to view your notebook.

## Extra Tips

- You MUST have a `.md` file in each subdirectory of `labnotebook` and every content file (`.md` or `.ipynb`) MUST have a heading starting with a `#` character at the beginning of the document.
- If you jump header levels (i.e. starting with `#` and then the next heading is `###`), the build will complain.
- If you remove a file from your book and remove it from the TOC, but the HTML for the file has already been built, re-building the book will not automatically clear it. The simplest fix is to delete the `_build` folder in `labnotebook` and re-build.


## Recommended folder structure
```
myproject
└── data
└── scripts
└── figures
└── images
└── labnotebook
     └── experiments
         └── experiments.md
         └── experiment_type1
             └── YYYYMMDD_description.md <-- relative path uses files in 'data'
         └── experiment_type2
             └── YYYYMMDD_description.md
     └── index.md
     └── _config.yml
     └── _toc.yml
     └── logo.png
└──  other_directories (folders of PDFs, presentations, etc)
```
