# SecPass Manager
A simple password manager that use in built 'pass' command and gpg keys for encryption

### SDG 9: Industry, Innovation and Infrastructure

## Introduction
SecPass is a simple password management tool that utilizes the linux pass command tool to store passwords inside gpg encrypted files inside a directory 
residing at ~/.password-store. The pass utility uses a series of commands to store passwords, add or delete, edit, generate, synchronze and manipulate 
passwords securely.
In this digital age and being tech women, we use our devices for various activities and we need to keep our eye on security. 
That is storing strong passwords, and files in safe locations. Fortunately, for every usage there are tools and thus as a group we 
created the SecPass as a training project, in hopes of learning how commercial tools like LastPass and Keepass work without putting our
data at risk or spending limited resources.

### Benefits of SecPass

* pass is open source and thus a user can update the application, and the linux community is always identifying bugs and coming up with extensions 
making more desirable than other applicayions.
* One needs not to make any purchase as the pass command in a linux command tool.
* The password.store can remain in your system only, or you can sync it with a private git repository.
* It is encrypted with GnuPG to a level of your choosing
* The pass command is well documented in the man page thus simple to use and debug.
* It is a command line based application but there are GUI extensions available.

## Technologies used
*Project is created with:*
 1. A linux distribution Operating System
 2. A laptop that runs BSD, MacOS Xor any UNIX-derivatives
 3. Workflow tools:
    1. _**pass**_ -provides the centre for the password store and the access to it.
    2. **GnuPG** - offers the tools for encrypting the password store
    3. **dmenu** - it lists the available passwords
    4. **git** - a version control system for software projects which allows access from different locations and restoring old versions.
  
  ## Setup
  1. Initializing the password store 
  ` ` `
  pass init "sally.mukami@womentechsters.org"
  ` ` `
  2. creating and generating GPG keys
  ` ` `
  gpg --full-generate-key
  *GnuPG will create a user ID*
  Real name:
  email address
  Comment
  ` ` `
  3. List your keys and take note of the secret key ID
  ` ` `
  gpg --list-secret-keys --keyid-format LONG
  sec 4096R/ANHGFGRFGRBMGNKLDFOGFIDGYURFYRGRGMJNJJ 2021-06-26 uid
  Sally k <sajhgyd@womentechsers.com>
  ` ` `
  4. with the ID now initiate the pass datastore
    ` ` `
    pass init 'uid'
    ` ` `
  5. You can now Generate and fetch passwords from RSA4096-ENCRYPTED password store.
  
  ## Workflow
  _Enter passwords_
  
  ` ` `
  pass insert socialmedia/somebody@techsters.com/LinkedIn
  pass insert socialmedia/somebody@techsters.com/LinkedIn < password.txt
  ` ` `
  Here **socialmedia** is the directory that holds all the social media accounts and LinkeIn is the name of the account
   
   
   _Retrieving passwords_
   
   ` ` `
   pass socialmedia/somebody@techsters.com/LinkedIn
   ` ` `
   Writes the password to stdout
   
    ` ` `
    pass -c socialmedia/somebody@techsters.com/LinkedIn
    ` ` `
    Writes the retrieved password to the clipboard for 45 seconds
    
  _Generating Passwords_
 ` ` `
 pass generate socialmedia/somebody@techsters.com/LinkedIn 12
 ` ` `
 _Saving the password store_
 ` ` `
 pass git pull
 pass git push
 ` ` `
 

