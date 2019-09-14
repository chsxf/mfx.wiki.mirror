## Fetching Framework Source Code

### Composer Support

At this time, MFX does not support Composer.\
It is a planned improvement and work has already began to port dependencies and the core module.

### Recommended method - Framework as Submodule

It is recommended to add the framework's repository as a submodule of an existing project. This way you can seperate your application code from the the framework's code and let it untouched and ready for future upgrades.

#### Instructions

We recommend adding the submodule under the name `mfx` and the documentation has been written with this in mind. However, the folder name and location can be changed as you see fit.

* Go to your project's repository folder
* Run the following command line to add the framework as a submodule:
  * through HTTPS:\
  	`git submodule add https://github.com/cheeseburgames/php-micro-framework.git mfx`
  * through SSH:\
  	`git submodule add git@github.com:cheeseburgames/php-micro-framework.git mfx`
* Update the submodules recursively: `git submodule update --init --recursive`

### Alternative Method - Cloning the Repository

You can clone the repository's master branch through HTTPS:

```
git clone https://github.com/cheeseburgames/php-micro-framework.git
```

or through SSH:

```
git clone git@github.com:cheeseburgames/php-micro-framework.git
```

##### Updating Submodules

MFX relies on several submodules you'll need to update and initialize to be able to run the framework.

Go to the MFX repository's folder and run this command-line:

```
git submodule update --init --recursive
```

### Alternative Method - Source Code Archive

Additionally, you can download the repository as a .zip file from github. However, we do not recommend this method as you won't get any submodule source code through the download.