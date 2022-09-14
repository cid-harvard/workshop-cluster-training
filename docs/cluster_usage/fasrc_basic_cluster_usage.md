!!! note "FASRC documentation"
    - This page is intended to provide a basic overview of how to use the FASRC cluster.
    - A [quickstart guide](https://docs.rc.fas.harvard.edu/kb/quickstart-guide/) is available on FASRC's documentation page.
    - For more detailed information, please see the [FASRC User Guide](https://docs.rc.fas.harvard.edu/user-guide/).

## Introduction to FASRC
A compute cluster (used to be called supercomputers) is essentially a set of computers tied together, allowing for larger scale / shared usage. The FASRC cluster is a shared resource for the Harvard community, managed by the [FAS Research Computing](https://www.rc.fas.harvard.edu/) group.

The [RCE cluster](https://rce-docs.hmdc.harvard.edu/book/rce-docs) is shutting down entirely on November 1st, 2022, and all users and projects are being migrated to FASRC. Note that the RCE support teams from IQSS will continue to be the Growth Lab's point of contact for FASRC support requests.

## Pre-requisites

- You should have a Harvard ID, and have an account on FASRC. If you don't have an account on FASRC yet, please sign up [here](https://portal.rc.fas.harvard.edu/request/account/new) and request access to `hausmann_lab`. Email Andrea Hayes for approval once you're done with these steps.
- You should have the [FASRC VPN](https://docs.rc.fas.harvard.edu/kb/vpn-setup/) setup
- You should have [two-factor authentication setup](https://docs.rc.fas.harvard.edu/kb/openauth/) for your FASRC account.
- For GL users who work with confidential data (almost all applied projects do), you should have completed the necessary research data security trainings. Link to the university-wide training is [here](https://trainingportal.harvard.edu/Saba/Web_spf/NA1PRD0068/app/me/learningeventdetail/cours000000000020423;spf-url=common%2Fledetail%2Fcours000000000020423). Users who work with human subjects data need additional training certifications. Please contact Andrea Hayes for more information.
- (Optional) If you plan to work on Python, install [VSCode](https://code.visualstudio.com/download) and [Miniconda](https://docs.conda.io/en/latest/miniconda.html#latest-miniconda-installer-links).
- (Optional) Install the [Remote SSH extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack) and the [Python extension](https://marketplace.visualstudio.com/items?itemName=donjayamanne.python-extension-pack) for VSCode.

??? tip "Easy installation for Mac users using Homebrew"
    ``` bash
    # Make sure XCode is installed
    sudo xcode-select --install
    # Install Homebrew
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
    # Check Homebrew installation
    brew doctor
    # Install VSCode
    brew install --cask visual-studio-code
    # Install Miniconda
    brew install --cask miniconda
    # Set paths
    echo 'export PATH=/usr/local/anaconda3/bin:$PATH' >> ~/.bash_profile
    echo 'export PATH=/opt/homebrew/anaconda3/bin:$PATH' >> ~/.bash_profile
    source ~/.bash_profile
    ```

## Jargon

Note that these are not the exact technical definitions of these terms, but my (potentially simplistic) understanding of them.

- FASRC = FAS Research Computing
- Cannon = Cluster for level 2 data. This is where most of the academic group's data lives.
- FASSE = FAS Secure Environment. Cluster for level 3 data. This is where the applied projects' data will live.
- SLURM = a job scheduler that is used to manage jobs on the cluster. This is the scheduler that FASRC uses.
- Partition = A portion of the cluster that is reserved for a specific purpose. For example, the `gpu` partition is reserved for GPU jobs.
- Job = A task that is submitted to the cluster. A job can be a single task, or a series of tasks that are run in sequence.
- Node = an individual server.
- Core = a single CPU.


## Storage
FASRC gives every user 100GB of storage space in your home folder. In addition, the Growth Lab has lab storage available at the following locations:
```
- /n/hausmann_lab/lab/
- /n/holylfs05/LABS/hausmann_lab
```

Applied projects will be moved to FASSE. The GL data committee has submitted requests to FASRC to move RCE projects to FASSE, and the requests are being considered on an individual basis by FASRC for data security review.

## Working with VDI

Great guides available directly on FASRC documentation page:

- [Using VDI](https://docs.rc.fas.harvard.edu/kb/virtual-desktop/)
- [VDI apps](https://docs.rc.fas.harvard.edu/kb/vdi-apps/)
- [FASSE VDI apps](https://docs.rc.fas.harvard.edu/kb/fasse-vdi-apps/)
