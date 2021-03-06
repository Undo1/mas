# mas-cli

A simple command line interface for the Mac App Store. Designed for scripting 
and automation.

## Install

[Homebrew](https://brew.sh) is the preferred way to install:

    brew install mas

Alternatively, binaries are available in the [GitHub Releases](https://github.com/argon/mas/releases)

## Usage

Each application in the Mac App Store has a product identifier which is also
used for mas-cli commands. Using `mas list` will show all installed
applications and their product identifiers.

    $ mas list
    446107677 Screens
    407963104 Pixelmator
    497799835 Xcode

It is possible to search for applications by name using `mas search` which
will search the Mac App Store and return matching identifiers

    $ mas search Xcode
    497799835 Xcode
    688199928 Docs for Xcode
    449589707 Dash 3 - API Docs & Snippets. Integrates with Xcode, Alfred, TextWrangler and many more.
    [...]

To install or update an application simply run `mas install` with an
application identifier:

    $ mas install 808809998
    ==> Downloading PaintCode 2
    ==> Installed PaintCode 2

Use `mas outdated` to list all applications with pending updates.

    $ mas outdated
    497799835 Xcode (7.0)
    446107677 Screens VNC - Access Your Computer From Anywhere (3.6.7)

To install all pending updates run `mas upgrade`.

    $ mas upgrade
    Upgrading 2 outdated applications:
    Xcode (7.0), Screens VNC - Access Your Computer From Anywhere (3.6.7)
    ==> Downloading Xcode
    ==> Installed Xcode    
    ==> Downloading iFlicks
    ==> Installed iFlicks    

To sign into the Mac App Store for the first time run `mas signin`.

    $ mas signin mas@example.com
    ==> Signing in to Apple ID: mas@example.com
    Password: 


You can also embed your password in the command.

    $ mas signin mas@example.com "ZdkM4f$gzF;gX3ABXNLf8KcCt.x.np"
    ==> Signing in to Apple ID: mas@example.com

Use `mas signout` to sign out from the Mac App Store.

## Build from source

`mas` currently requires the [bundler](http://bundler.io/) RubyGem in order to 
bootstrap and build the project. There are a number ways to install bundler but
if you have never used it before then installing it with `gem` should be enough.

```
$ gem install bundler
```

You can now bootstrap the project by executing the `bootstrap` script
from the mas sources script directory:

```
$ script/bootstrap
```

You can now build from Xcode by opening `mas-cli.xcodeproj`, or from the Terminal:

```
$ script/build
```

Build output can be found in the `build/` directory within the project.

## License

Code is under the [MIT license](LICENSE).
