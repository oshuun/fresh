#!/bin/bash
# Fresh install, version 1

# Run as root.

ROOT_UID=0    # Only users with $UID 0 have root privileges
E_NOTROOT=87  # Non-root exit error
ORIG_DIR=$PWD # There if user wants to return to original working directory

ALIASES=\
"\nalias search='pacman -Ss'\n\
alias searchy='yay -Ss'\n\
alias remove='pacman -Rs'\n\
alias temacs='emacs -nw'"

cd $HOME

echo "Creating aliases..."

if [ "$SHELL" == "/bin/bash" ]
then
	echo -e ${ALIASES} >> .bashrc
elif [ "$SHELL" == "/bin/zsh" ]
then
	echo -e ${ALIASES} >> .zshrc
else
	echo "Can't create aliases."
	echo "Current shell: $SHELL"
	echo "Supported shells: bash, zsh"
	exit 1
fi


# Install packages
# Official repositories:
#	[
#		-base-devel
#		-code
#		-emacs
#		-ffmpeg
#		-git
#		-neofetch
#		-vlc
#		-xclip
#		-yay
#	]
# AUR:
#	[
#		-google-chrome
#	]

echo "Installing packages..."

sudo pacman -Syu yay vlc base-devel ffmpeg code neofetch emacs git xclip

yay -Syu google-chrome

echo $ORIG_DIR

exec $SHELL

