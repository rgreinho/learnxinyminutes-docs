---
category: tool
tool: cookiecutter
filename: cookiecutter.txt
contributors:
    - ["Rémy Greinhofer", "https://github.com/rgreinho"]
lang: en-us
---

A command-line utility that creates projects from cookiecutters (project
templates), e.g. creating a Python package project from a Python package project
template.

It can also be used as a Python library.

## CLI Usage

```bash
# Create a project from a local template.
cookiecutter cookiecutter-pypackage
cookiecutter cookiecutter-pypackage.zip

# Create a project from a URL.
cookiecutter https://example.com/path/to/cookiecutter-pypackage.zip

# Create a project from a repository.
cookiecutter https://github.com/audreyr/cookiecutter-pypackage
cookiecutter https://github.com/audreyr/cookiecutter-pypackage.git
cookiecutter git+ssh://git@github.com/audreyr/cookiecutter-pypackage.git
cookiecutter hg+ssh://hg@bitbucket.org/audreyr/cookiecutter-pypackage

# Create a project using the shorthand syntax.
cookiecutter gh:audreyr/cookiecutter-pypackage # GitHub
cookiecutter bb:audreyr/cookiecutter-pypackage # Bitbucket
cookiecutter gl:audreyr/cookiecutter-pypackage # GitLab

# Create a project from a specific tag, branch or commit.
cookiecutter gh:audreyr/cookiecutter-pypackage --checkout 1.0.0
```

## Create a cookiecutter

```bash
# Create the cookiecutter template.
mkdir -p /tmp/HelloCookieCutter1

# Create a folder for the generated project.
cd /tmp/HelloCookieCutter1
mkdir {{cookiecutter.directory_name}}

# Create a template file.
cd "{{cookiecutter.directory_name}}"
echo 'print("Hello, {{cookiecutter.greeting_recipient}}!")' \
  >{{cookiecutter.file_name}}.py

# Create the variable file.
# This file is used to render the values between double curly brackets.
cd ..
cat <<EOF >cookiecutter.json
  {
    "directory_name": "Hello",
    "file_name": "Howdy",
    "greeting_recipient": "Julie"
  }
EOF

# Generate the project.
cookiecutter /tmp/HelloCookieCutter1 --no-input -o /tmp/MyOwnHelloCookieCutter
```

## References

* [Official documentation](https://cookiecutter.readthedocs.io/en/latest/index.html)
