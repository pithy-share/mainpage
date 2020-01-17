# Mkdocs

[MKdocs official doc](https://www.mkdocs.org/)
## Setup

`pip install mkdocs`

## Serve

`mkdocs serve`

## Build

`mkdocs build`

## Apply
Two ways to use

* copy `site` director  to your web root director

* or deploy to github pages

```bash
cd your_github_repository_dir
mkdocs gh-deploy --config-file ../mainpage/mkdocs.yml --remote-branch master
```

## Use material theme

[Material theme official doc](https://squidfunk.github.io/mkdocs-material/)

* setup

```bash
pip install mkdocs-material
```

* apply

add material to mkdocs.yml

```bash
theme:
  name: material
```

## Emoji
edit `mkdocs.yml`
```
markdown_extensions:
  - pymdownx.emoji:
      emoji_index: !!python/name:pymdownx.emoji.twemoji
      emoji_generator: !!python/name:pymdownx.emoji.to_svg
```

[emoji index](https://github.com/facelessuser/pymdown-extensions/blob/master/pymdownx/twemoji_db.py)

```
:100:
:eyes:
:green_book:
```

:100:
:eyes:
:green_book: