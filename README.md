## gdep

A lightweight submodule manager for git and bitbucket

### Installing

```console
$ curl -sSL https://raw.githubusercontent.com/gambit-labs/gdep/master/gdep > /usr/local/bin/gdep
```

### Key commands

```console
$ pwd
/home/user/my-project
$ ls
README.md my-webpage.html my-script.sh my-css-file.css

$ # Show usage for gdep
$ gdep
Welcome to gdep, the simple git and merurial submodule manager!
It downloads, updates and removes foreign repositories for you in an automated fashion.

Usage:
 - gdep add [vcs type=(hg|git)] [clone url] [refspec (optional)] [folder clone to (optional)] [subfolder to use (optional)]
   This command creates a new subfolder for you. 

   The first argument specifies if you want to clone a git or hg repo.
   The second argument is the clone url, in this form: http[s]://host.xz[:port]/path/to/repo.git/ or ssh://[user@]host.xz[:port]/path/to/repo.git/
   The third argument is optional; which refspec you want to checkout. It may be a branch, bookmark or specific commit. Defaults to the default branch.
   The fourth argument is optional; it specifies the name of the subfolder you want to create. 
      For example; if the clone url is http://github.com/nyeholt/silverstripe-webservices, the folder would be named silverstripe-webservices
   The fifth argument is optional; it may pick a specific subfolder of the cloned repository and use that only. Defaults to use the whole repo.
 
 - gdep update [foldername1] [foldername2] [foldernameN]
   This command updates one or more submodules. If zero arguments are given; it will update all submodules.

 - gdep list
   This command lists all submodules

 - gdep remove [foldername1] [foldername2] [foldernameN]
   This command removes a submodule. At least one argument is required.

$ # Example for a SilverStripe project: Add silverstripe-webservices from Github.
$ gdep add git http://github.com/nyeholt/silverstripe-webservices

$ # Yay! We got the package easily downloaded
$ # See the status of the submodules
$ gdep list
FOLDER  	BRANCH  	COMMIT 		URL
webservices	master  	81062d8513  	http://github.com/nyeholt/silverstripe-webservices

$ ls
README.md my-webpage.html my-script.sh my-css-file.css webservices

$ cat webservices/.gitstate
abcdabcdabcdabcdabcdabcd

$ # If the package was updated; we should refresh our copy too.
$ gdep update webservices

$ cat webservices/.gitstate
dcbadcbadcbadcbadcbadcba

$ # If we then get tired of the package, remove it
$ gdep remove webservices

$ ls
README.md my-webpage.html my-script.sh my-css-file.css

$ gdep list
You haven't added any submodules yet
```

### License

MIT
