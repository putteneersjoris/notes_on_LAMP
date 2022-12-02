# miniconda documentation

make empty conda environment with packages 
<pre>
<code>
$ conda create -n 'env_name' pip  python=3.6 scipy
</code>
</pre>

list all conda environments
<pre>
<code>
$ conda env list
</code>
</pre>

activate conda environment
<pre>
<code>
$ conda activate 'env_name'
</code>
</pre>

install packages
<pre>
<code>
$ conda install pip
</code>
</pre>

check installed packages
<pre>
<code>
$ conda list
</code>
</pre>

deactivate environment
<pre>
<code>
$ conda deactivate 'env_name'
</code>
</pre>

delete conda environment
<pre>
<code>
$ conda env remove -n 'env_name''
</code>
</pre>

export yml file
<pre>
<code>
$ conda env export -f conda_export.yml
</code>
</pre>
        
create conda environment with .yml file
<pre>
<code>
$ conda env create -f conda_export.yml
</code>
</pre>


.yml file layout example
<pre>
<code>
name: machine-learning-env

dependencies:
  - ipython=7.13
  - matplotlib=3.1
  - pandas=1.0
  - pip=20.0
  - python=3.6
  - scikit-learn=0.22
</code>
</pre>



        


        


        