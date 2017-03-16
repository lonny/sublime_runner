# sublime_runner
A Ruby script enabling optional "reopen files" behavior in Sublime Text with the same ease as Textmate.

**Why It Was Needed**

When switching from TextMate to [Sublime Text 3](https://www.sublimetext.com/3), I noticed that then you restart the editor in a project directory, it does not reopen project files you were last editing  in the same way TextMate does automatically. The "reopen files" behavior of Sublime Text is very different and inconsistent. I find it frustrating and annoying.

This little script takes the frustration out of it.

TextMate stores information about your project. When you start it up again in a project directory, it resumes pretty much where you left off. In a different project directory, it opens that project's files in a similar manner.

Sublime Text, not so much. If you have the "hot_exit" setting turned on, it will restore edited files and the state they were in when you last quit editing them, **only if** you quit the whole program, not if you just closed the window. If you close the window and then open a new one or restart the editor, your files will not be reopened.

Worse: if you "hot exit", then switch to a different project directory and start it again, the files from the first project will be opened, not the current project.

To complicate matters further, Sublime allows you to "save your workspace" in a project directory, which creates a "<your_supplied_name>.sublime-workspace" file in your project. With that in place, your files will be reopened if you start the editor... unless you start the editor from the command line. In which case you must supply the name of your .sublime-workspace file in the command.

So whether your files will reopen -- and even *which* files will be opened -- when you start the editor depends entirely on (A) how you last closed the editor, (B) how you start it back up again, and (C) whether you remember and type in manually the name of a state file Sublime should be able to find by itself.

That is terribly inconsistent and I find it troublesome and aggravating.

**What It Does**

This script allows you to start Sublime Text via the command line with one simple command and get consistent results. Go to a project directory, type in "sublime", and your project files will reopen as they were when you last quit. Go to a different project, type "sublime", and get **that** project's last state restored. No need to to worry about whether you closed the program or just closed the window, and no need to remember the name of a .sublime-workspace file.

You can also supply a filename to open just one file, or a directory name (or .) to open a directory with no files pre-opened, just as you normally can with this sort of code editor.

**Set It Up**

Download the file named sublime. Edit the first line (the "shebang") to point to your own Ruby interpreter.

Put it somewhere in your path. I put mine in /usr/local/bin. Make it executable: "chmod 755 sublime".

(To find Ruby, enter "which ruby" on the command line. If you don't have it, look up how to install it.)

**How It Works**

Open a project in Sublime Text, and click Project > Save Workspace As...

Give it a name for your .sublime-workspace file, and make sure it is saved in the main project directory.

After that, just go to the project directory in your terminal or console, type "sublime", and hit Enter.

It will find the .sublime-workspace file in that directory and open Sublime Text using that saved information. If it doesn't find one, it will open the current directory in the sidebar with no files open in the editor.

Every time. Simple and consistent.

If you like, you can supply a filename: "sublime foo" to open a single file. Or "sublime ~/bar" to open the ~/bar directory.

**Tips**

Give your .sublime-workspace file a name starting with a . like ".project_name.sublime-workspace". Sublime will warn you about the file being hidden but it works fine and you won't see it in your sidebar.

Don't forget to add your .sublime-workspace file to .gitignore.

**Parting Words**

Sublime Text is a very unfortunate name. For a long time I let the name bias me against what is actually a very good, if quirky, code editor. I finally decided to switch anyway, mainly because the TextMate crew simply refuses to support split windows. That has been a missing feature for far too long and the developers have expressed zero interest in filling that demand, even though for years it was the most-requested feature.

Despite the quirks I am finding even more to like in Sublime Text. It is becoming my go-to code editor.
