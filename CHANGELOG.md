# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## Releases

### [0.1.1] - 2022-05-22

* Add import documentation

### [0.1.0] - 2022-05-21

* Initial release

## Add new version

```bash
# Checkout master branch
$ git checkout master && git pull

# Check current version
$ cat VERSION

# Add new version
$ echo "0.1.0" > VERSION

# Set version to bin/table-dumper
$ bin/table-dumper -u > bin/table-dumper.tmp && chmod 775 bin/table-dumper.tmp && mv bin/table-dumper.tmp bin/table-dumper

# Change changelog
$ vi CHANGELOG.md

# Push new version
$ git add CHANGELOG.md VERSION bin/table-dumper && git commit -m "Add version $(cat VERSION)" && git push

# Tag and push new version
$ git tag -a "$(cat VERSION)" -m "Version $(cat VERSION)" && git push origin "$(cat VERSION)"
```
