# create-gh-release

Usage:

```yaml
on:
  push:
    tags:
      - 'v*' # Push events to matching v*, i.e. v1.0, v20.15.10

name: Create Release

permissions: {}
jobs:
  build:
    permissions:
      contents: write # to create release (khanhduy1407/create-gh-release)

    name: Create Release
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@master
      - name: Create GitHub Release for Tag
        id: release_tag
        uses: khanhduy1407/create-gh-release@master
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          tag_name: ${{ github.ref }}
          body: |
            This is the body content GitHub Release
```
