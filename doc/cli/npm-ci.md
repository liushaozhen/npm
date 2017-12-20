npm-ci(1) -- Install a project with a clean slate
===================================

## SYNOPSIS

    npm ci

## DESCRIPTION

This command is similar to `npm-install(1)`, except it's meant to be used in
automated environments such as automated testing, continuous integration, and
deployment. It can be significantly faster than a regular npm install by
skipping certain user-oriented features. It is also more strict than a regular
install, which can help catch errors or inconsistencies caused by the
incrementally-installed local environments of most npm users.

Concretely, the main differences between an `npm install` call and an `npm ci`
call are:

* The resulting `node_modules/` is not meant for interactive development.
* The project **must** have an existing `package-lock.json` or `npm-shrinkwrap.json`.
* If dependencies in the package lock do not match those in `package.json`, `npm ci` will exit with an error, instead of updating the package lock.
* `npm ci` can only install entire projects at a time: individual dependencies cannot be added with this command.
* If a `node_modules` is already present, it will be automatically removed before `npm ci` begins its install.
* It will never write to `package.json` or any of the package-locks: installs are essentially frozen.

## SEE ALSO

* npm-install(1)
* npm-package-locks(5)
