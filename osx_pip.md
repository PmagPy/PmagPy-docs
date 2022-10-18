<h2 id="install-pmagpy">Install PmagPy</h2>
<ul>
<li><p>Install pmagpy and pmagpy-cli:</p>
<pre><code>
  pip install --upgrade pmagpy --no-deps
  pip install --upgrade pmagpy-cli --no-deps</code></pre></li>
<li><p>If you are getting weird install errors, try uninstalling and
then force reinstalling with this:</p>
<pre><code>  pip uninstall pmagpy pmagpy-cli
  pip install pmagpy --upgrade --no-deps --force-reinstall --no-cache-dir
  pip install pmagpy-cli --upgrade --no-deps --force-reinstall --no-cache-dir
</code></pre></li>
</ul>
<h2 id="test-pmagpy">Test PmagPy</h2>
<p>Test core functionality:</p>
<ul>
<li><p>On your command line, type “python” to start the interpreter. You
will import pmagpy and then run a simple calculation. Importing pmagpy
may take over a minute the first time, so be patient! It will be much
faster in subsequent runs.</p>
<pre><code>&gt;&gt;&gt; from pmagpy import pmag
&gt;&gt;&gt; pmag.angle([350.0,10.0],[320.0,20.0])
array([30.59060998])
&gt;&gt;&gt;</code></pre></li>
</ul>
<p>Test the GUIs:</p>
<ul>
<li><p>On the command line, open Pmag GUI by running:</p>
<pre><code>pmag_gui_anaconda</code></pre></li>
</ul>
<p>Remember that the program may be very slow to initialize the first
time! You may also need to resize the GUI window. If the program doesn’t
open or you get an error message, go back and carefully follow the
install instructions to make sure you didn’t miss a step. If you still
have a problem, try the <a
href="https://earthref.org/PmagPy/cookbook/#trouble">Troubleshooting
section</a>. If you don’t find an answer there, check out the existing
<a href="https://github.com/PmagPy/PmagPy/issues">Github issues</a> and
create a new one if necessary.</p>
<h2 id="finishing-up">Finishing up</h2>
<p>Accessing example data files:</p>
<p>There are many data files used in the examples of programs and for
use with the textbook <a
href="http://earthref.org/MAGIC/books/Tauxe/Essentials/WebBook3.html">Essentials
of Paleomagnetism</a>. You may want to copy the data files to your
Desktop or another convenient location. To do this, navigate on the
command line to your desired destination folder (for help, see <a
href="https://earthref.org/PmagPy/cookbook/#file_system">this Cookbook
section</a>). Then, use the command:</p>
<pre><code>  move_data_files.py</code></pre>
<p>This will copy all of the PmagPy example files to your current
directory. NB: If you have a developer install, you can simply navigate
to PmagPy/data_files, and move_data_files.py will not be needed.</p>
<h2 id="keeping-pmagpy-up-to-date">Keeping PmagPy up-to-date</h2>
<p>To stay up to date with new features and bug fixes, you should
periodically update both <span><strong>PmagPy</strong></span>
packages.</p>
<pre><code>
  pip install pmagpy --upgrade --no-deps</code></pre>
<p>To check the currently installed version number for pmagpy (or any
other Python package), run:</p>
<pre><code>  conda list</code></pre>
<p>If you ever need to uninstall pmagpy or pmagpy-cli:</p>
<pre><code>
  pip uninstall pmagpy</code></pre>
<p>or</p>
<pre><code>  pip uninstall pmagpy-cli</code></pre>
<h1 id="next-steps">Next steps</h1>
<p>Back to the <a
href="https://earthref.org/PmagPy/cookbook/#next_steps">Cookbook</a>!</p>