## Remote Python Usage

Note that Python can be run either through VDI or through the terminal. 

## Running Python through VDI

## Running Python through the terminal

This is an example workflow for running Python through the terminal. The steps to follow are:

- Connect to the cluster
- Run the batch submission script
- Run `cat juypter.*` and copy the URL
- Open VSCode and use `remote-ssh` to SSH into the cluster
- Connect to the remote Jupyter server by pasting the URL (bottom right of your VSCode window)
- Connect to the appropriate conda environment (top right of your window)

``` bash title="JupyterLab - example batch submission script"
#!/bin/bash
#SBATCH --partition=test
#SBATCH --job-name=jupyter
#SBATCH --ntasks=1
#SBATCH --cpus-per-task=5
#SBATCH --mem-per-cpu=36GB
#SBATCH -t 0-08:00
#SBATCH -e jupyter.err
#SBATCH -o jupyter.out
#SBATCH --mail-type=BEGIN,END,FAIL


# get tunneling info
XDG_RUNTIME_DIR=""
# port=$(shuf -i8000-9999 -n1)
port=9258
node=$(hostname -s)
user=$(whoami)
cluster=$(hostname -f)

echo $cluster

# print tunneling instructions jupyter-log
echo -e "
MacOS or linux terminal command to create your ssh tunnel
ssh -NL ${port}:${cluster}:${port} -NL 8788:${cluster}:8788 ${user}@login.rc.fas.harvard.edu

Forwarded port:same as remote port
Remote server: ${node}
Remote port: ${port}
SSH server: ${cluster}.rc.fas.harvard.edu
SSH login: $user
SSH port: 22

Use a Browser on your local machine to go to:
localhost:${port}  (prefix w/ https:// if using password)
"

module load Anaconda3/2019.10
source activate cid
echo $CONDA_DEFAULT_ENV
jupyter lab --no-browser --port=${port} --ip='0.0.0.0'
```
