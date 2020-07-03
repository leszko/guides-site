# How To Publish A Guide On [GitHub Pages](https://hazelcast-guides.github.io/guides-site/guides-home/v0.1/index.html)

- In the guide repository to be published, create `antora` files:

```
antora
├── antora.yml
└── modules
    └── ROOT
        └── pages
            └── index.adoc
```
This files can be in a separate branch or located in a different root directory. In this case, they need to be specified in `antora-playbook.yml`.

- In `home/modules/ROOT/pages/index.adoc`, include the new guide:

```
[.guide]
=== xref:<new-guide>:ROOT:index.adoc[New Guide Header]

This is a brand new guide explanation.

``` 
`<new-guide>` tag here is the one that you specify in the `antora.yml` at the first step.

- In `antora-playbook.yml`, include the new guide's repository:

```
- url: https://github.com/hazelcast-guides/new-guide-repository
  branches: antora-doc-branch
  start_path: antora-root-dir
```

- Create new docs:

```
$ antora antora-playbook.yml
```

- Move the created content into docs:

```
$ rm -rf docs/*
$ mv build/site/* docs
$ rm -r build
```
- Check if your guide is added successfully:

```
$ open docs/index.html
```

Push if everything looks good and it will be published on GitHub pages in a while.
