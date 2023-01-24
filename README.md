# templates
A kn func repository for WASMEdge templates

Currently the [buildpack](https://github.com/knawd/buildpack) required to run this repo in `kn func` has some known issues.

See https://github.com/knative/func/discussions/1489#discussioncomment-4761544

If you are looking for something more complete then please consider the https://github.com/knawd/gen-templates project.

## usage

```
kn func create myfunc -l rust -t http --repository https://github.com/knawd/templates
```
