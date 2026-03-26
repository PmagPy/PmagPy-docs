# Command line programs

**PmagPy** can also be used on the command line through the command line 
programs.

Here is a brief introduction to how the **PmagPy** command-line programs
work. All **PmagPy** programs print a help message out if you type:
“**program_name.py -h**” on the command line. Many have an “interactive”
option triggered by typing **program_name.py -i**. Many also allow
reading from . The help
message will explain how each particular program functions. There are
some common features for the command line options:

- Switches are from one to three characters long, preceded by a ’-’.
- The switch ’-h’ always prints the help message and ’-i’ allows
  interactive entry of options.
- Options for command line switches immediately follow the switch. For
  example: -f INPUT -F OUTPUT will set the input file to INPUT and the
  output to OUTPUT.
- The switch for input files all start with -f and -F for output files.
- -spc -sam -sit -syn -loc are switches relating to specimens, samples,
  sites, synthetics and locations respectively.
- Capitalized switches suppress an option (e.g., -A means do not
  average, while -a means DO average).
- -crd \[s,g,t\] sets the coordinate system
- -fmt \[svg,png,jpg\] the default image format.
- -sav saves the plots silently and quits the program

Depending on your operating system, you may need to use a different
command to invoke a command line program. See installation instructions
 for details.

You can see examples for each program on the [\*\*PmagPy-cli\*\*
page](http://pmagpy.github.io/PmagPy-cli.html). The data files used
in the examples are located in the *data_files* directory bundled with
the **PmagPy** software distribution.