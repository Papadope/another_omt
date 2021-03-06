# Another Oh-My-Tmux script, for HackTheBox or TryHackMe

# Setup THM tmux steps (with the ip addr checker script)
	cd /opt
	sudo git clone https://github.com/OreoByte/another_omt.git
	cd another_omt/
	sudo chmod +x thm_vpn
	cp /opt/another_omt/tmux.conf-byte ~/.tmux.conf

# Changing to the curl connection checker script (after first setup)
	Comment out the ip addr checker line
		#set -ag status-right " #[fg="#34ebe1"]#(/opt/another_omt/thm_vpn)"

	Uncomment the curl connection checker line
		set -ag status-right " #[fg="#ab2fad"]#(/opt/another_omt/curl_thm_vpn)"

	don't forget to chmod the curl-thm-vpn script
		chmod +x /opt/another_omt/curl_thm_vpn

# testing the tmux script on the next launch of tmux
	tmux

	update tmux script
		tmux source-file ~/.tmux.conf
	update tmux script within tmux session
		:source-file ~/.tmux.conf

# If borked remote or rename the .tmux.conf file
	rm ~/.tmux.conf
	mv ~/.tmux.conf ~/.tmux.conf.broken

# Loading vpn check script with tmux if .tmux.conf doesn't load them (OLD)
	tmux set -ag status-right " #[fg="#dd99ff"]#(~/another_omt/curl_thm_vpn)"
	OR
	tmux set -ag status-right " #[fg="#34ebe1"]#(~/another_omt/thm_vpn)"

	OR "Older version of tmux doesn't auto load hex-color codes, use color names"
	set -ag status-right " #[fg="red"]#(~/another_omt/curl_thm_vpn) "
	set -ag status-right " #[fg="cyan"]#(~/another_omt/thm_vpn) "
		# Make sure to comment out the other lines with hex-color codes

# Use the Updated VPN lines instead that don't break Reloading the .tmux.conf config file
	set -g status-right " #[fg="#c299ff"]#H#[default] %H:%M %d-%b-%y #[fg="#dd99ff"]#(~/another_omt/curl_thm_vpn) #[fg="#34ebe1"]#(~/another_omt/thm_vpn) "
	OR
	set -g status-right " #[fg="cyan"]#H#[default] %H:%M %d-%b-%y #[fg="red"]#(~/another_omt/curl_thm_vpn) #[fg="green"]#(~/another_omt/thm_vpn) "

# Home dir install script (for the main file)
	#!/bin/bash
	# also comes with the repo as oreo-setup-script.sh
	cd ~/
	git clone https://github.com/OreoByte/another_omt.git
	chmod +x ~/another_omt/thm_vpn
	chmod +x ~/another_omt/curl_thm_vpn
	cp ~/another_omt/tmux.conf-byte ~/.tmux.conf
