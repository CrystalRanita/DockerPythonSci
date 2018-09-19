# DockerPythonSciMac
Docker python with machine learning libs on Mac OS

# In dockerfile
Python 3  
libs: numpy scipy matplotlib scikit-learn pandas

# Construct image
$ git clone https://github.com/CrystalRanita/DockerPythonSciMac  
$ cd DockerPythonSciMac  
$ docker build -t pythonml:v1 .  
(where pythonml is repository name and v1 is tag)  

# Check docker images:
$ docker images
find which one you want to run

# Run container:
docker run -v /Users/host_crystal/:/home/container_crystal -it pythonml:v1 /bin/bash
(where pythonml is repository name and v1 is tag.  
Use -v here mount host location to container's location, modify will kept . 
and can easy use visual studio code to edit code files.)

# Check libs version in container
After container running

>>> python

>>> import numpy
>>> numpy.version.version
'1.15.1'

>>> import scipy
>>> scipy.version.version
'1.1.0'

>>> import matplotlib
print('matplotlib: {}'.format(matplotlib.__version__))
matplotlib: 2.2.3

>>> import sklearn
>>> print('sklearn: {}'.format(sklearn.__version__))
sklearn: 0.19.2

>>> import pandas
>>> print('pandas: {}'.format(pandas.__version__))
pandas: 0.23.4

# Copy host file to container
Instruction: docker cp SourceDir containerID/DestDir  
Example: docker cp MachineLearning/. 069f40db12a2:/target  
Copy host file in MachineLearning directory to container's /target directory  

# Commit change to keep data
if use $ docker run -t -i pythonml:v1 /bin/bash .  
without mount point, after exit container modify will gone without commit.
Instruction: docker commit containerID IMAGE  
docker commit ce7f5ced748c pythonml:v1
