# Tmux for Termux
Have you ever wonder how to open multiple sessions in a singel screen in [termux]().

Here is a solution, an open source terminal multiplexer for Linux or Unix operating systems.

>I often used this alot while writing program. 

It was developed by [Nicholas Marriott](https://github.com/nicm) and contribute by [Thomas Adam](https://github.com/ThomasAdam) , [Ben Boeckel](https://github.com/mathstuf) and many more you can check it in the [GitHub Contribution page](https://github.com/tmux/tmux/graphs/contributors).

Tmux is written in C Language and it's open sourced at GitHub. If you think that you can improve the program than you can contribute at [Tumx](https://github.com/tmux/tmux).

> You can visit my GitHub account [jyotirmoydotdev](https://github.com/jyotirmoydotdev) and follow me i contribute c++ programmes which will help you to learn c++ .

Now let me tell you who to use it and gain all the full potential of this program.

## Installation 🔧

To install tumx in your termux you will first need to update the packages by typing...

    pkg update && pkg upgrade

After that you need to type a command which will basically install the tumx

    pkg install tmux

## Basic command

After you successfully install tmux. You will see message like this 

    Unpacking tmux (3.2) ...
    Setting up tmux (3.2) ...
    Processing triggers for man (1.14.5-2) ...

Now move on the basic commands.

To start the program, first simply type :

    tmux

Remember if you want to use this command than first you need to type <br>` CTRL + b ` after than the command.

> <b>Eg</b> : To split a screen in vertical orientation your need to first type ` CTRL + b ` after than " % " percentage symbol.

| Command | Description |
| - | - |
| % | Vertical Split      |
| " | Horizontal split |
| z | Full screen mode for current pane |
| o | Go to next pane |
| x | Kill pane |

This are the command commonly use there are more advance thing which i will covering in the part 2.

Here are some of the extra command which will be useful

<b>Note </b>:  For this command you don't need to type `CTRL + b ` .

| Command | Description |
| - | - |
| tmux | Start tmux |
| tmux new -s "name" | Start tmux with "name" |
| tmux ls | Show the list of session |
| tmux kill-session -t "name" | Kill the session "name" |
| tmux kill-server | Stop the program |

To get all the command list type ` CTRL + b ` and then "?" question mark.

Thank you for reading this far. If there is any mistake than a humble sorry 🙇 and leave a comment.

Do follow me on Twitter to get the latest update.
<a href="https://twitter.com/jyotirmoydotdev?ref_src=twsrc%5Etfw" class="twitter-follow-button" data-show-count="false"><img src="https://img.shields.io/badge/-_@jyotirmoydotdev_-blue?style=flat&logo=twitter&logoColor=white">
</a><script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

