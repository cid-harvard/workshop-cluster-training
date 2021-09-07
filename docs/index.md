# Effective Cluster Usage and Data Management

Tuesday, Sep 07, 2021.

### Pre-requisites

Please perform the following steps **before the workshop**, in the interest of time:

- You should have an account on the [RCE Cluster](https://rce-docs.hmdc.harvard.edu/). If you do not have an account, look at [Accessing the RCE](https://rce-docs.hmdc.harvard.edu/book/accessing-rce-0) for instructions on how to obtain one.
- You should be able to login to the cluster using the graphical client [instructions here](https://rce-docs.hmdc.harvard.edu/nx4)

### Setup

- If you're using Windows, download and install [PuTTY](https://www.putty.org/)
- If you're on a Mac, download and install [Xquartz](https://www.xquartz.org/)
- Download and install [FileZilla](https://rce-docs.hmdc.harvard.edu/book/installing-filezilla)
    + If you can follow the instructions [here](https://rce-docs.hmdc.harvard.edu/book/configuring-filezilla), go ahead and configure FileZilla.
- Download and install [Atom](https://atom.io/)
    + If you already know how to, go ahead and install the following packages for Atom:
        - [remote-ftp](https://atom.io/packages/remote-ftp)
        - [hydrogen](https://atom.io/packages/hydrogen)
        - [language-stata](https://atom.io/packages/language-stata)
- Download and install [miniconda](https://docs.conda.io/en/latest/miniconda.html), if you don't already have conda.


### Workshop Topics

- Project folder structures and data management
    + How to achieve sanity when your project's folders and data are a mess (i.e. restructuring your project's folders)
    + Data management for CID
        - Planning for a new project
        - Folder structures
        - Best practices and documentation
        - Scripts for reorganizing existing folders
- Cluster usage
    + Basic terminal usage
    + How to submit jobs on the cluster and manage them
    + Using Atom to edit files remotely
    + Using FileZilla to upload / download files
    + Using Python / Stata remotely
- Tips / tricks:
	+ How to write code that other people can run
    + How to run Python / R / Stata code on the cluster without explicitly having to open the cluster's interface
    + Brief intro to parallel computing
