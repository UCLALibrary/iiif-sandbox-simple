# iiif-sandbox-simple
A simple sandbox for experimenting with different IIIF viewers.

## Acknowledgements
The code and basic implementation for this site was shamelessly borrowed from
[this IIIF Workshop](https://github.com/jronallo/iiif-workshop-new).

## How to update the viewer code
This is easiest to do if you have [Yarn](https://yarnpkg.com/en/) installed.

```
yarn add universalviewer
yarn add mirador
cp -r node_modules/mirador/dist mirador
cp -r node_modules/universalviewer/uv uv
```
There may be a better way to refresh the viewer code, but for now, that will
have to do.
