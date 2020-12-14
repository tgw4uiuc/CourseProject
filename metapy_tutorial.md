# metapy: (experimental) Python bindings for [MeTA][meta]

[![Build Status](https://travis-ci.org/meta-toolkit/metapy.svg?branch=master)](https://travis-ci.org/meta-toolkit/metapy)

[![Windows Build Status](https://ci.appveyor.com//api/projects/status/github/meta-toolkit/metapy?svg=true&branch=master)](https://ci.appveyor.com/project/skystrife/metapy)

```diff
-Author tgw4's note regarding attribution:  I created the OS
-specific sections of this, and the note regarding python 2.7 and
-3.4-3.7 being easier to use, the rest was created by the
-previous tutorial author(s).
```

This project provides Python (2.7 and 3.x are supported) bindings for the
MeTA toolkit. They are still very much under construction, but the goal is
to make it seamless to use MeTA's components within any Python application
(e.g., a Django or Flask web app).

This project is made possible by the excellent [pybind11][pybind11]
library.

- [OS Specific Instructions](#OS-specific-instructions)
    - [General Instructions](#General-setup-notes)
    - [Chromebook](#Chromebook)
    - [Ubuntu 20.04LTS](#Ubuntu-20.04-LTS)
    - [CentOS 8.2.2004](#Centos-8.2.2004)
    - [Windows 10](#Windows-10)



## Getting setup notes
(the easy way)

```bash
# Ensure your pip is up to date
pip install --upgrade pip

# install metapy!
pip install metapy
```

This should work on Linux, OS X, and Windows with pretty much any recent
Python version >= 2.7. On Linux, make sure to update your `pip` to version
8.1 so you can install from a binary package---this will save you a lot of
time.

## Compiling it yourself
(the hard way)

You will, of course, need Python installed. You will also need its headers
to be installed as well, so look for a `python-dev` or similar package for
your system. Beyond that, you'll of course need to satisfy the requirements
for [building MeTA itself][build-guide].

This repository should have everything you need to get started. You should
ensure that you've fetched all of the submodules first, though:

```bash
git submodule update --init --recursive
```

Once that's done, you should be able to build the library like so:

```bash
mkdir build
cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
make
```

You can force building against a specific version of Python if you happen
to have multiple versions installed by specifying
`-DMETAPY_PYTHON_VERSION=x.y` when invoking `cmake`.

The module should be written to `metapy.so` in the build directory.

###OS specific instructions

##Chromebook
Recently released Chromebooks (in the last couple of years as of December 2020) have a option to run a linux beta.  Metapy can be installed on these Chromebooks.  Check here for a list of compatible Chromebooks:  [https://www.chromium.org/chromium-os/chrome-os-systems-supporting-linux](https://www.chromium.org/chromium-os/chrome-os-systems-supporting-linux)

If your Chromebook is compatible, see this page to turn on the linux beta mode:

[Chomebook Linux Beta Mode](https://support.google.com/chromebook/answer/9145439)

Once you have Linux Beta installed and working, these are the steps to install metapy:

Open a linux terminal then:

'''
#update package lists
sudo apt-get update

#Install python3.7
sudo apt-get install python3.7

#install pip
sudo apt-get install python3-pip

#update pip
pip3 install --upgrade pip

#install metapy
pip3 install metapy

```
That's it, metapy is now installed.



### Ubuntu 20.04 LTS
'''
#update package lists
sudo apt update

#install pip
sudo apt install python3-pip

#update pip
pip3 install --upgrade pip

#make an install file directory
mkdir metapy
cd metapy
pip3 download metapy
ls (to see the filename it downloaded .. should be metapy(something).tar.gz

tar -xvf metapy-0.2.13.tar.gz (or whatever your filename is you downloaded above)

ls (to see the name of the directory it created)
cd (directory name from above, will be metapy-(something))

cd deps
mkdir icu-61.1

now download the "icu4c-61_1-src.tgz" file from https://github.com/unicode-org/icu/releases/tag/release-61-1
and copy it to the icu-61.1 directory you created above.

#move back up to the directory above the meta directory
cd ..
cd ..
cd ..

#when you 'ls' you should see "metapy" as one of the subdirectories


#install metapy 
pip3 install metapy (this will takeawhile as the metapy package is compiled).
```
Once its completed, that's it, metapy is now installed.



##CENTOS 8.2.2004

Centos is quite easy, as python 3.6 and pip are installed by 
default.

All you need to do is:

Make sure your user account is in the "sudoers" group, see this tutorial here:
[https://linuxize.com/post/how-to-add-user-to-sudoers-in-centos/](https://linuxize.com/post/how-to-add-user-to-sudoers-in-centos/)


Then to install metapy:
```
sudo pip3 install --upgrade pip
sudo pip3 install metapy
```

That's it, you now have metapy installed!


##Windows-10
First, be sure to have python version 2.7 or 3.4-3.7 installed.

To check if python is installed, open a command prompt window an type:

``
#check if proper version of python is installed
python --version
``

If it is not, download it from [python.org](python.org) (be sure to grab one of the versions mentioned above, not necessarily the latest version.)

Once python is installed, check if pip is installed:

```
#check for pip
pip --version
```

If pip is not installed, get it from [https://pypi.org/project/pip/](https://pypi.org/project/pip/).

Once pip is installed, upgrade it to the latest version, and install metapy:
```
#upgrade pip
pip install --upgrade pip

#install metapy
pip install metapy
```

That's it, you now have metapy installed!



[meta]: https://meta-toolkit.org
[pybind11]: https://github.com/pybind/pybind11
[build-guide]: https://meta-toolkit.org/setup-guide.html
