# heroku-buildpack-dpkg

Add support for dpkg-based packages during both compile and runtime.

## Usage

This buildpack works best with [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi) so that it can be used with your app's existing buildpacks.

Include a list of packages urls to be installed in a file named `Debfile`

> Note: If you want to install packages from the standard ubuntu lucid repository you better use [heroku-buildpack-apt](https://github.com/ddollar/heroku-buildpack-apt). This buildpack covers packages that may come from PPAs for example. But to resolve PPAs dependencies, you should still use [heroku-buildpack-apt](https://github.com/ddollar/heroku-buildpack-apt).

## Example

#### .buildpacks

    https://github.com/rricard/heroku-buildpack-dpkg
    https://github.com/heroku/heroku-buildpack-ruby

#### Debfile


    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/fontforge_0.0.20120828%2Bgit1-1ubuntu8_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/fontforge-dbg_0.0.20120828%2Bgit1-1ubuntu8_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/libfontforge-dev_0.0.20120828%2Bgit1-1ubuntu8_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/libfontforge1_0.0.20120828%2Bgit1-1ubuntu8_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/libgdraw4_0.0.20120828%2Bgit1-1ubuntu8_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/python-fontforge_0.0.20120828%2Bgit1-1ubuntu8_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/gir1.2-poppler-0.18_0.20.3-2ubuntu1pdf2htmlEX_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/libpoppler-cpp-dev_0.20.3-2ubuntu1pdf2htmlEX_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/libpoppler-cpp0_0.20.3-2ubuntu1pdf2htmlEX_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/libpoppler-dev_0.20.3-2ubuntu1pdf2htmlEX_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/libpoppler-glib-dev_0.20.3-2ubuntu1pdf2htmlEX_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/libpoppler-glib8_0.20.3-2ubuntu1pdf2htmlEX_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/libpoppler-private-dev_0.20.3-2ubuntu1pdf2htmlEX_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/libpoppler-qt4-4_0.20.3-2ubuntu1pdf2htmlEX_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/libpoppler-qt4-dev_0.20.3-2ubuntu1pdf2htmlEX_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/libpoppler27_0.20.3-2ubuntu1pdf2htmlEX_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/poppler-dbg_0.20.3-2ubuntu1pdf2htmlEX_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/poppler-utils_0.20.3-2ubuntu1pdf2htmlEX_amd64.deb
    https://launchpad.net/~coolwanglu/+archive/pdf2htmlex/+files/pdf2htmlex_0.6-1~git201210292011r7993a-0ubuntu1_amd64.deb


    
### Compile with [Anvil](https://github.com/ddollar/anvil-cli)

    $ heroku plugins:install https://github.com/ddollar/heroku-build
    
    $ heroku create dpkg-pdf2htmlex-test
    
    $ heroku build . -b ddollar/multi -r 
	Checking for app files to sync... done, 2 files needed
	Uploading: 100.0%
	Launching build process... done
	Preparing app for compilation... done
	Fetching buildpack... done
	Detecting buildpack... done, Multipack
	Fetching cache... done
	Compiling app...
	=====> Downloading Buildpack: https://github.com/ddollar/heroku-buildpack-apt
	=====> Detected Framework: Dpkg
	  ...
	=====> Downloading Buildpack: https://github.com/heroku/heroku-buildpack-ruby
	=====> Detected Framework: Ruby
	  Installing dependencies using Bundler version 1.3.2
	  ...
	Putting cache... done
	Creating slug... done
	Uploading slug... done
	Success, slug is https://api.anvilworks.org/slugs/00000000-0000-0000-0000-0000000000.tgz
	
## License

MIT
