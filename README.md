# Python fundamentals course

The internal python course held @Cegeka.

In this repository you will find:
* a presentation, available at [gitpitch](https://gitpitch.com/slbucur/python_course/master?n=true#/)
  * you can download it at the link, or see the text format inside the `PITCHME.md` file
* the jupyer notebooks in the `code` folder, as `.ipynb` files
* the python files in the `code` folder, as `.py` files

## Local installation
To run the assets locally, the recommended path through a virtual environment.
This is an isolated python environment where you can play around without affecting
the global python installation.

1.Find a python distribution suited for you

For `windows`:

* Go to [python.org](https://www.python.org/downloads/release/python-365/)
* Download the Windows executable [installer](https://www.python.org/ftp/python/3.6.5/python-3.6.5-amd64.exe)
* This will install `python` and `pip`

Also recommended, install `cmder`, a beter alternative to cmd.
This will also install git locally, so you can use it to easily clone this project.
* Install [cmder](http://cmder.net/) - full version (much better than cmd)
* Open cmder as Administrator

For `linux`:
* install python3.6 with your local package manager
```bash
apt-get install python3.6
```

2. Download the project locally

Using git (recommended):
* open a terminal window
  * on windows, go to the cmder installation on double click on `cmder.exe`
  * on linux `Ctrl+Alt+T` usually does the trick
* go to a directory where you want to make the project
  * windows: `cd C:\Users\<user_name>\Desktop`
  * linux: `cd /home/<user_name>/Desktop`
* clone the project
  * `git clone https://github.com/slbucur/python_course.git`

You can also use [Git for Desktop](https://desktop.github.com/)
 for downloading purpuses

Using zip:

* download using this [url](https://github.com/slbucur/python_course/archive/master.zip)
* unzip it where you want it

3. Instantiate a new virtualenv

* open a terminal window and cd to the folder you just created
  * on windows, it's easy with `Shift + Right Click` -> open cmd here
  * on linux, just Right Click should to the trick
* run these commands
  * `pipenv install` - installs a new virtualenv
  * `pipenv shell` - changes the shell (terminal) to that environment

4. Run a jupyterlab instance

* `jupyter lab`

### Good job 😉