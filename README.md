# github-latest
A quick little utility to *download the latest release* of a given project from GitHub.

This is a *very specific* tool for my own needs, but is open-source in case it is of use to others, either directly or as example code.

The next version will support unzipping the downloaded file (if you chose zip).

**Note:** It does not use project versions or tags, it uses the publish date and will download the latest.

### Download
Binary executables can be downloaded for Windows, Linux and MacOS X. These are available as assets on [the Release page](https://github.com/appurist/github-latest/releases/latest).

### To Build

**Prerequisites:** You must have Node.js installed to build this, as well as `yarn` (or you can run `"npm install"` and substitute `"npm run"` everywhere else you see `"yarn"`).

To **build** this tool with yarn:
```
yarn install
yarn build
```
This will produce an executable named `latest` (or `latest.exe` on Windows).

### Usage
```
Usage: latest [-avxXh?] owner project [tar|zip|unzip [ outfile]]
 e.g.: latest appurist github-latest unzip release.zip
   or: latest -X appurist github-latest
Options are:
    -a all: display all release versions/tags
    -x expand: (unzip) the zip file after download
    -X expand verbose: unzip and show files
    -v version: show version info
    -h or -? help: show this usage syntax
```
The default is to download the zip file, and the output filename (`outfile`) is either `latest.zip` or `latest.tar.gz`, depending on the format requested.

Choosing `unzip` is the same as `zip` (it downloads the .zip from GitHub), however it automatically expands the zip file into a new `"latest-unzipped"` folder.  Alternatively, specifying a `-x` option before the other arguments also implies a zip format and expands the files. Specifying `-X` (capitalized) expands the zip in a verbose manner, naming every file expanded.

Note that when unzipping, it replaces the top-level GitHub *numbered* folder name (e.g. `"appurist-github-latest-acdd162"`) with a fixed `"latest-unzipped"` folder name for easy scripting and automation. When expanding the zip file, it does *not* remove the downloaded zip file.

For example, to download the zip for the latest release of this project:
```
latest appurist github-latest
```
This will download the latest release as `latest.zip`. To automatically extract the contents of the zip file:
```
latest appurist github-latest unzip
```
This will download the latest release as `latest.zip`, and extract its contents into a `"latest-unzipped"` folder.

To download the tarball for the latest release of this project:
```
latest appurist github-latest tar
```
This will download the latest release as `latest.tar.gz`.

It is also possible to specify the download file (or path):
```
latest appurist github-latest zip outfile.zip
```
This will download the latest zip release as `outfile.zip`.
