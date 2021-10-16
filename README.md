# RSE-ops Readthedocs

This is a documentation template that can be deployed to read-the-docs, or
if built and pushed manually, to GitHub pages. [Readthedocs](readthedocs.org/) is nice because
it will maintain a record of previous versions. The template is provided in
the [docs](docs) folder as very likely you will maintain the documentation alongside
your code (recommended).

🚧️ **under developemnt** 🚧️

## Features

 - Markdown or Restructured syntax
 - Python gallery with examples (if you have a Python project)


## Install

To install dependencies:

```bash
$ cd docs
$ python -m venv env
$ source env/bin/activate
$ pip install -r requirements.txt
```

At this point, you'll want to edit [conf.py](docs/conf.py) to add the correct GitHub links
and metadata for your project. If you have a Python project and include docstrings, you might even want to
add it to the requirements.txt and import it there. We also support both markdown
and restructured syntax (rst) depending on the file extension. To see tricks for
using markdown, see [this guide](https://myst-parser.readthedocs.io/en/latest/syntax/optional.html).
If you have existing rst docs to convert to markdown, see [this tool](https://github.com/executablebooks/rst-to-myst).

To build the documentation run:

```bash
$ make html
```

To clean up old generated files and start again:

```bash
make clean
```

And then to preview the built docs:

```
cd _build/html
python -m http.server 9999
```

Then open your browser to [http://127.0.0.1:9999](http://127.0.0.1:9999)

## Deploying

The easiest thing to do is have an automated build deployed to readthedocs.
You can login there, connect the repository, and then configure the build.

**TODO** If you'd like to deploy during CI, recipes are included here for both CircleCI
and GitHub Actions.

License
-------

Copyright (c) 2017-2021, Lawrence Livermore National Security, LLC. 
Produced at the Lawrence Livermore National Laboratory.

The RADIUSS documentation is licensed under the MIT license [LICENSE](./LICENSE).

Copyrights and patents in the RADIUSS project are retained by
contributors. No copyright assignment is required to contribute to RADIUSS
Docker.

This work was produced under the auspices of the U.S. Department of
Energy by Lawrence Livermore National Laboratory under Contract
DE-AC52-07NA27344.
