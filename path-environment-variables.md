# Path environment variables

The AIR SDK contains a few programs that can be launched from a command line or
terminal. Running these programs can often be more convenient when the path to
the SDK bin directory is included in the path environment variable.

The information presented here discusses how to set the path on Windows, Mac,
and Linux and should serve as a convenient guide. However, computer
configurations vary widely, so the procedure does not work for every system. In
these cases, you should be able to find the necessary information from your
operating system documentation or the Internet.

## Setting the PATH on Linux and Mac OS using the Bash shell

When you type a command in a terminal window, the shell, a program that reads
what you typed and tries to respond appropriately, must first locate the command
program on your file system. The shell looks for commands in a list of
directories stored in an environment variable named \$PATH. To see what is
currently listed in the path, type:

    echo $PATH

This returns a colon-separated list of directories that should look something
like this:

    /usr/bin:/bin:/usr/sbin:/usr/local/bin:/usr/x11/bin

The goal is to add the path to the AIR SDK bin directory to the list so that the
shell can find the ADT and ADL tools. Assuming that you have put the AIR SDK at
`/Users/fred/SDKs/AIR`, then the following command will add the necessary
directories to the path:

    export PATH=$PATH:/Users/fred/SDKs/AIR/bin:/Users/fred/SDKs/android/tools

> **Note:** If your path contains blank space characters, escape them with a
> backslash, as in the following:
>
>     /Users/fred\ jones/SDKs/AIR\ 2.5\ SDK/bin

You can use the `echo` command again to make sure it worked:

    echo $PATH
    /usr/bin:/bin:/usr/sbin:/usr/local/bin:/usr/x11/bin:/Users/fred/SDKs/AIR/bin:/Users/fred/SDKs/android/tools

So far so good. You should now be able to type the following commands and get an
encouraging response:

    adt -version

If you modified your \$PATH variable correctly, the command should report the
version of ADT.

There is still one problem, however; the next time you fire up a new terminal
window, you will notice that the new entries in the path are no longer there.
The command to set the path must be run every time you start a new terminal.

A common solution to this problem is to add the command to one of the start-up
scripts used by your shell. On Mac OS, you can create the file, .bash_profile,
in the ~/username directory and it will be run every time you open a new
terminal window. On Ubuntu, the start-up script run when you launch a new
terminal window is .bashrc. Other Linux distributions and shell programs have
similar conventions.

To add the command to the shell start-up script:

1.  Change to your home directory:

        cd

2.  Create the shell configuration profile (if necessary) and redirect the text
    you type to the end of the file with "`cat >>`". Use the appropriate file
    for your operating system and shell. You can use `.bash_profile` on Mac OS
    and `.bashrc` on Ubuntu, for example.

        cat >> .bash_profile

3.  Type the text to add to the file:

        export PATH=$PATH:/Users/cward/SDKs/android/tools:/Users/cward/SDKs/AIR/bin

4.  End the text redirection by pressing `CTRL-SHIFT-D` on the keyboard.

5.  Display the file to make sure everything is okay:

        cat .bash_profile

6.  Open a new terminal window to check the path:

        echo $PATH

    Your path additions should be listed.

If you later create a new version of one of the SDKs into different directory,
be sure to update the path command in the configuration file. Otherwise, the
shell will continue to use the old version.

## Setting the Path on Windows

When you open a command window on Windows, that window inherits the global
environment variables defined in the system properties. One of the important
variables is the path, which is the list of directories that the command program
searches when you type the name of a program to run. To see what is currently
included in the path when you are using a command window, you can type:

    set path

This will show a list of semicolon-separated list of directories that looks
something like:

    Path=C:\WINDOWS\system32;C:\WINDOWS;C:\WINDOWS\System32\Wbem

The goal is to add the path to the AIR SDK bin directory to the list so that the
command program can find the ADT and ADL tools. Assuming that you have put the
AIR SDK at `C:\SDKs\AIR`, you can add the proper path entry with the following
procedure:

1.  Open the System Properties dialog from the Control Panel or by
    right-clicking on the My Computer icon and choosing Properties from the
    menu.

2.  Under the Advanced tab, click the Environment Variables button.

3.  Select the Path entry in the System variables section of the Environment
    Variables dialog

4.  Click Edit.

5.  Scroll to the end of the text in the Variable value field.

6.  Enter the following text at the very end of the current value:

        ;C:\SDKs\AIR\bin

7.  Click OK in all the dialogs to save the path.

If you have any command windows open, realize that their environments are not
updated. Open a new command window and type the following command to make sure
the paths are set up correctly:

    adt -version

If you later change the location of the AIR SDK, or add a new version, remember
to update the path variable.
