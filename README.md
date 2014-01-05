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


    


    
### Compile with [Anvil](https://github.com/ddollar/anvil-cli)

    $ heroku plugins:install https://github.com/ddollar/heroku-build
    
    $ heroku create apt-pg-test
    
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
