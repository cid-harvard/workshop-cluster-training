
## Working with Linux
The FASRC cluster runs on Linux. This section discusses some commands that might be useful for everday cluster usage through the terminal:

- Change directory: `cd <path to directory>`
- Create new folder in current directory: `mkdir <name of new folder>`
- List contents of current directory: `ls`
    + Including hidden files: `ls -al`
    + With file sizes in KB/MB/GB instead of bytes: `ls -alh`
- Create an empty file: `touch <filename>`
- Open a Vim text editor: `vi <filename>` (There are a bunch of vim specific commands you need to learn to use Vim)
- Output the contents of a text file: `cat <filename>`
- Output the first few lines of a file: `head <filename>`
- Copy file: `cp <old_file_path> <new_file_path>`
- Move file: `mv <old_file_path> <new_file_path>`
- Rename file: `mv <old_file_name> <new_file_name>`
- Remove file: `rm <file_name>`

For more commonly used commands, [here's](https://www.cheatography.com/davechild/cheat-sheets/linux-command-line/) a cheatsheet

## SLURM commands
``` bash
# Adapted from https://vsoch.github.io/lessons/sherlock-jobs/
# Show the overall status of each partition
sinfo

# Submit a job
sbatch jobFile.job

# See the entire job queue
squeue

# See only jobs for a given user
squeue -u username

# Count number of running / in queue jobs
squeue -u username | wc -l

# Get estimated start times for your jobs (when Sherlock is busy)
squeue --start -u username

# Show the status of a currently running job
sstat -j jobID

# Show the final status of a finished job
sacct -j jobID

# Kill a job with ID $PID
scancel $PID

# Kill ALL jobs for a user
scancel -u username

# Kill all pending jobs
scancel -u username --state=pending

# Run interactive node with 16 cores (12 plus all memory on 1 node) for 4 hours:
srun -n 12 -N 1 --mem=64000 --time 4:0:0 --pty bash

# Claim interactive node for exclusive use, 8 hours
srun --exclusive --time 8:0:0 --pty bash

# Same as above, but with X11 forwarding
srun --exclusive --time 8:0:0 --x11 --pty bash

# Same as above, but with priority over your other jobs
srun --nice=9999 --exclusive --time 8:0:0 --x11 --pty -p dev -t 12:00 bash

# Check utilization of group allocation
sacct

# Running jobs in the group allocation
srun -p groupid
sbatch -p groupid

# Stop/restart jobs interactively
# To stop:
scancel -s SIGSTOP job id

# To restart (this won't free up memory):
scancel -s SIGCONT job id

# Get usage for file systems
df -k
df -h $HOME

# Get usage for your home directory 
du

# Counting Files
find . -type f | wc -l

# Check lab disk quota
# Based on https://docs.rc.fas.harvard.edu/kb/faq/
lfs quota -hg hausmann_lab /n/holystore01
lfs quota -hg hausmann_lab /n/holylfs05
```

## Tips for quickly connecting to FASRC (Mac or Linux only)

Set up custom command `sshody` to ssh from laptop to RC: aliased to 
``` bash
ssh -o ServerAliveInterval=30 -CY username@login.rc.fas.harvard.edu
```

For new connections, you can then do `ssh ody` to piggyback off the first connection using ControlMaster

For piggybacking, the following settings need to be enabled in `~/.ssh/config`:

``` bash
Host *
 AddKeysToAgent yes
 UseKeychain yes
 IdentityFile ~/.ssh/id_rsa
 XAuthLocation /opt/X11/bin/xauth

Host login.rc.fas.harvard.edu odyssey ody
 HostName login.rc.fas.harvard.edu
 User shreyasgm
 ControlMaster auto
 ControlPath ~/.ssh/%r@%h:%p
 ForwardAgent yes
 ForwardX11Trusted yes
```