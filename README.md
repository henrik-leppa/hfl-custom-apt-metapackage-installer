HFL Custom APT Metapackage Installer 1.0.0
==========================================

[ Encoding: UTF-8; Syntax: GitHub Flavored Markdown ]:#

Template for writing scripts that create and install custom metapackages,
written by Henrik Franciscus Leppä (HFL).


[Changelog][]
-------------


Background
----------

APT is a great package manager, but it lacks a few things:

- It does not keep track of which packages have been installed by the user, and
  why.

  - In particular, there are times when you need to install packages for the
    sake of other packages, without the packages being coded as dependencies.

  - Being able to record why a package was installed makes it easier to keep the
    number of packages in check, and thus make the package list more manageable.

- While there are tools to backup and restore your packages, these tools are
  only meant to for the entire setup, without a possibility to compartmentalize.

  - In particular, there are times when you want to install certain packages on
    all your computers, but others on only some.

  - Additionally this script allows the packages of multiple computers to be
    kept in sync with fairly little hassle.

This script template is meant to address these shortcomings and more.


Purpose
-------

When executed, the script based on this template:
1. Ensures that PPAs listed on the script (if any) are set up.
2. Creates temporary a metapackage that has the packages on the script as
   dependencies.
3. Installs the temporary metapackage, along with its dependencies.


Prerequisites
-------------

- POSIX-compliant shell (`/bin/sh`)
- Root privileges
- `apt-get` command
- `add-apt-repository` command
- `equivs-build` command
- `gdebi` command

**Note:** The script will check for the required commands itself, and install
the last three if needed, so you do not have to.


Usage
-----

1. Make a copy of [template][] and name it in the form:
   ```
   install-__METAPACKAGE_NAME__-metapackage
   ```
2. Open the copy using a plain text editor.
3. Replace every word that starts and ends with two underscores (`__`) with
   something appropriate.
   - If you are unsure what to do, take example from the [example scripts].
4. Save the copy.
5. Execute the copy in terminal, supplying it a root password.
6. Once the metapackage has been installed, you can review it with a command in
   the form:
   ```sh
   apt-cache show __METAPACKAGE_NAME__
   ```
   ...or using a software manager application.

**Note:** List of PPAs is not necessary for the script, see
[`install-hfl-boinc-metapackage`][] for an example of a script that does not
include PPA handling.


[Examples]
----------


Licensing
---------

This software and associated documentation files are licensed under the [MIT
License][].

You are also allowed to make modified copies of [template] use them as you wish
as long as it contains the lines:
```
Based on: [HFL Custom APT Metapackage Installer 1.0.0 by Henrik Franciscus
Leppä](https://github.com/henrik-leppa/hfl-custom-apt-metapackage-installer)
```


Testing
-------

Automated tests are done using [shUnit2][] and [ShellCheck][].

### Steps

1. Install ShellCheck 0.7.0.
2. Run:
   ```sh
   ./test
   ```


[Changelog]: ./CHANGELOG.md
[Examples]: ./examples/
[example scripts]: ./examples/
[`install-hfl-boinc-metapackage`]: ./examples/install-hfl-boinc-metapackage
[MIT License]: ./LICENSE.md
[ShellCheck]: https://github.com/koalaman/shellcheck
[shUnit2]: https://github.com/kward/shunit2
[template]: ./template
