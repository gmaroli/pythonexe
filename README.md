# pythonexe
Steps to create Python executable file that can be run on system without python

Pre-requisite: Python 3.x should be installed 
These steps are created with Python 3.6.5 and IDE used in PyCharm
1. Create a project in PyCharm
2. Add a new python file for your script
3. Install cx_Freeze using cmd prompt(if using venv then in your project folder navigate to venv/Scripts folder and execute: 'pip install cx_Freeze')
4. Install idna (same as step 3) : Details:  https://pypi.org/project/idna/
5. Create a new python file in the same project called 'setup.py'
6. Enter the below code in setup.py file:
	from cx_Freeze import setup, Executable

	base = None    

	executables = [Executable("<Python_Script>", base=base)]

	packages = ["idna"]
	options = {
	    'build_exe': {    
	        'packages':packages,
	    },    
	}

	setup(
	    name = "<any name>",
	    options = options,
	    version = "<any number>",
	    description = '<any description>',
	    executables = executables
	)
Notes: 
	Python_Script: name of the python script along with .py extension that needs to be converted to a exe
	enter each of the imported packages from the python script under the packages section (example: packages = ["idna", "os", "sys"])
	Provide any name , number and description under setup section above
7. open the terminal in Pycharm and enter the command: python setup.py build
8. under your project directoy a new folder will be created 'build'
9. exe file will be created under this build folder

Run the executable.
