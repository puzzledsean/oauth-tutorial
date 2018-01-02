# OAuth

Following video tutorials from: <br>
https://www.udacity.com/course/authentication-authorization-oauth--ud330

This repo is based on a clone of their starter code with the proper vagrant file: <br>
https://github.com/udacity/OAuth2.0

### Topics Covered
- [x] Lesson 1: Authentication vs Authorization
  - Differences between Authentication vs Authorization
  - Pros and cons of using third party authentication (i.e. G+, Facebook, etc)
- [x] Lesson 2: Creating a Google Sign In (Hybrid auth flow)
  1. Generate anti forgery session states from random alphanumerical characters
  2. Use Google Developer API to get client secrets for a G+ app 
      1. note for future reference: if getting 401 error "Error: Missing property "redirect_uris" in a client type of "web".", go to: https://github.com/google/oauth2client/issues/16
  3. Create basic login page with G+ sign in button
  4. Add client/frontend signin logic
      1. Client authenticates and queries G+ API
      2. G+ API sends one-time code back to Client
      3. Client POSTs one-time code to /gconnect server endpoint
  5. Add server/backend signin logic
      1. Server uses one-time code to query G+ API
      2. Upon success, G+ API sends access token to server for getting basic user info (email, name, pic, etc)
  6. Logging out with G+ revoke endpoint
  7. Basic page protection (i.e. user needs to be logged in to access certain pages)

<hr>

[Original Description]

# OAuth2.0
Starter Code for Auth&amp;Auth course
# Installing the Vagrant VM for ud330 - Authentication & Authorization

**Note: If you already have a vagrant machine installed from previous Udacity courses skip to the 'Fetch the Source Code and VM Configuration' section**

In Lessons 2,3 and 4 of this course, you'll use a virtual machine (VM) to run a web server and a web app that uses it. The VM is a Linux system that runs on top of your own machine.  You can share files easily between your computer and the VM.

We're using the Vagrant software to configure and manage the VM. Here are the tools you'll need to install to get it running:

### Git

If you don't already have Git installed, [download Git from git-scm.com.](http://git-scm.com/downloads) Install the version for your operating system.

On Windows, Git will provide you with a Unix-style terminal and shell (Git Bash).  
(On Mac or Linux systems you can use the regular terminal program.)

You will need Git to install the configuration for the VM. If you'd like to learn more about Git, [take a look at our course about Git and Github](http://www.udacity.com/course/ud775).

### VirtualBox

VirtualBox is the software that actually runs the VM. [You can download it from virtualbox.org, here.](https://www.virtualbox.org/wiki/Downloads)  Install the *platform package* for your operating system.  You do not need the extension pack or the SDK. You do not need to launch VirtualBox after installing it.

**Ubuntu 14.04 Note:** If you are running Ubuntu 14.04, install VirtualBox using the Ubuntu Software Center, not the virtualbox.org web site. Due to a [reported bug](http://ubuntuforums.org/showthread.php?t=2227131), installing VirtualBox from the site may uninstall other software you need.

### Vagrant

Vagrant is the software that configures the VM and lets you share files between your host computer and the VM's filesystem.  [You can download it from vagrantup.com.](https://www.vagrantup.com/downloads) Install the version for your operating system.

**Windows Note:** The Installer may ask you to grant network permissions to Vagrant or make a firewall exception. Be sure to allow this.

## Fetch the Source Code and VM Configuration

**Windows:** Use the Git Bash program (installed with Git) to get a Unix-style terminal.  
**Other systems:** Use your favorite terminal program.

From the terminal, run:

    git clone https://github.com/udacity/OAuth2.0 oauth

This will give you a directory named **oauth** complete with the source code for the flask application, a vagrantfile, and a bootstrap.sh file for installing all of the necessary tools. 

## Run the virtual machine!

Using the terminal, change directory to oauth (**cd oauth**), then type **vagrant up** to launch your virtual machine.


## Running the Restaurant Menu App
Once it is up and running, type **vagrant ssh**. This will log your terminal into the virtual machine, and you'll get a Linux shell prompt. When you want to log out, type **exit** at the shell prompt.  To turn the virtual machine off (without deleting anything), type **vagrant halt**. If you do this, you'll need to run **vagrant up** again before you can log into it.


Now that you have Vagrant up and running type **vagrant ssh** to log into your VM.  change to the /vagrant directory by typing **cd /vagrant**. This will take you to the shared folder between your virtual machine and host machine.

Type **ls** to ensure that you are inside the directory that contains project.py, database_setup.py, and two directories named 'templates' and 'static'

Now type **python database_setup.py** to initialize the database.

Type **python lotsofmenus.py** to populate the database with restaurants and menu items. (Optional)

Type **python project.py** to run the Flask web server. In your browser visit **http://localhost:5000** to view the restaurant menu app.  You should be able to view, add, edit, and delete menu items and restaurants.
