# Demonstrates the build issue with reuse libraries

```
# Clean any previous test and clone the repo
rm -rf cds-reuse-build-issue
git clone https://github.com/carlonnheim/cds-reuse-build-issue.git

# This fails
(
    cd cds-reuse-build-issue
    for m in module-a utilities module-b ; do npm --prefix $m i; done
)
```
```
# Clean any previous test and clone the repo
rm -rf cds-reuse-build-issue
git clone https://github.com/carlonnheim/cds-reuse-build-issue.git

# This makes it work
rm cds-reuse-build-issue/module-b/package-lock.json

(
    cd cds-reuse-build-issue
    for m in module-a utilities module-b ; do npm --prefix $m i; done

    # ... but the package-lock.json file coming out after is identical
    git status
)
```
