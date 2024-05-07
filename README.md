# DocGenSpec

Is a template/scaffold for creating [DocGen](https://github.com/DanielCardonaRojas/docgen) specifications. This allows sharing templates that generate particular types of documents, like invoices, CVs.

## Usage

This template provides an example of creating a simple invoice from a markdown file.

```sh
gomplate --config=configs/default.yaml
```

## Creating a Spec

All valid DocGenSpecs should be able to generate a document from example data. So users should be able to duplicate `./data/example.json`
and create a personalized document.

You can provide more than one template but at least one named `default.FILE_EXTENSION` should be defined. This can be an HTML, Markdown or any other file type supported by [gomplate](https://github.com/hairyhenderson/gomplate).

Note that [DocGen](https://github.com/DanielCardonaRojas/docgen) will only search for configs so for every template there should be a corresponding config, this might change in the future but is an easy way to manage templateswithout overcomplicating the [DocGen](https://github.com/DanielCardonaRojas/docgen) script to account for every combination of config and template.

More datasources may be defined in the configuration, see the [docs](https://docs.gomplate.ca/datasources) for possible datasources. Where possible define an example datasource and be ware of user privacy.


## Folder structure

```
├── configs
│   └── default.yaml (required)
├── data
│   └── example.json (required)
├── scripts
│   ├── doc_gen_cleanup.sh (optional)
│   └── doc_gen_file_name.sh (optional)
└── templates
    └── default.md (required)
```

## Requirements

List all the required binaries or libraries that your template requires.
