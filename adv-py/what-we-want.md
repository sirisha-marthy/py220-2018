For Lesson 5- Ken Murray, I was not able to get the pdb debugger to function. please give us a demo.
I kept getting a syntax error when I tried to follow the video. - Ken Murray

Could use help with having multiple formatters for different handlers. Thought I did it right but can't seem to get it working. 
  https://docs.python.org/3/howto/logging-cookbook.html


Lesson 4 - packaging notes: https://uwpce-pythoncert.github.io/PythonCertDevel/modules/Packaging.html


Missing context for the meta-mailroom exercise.  

Here is some of it.  For starters, I like to use virtualenvs for _everything, always.

```
brew@ontario:~$ which python3
/usr/local/bin/python3
brew@ontario:~$ python3 -V
Python 3.6.5
brew@ontario:~$ mkvirtualenv -p python3 mailroom
Running virtualenv with interpreter /usr/local/bin/python3
Using base prefix '/usr/local/Cellar/python/3.6.5/Frameworks/Python.framework/Versions/3.6'
New python executable in /Users/brew/.virtualenvs/mailroom/bin/python3.6
Also creating executable in /Users/brew/.virtualenvs/mailroom/bin/python
Installing setuptools, pip, wheel...done.
virtualenvwrapper.user_scripts creating /Users/brew/.virtualenvs/mailroom/bin/predeactivate
virtualenvwrapper.user_scripts creating /Users/brew/.virtualenvs/mailroom/bin/postdeactivate
virtualenvwrapper.user_scripts creating /Users/brew/.virtualenvs/mailroom/bin/preactivate
virtualenvwrapper.user_scripts creating /Users/brew/.virtualenvs/mailroom/bin/postactivate
virtualenvwrapper.user_scripts creating /Users/brew/.virtualenvs/mailroom/bin/get_env_details
```
The json_save.zip in the exercise description contains a module. You install it with
```
python setup.py install
```
from within the json_save directory. 

```
(mailroom) brew@ontario:/tmp/json_save$ python setup.py install
running install
running bdist_egg
running egg_info
creating json_save.egg-info
writing json_save.egg-info/PKG-INFO
writing dependency_links to json_save.egg-info/dependency_links.txt
writing top-level names to json_save.egg-info/top_level.txt
writing manifest file 'json_save.egg-info/SOURCES.txt'
reading manifest file 'json_save.egg-info/SOURCES.txt'
writing manifest file 'json_save.egg-info/SOURCES.txt'
installing library code to build/bdist.macosx-10.13-x86_64/egg
running install_lib
running build_py
creating build
creating build/lib
creating build/lib/json_save
copying json_save/json_save_meta.py -> build/lib/json_save
copying json_save/saveables.py -> build/lib/json_save
copying json_save/__init__.py -> build/lib/json_save
copying json_save/json_save_dec.py -> build/lib/json_save
creating build/lib/json_save/test
copying json_save/test/__init__.py -> build/lib/json_save/test
copying json_save/test/test_savables.py -> build/lib/json_save/test
copying json_save/test/test_json_save_dec.py -> build/lib/json_save/test
copying json_save/test/test_json_save_meta.py -> build/lib/json_save/test
creating build/bdist.macosx-10.13-x86_64
creating build/bdist.macosx-10.13-x86_64/egg
creating build/bdist.macosx-10.13-x86_64/egg/json_save
copying build/lib/json_save/json_save_meta.py -> build/bdist.macosx-10.13-x86_64/egg/json_save
creating build/bdist.macosx-10.13-x86_64/egg/json_save/test
copying build/lib/json_save/test/__init__.py -> build/bdist.macosx-10.13-x86_64/egg/json_save/test
copying build/lib/json_save/test/test_savables.py -> build/bdist.macosx-10.13-x86_64/egg/json_save/test
copying build/lib/json_save/test/test_json_save_dec.py -> build/bdist.macosx-10.13-x86_64/egg/json_save/test
copying build/lib/json_save/test/test_json_save_meta.py -> build/bdist.macosx-10.13-x86_64/egg/json_save/test
copying build/lib/json_save/saveables.py -> build/bdist.macosx-10.13-x86_64/egg/json_save
copying build/lib/json_save/__init__.py -> build/bdist.macosx-10.13-x86_64/egg/json_save
copying build/lib/json_save/json_save_dec.py -> build/bdist.macosx-10.13-x86_64/egg/json_save
byte-compiling build/bdist.macosx-10.13-x86_64/egg/json_save/json_save_meta.py to json_save_meta.cpython-36.pyc
byte-compiling build/bdist.macosx-10.13-x86_64/egg/json_save/test/__init__.py to __init__.cpython-36.pyc
byte-compiling build/bdist.macosx-10.13-x86_64/egg/json_save/test/test_savables.py to test_savables.cpython-36.pyc
byte-compiling build/bdist.macosx-10.13-x86_64/egg/json_save/test/test_json_save_dec.py to test_json_save_dec.cpython-36.pyc
byte-compiling build/bdist.macosx-10.13-x86_64/egg/json_save/test/test_json_save_meta.py to test_json_save_meta.cpython-36.pyc
byte-compiling build/bdist.macosx-10.13-x86_64/egg/json_save/saveables.py to saveables.cpython-36.pyc
byte-compiling build/bdist.macosx-10.13-x86_64/egg/json_save/__init__.py to __init__.cpython-36.pyc
byte-compiling build/bdist.macosx-10.13-x86_64/egg/json_save/json_save_dec.py to json_save_dec.cpython-36.pyc
creating build/bdist.macosx-10.13-x86_64/egg/EGG-INFO
copying json_save.egg-info/PKG-INFO -> build/bdist.macosx-10.13-x86_64/egg/EGG-INFO
copying json_save.egg-info/SOURCES.txt -> build/bdist.macosx-10.13-x86_64/egg/EGG-INFO
copying json_save.egg-info/dependency_links.txt -> build/bdist.macosx-10.13-x86_64/egg/EGG-INFO
copying json_save.egg-info/top_level.txt -> build/bdist.macosx-10.13-x86_64/egg/EGG-INFO
zip_safe flag not set; analyzing archive contents...
creating dist
creating 'dist/json_save-0.4.0-py3.6.egg' and adding 'build/bdist.macosx-10.13-x86_64/egg' to it
removing 'build/bdist.macosx-10.13-x86_64/egg' (and everything under it)
Processing json_save-0.4.0-py3.6.egg
Copying json_save-0.4.0-py3.6.egg to /Users/brew/.virtualenvs/mailroom/lib/python3.6/site-packages
Adding json-save 0.4.0 to easy-install.pth file

Installed /Users/brew/.virtualenvs/mailroom/lib/python3.6/site-packages/json_save-0.4.0-py3.6.egg
Processing dependencies for json-save==0.4.0
Finished processing dependencies for json-save==0.4.0
```

And now when you check
```
pip list
```

you will see the json_save package. 

```
(mailroom) brew@ontario:/tmp/json_save$ pip list
Package          Version
---------------- -------
appnope          0.1.0
backcall         0.1.0
decorator        4.3.0
ipython          6.3.1
ipython-genutils 0.2.0
jedi             0.12.0
json-save        0.4.0  # Here it is!
parso            0.2.0
```
etc....

And now you can use the module to do the exercise.
