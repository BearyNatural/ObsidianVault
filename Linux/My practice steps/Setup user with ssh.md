ensure ssh is enabled:
	systemctl status ssh %% active (running) %%
	IF NOT:
		sudo apt install openssh-server -y
		systemctl start ssh

issues with windows 10 - wsl installed, not allowing updates and not allowing install of ssh :'()'

%% search for commands with key words %%
man -k user
man -k keygen

