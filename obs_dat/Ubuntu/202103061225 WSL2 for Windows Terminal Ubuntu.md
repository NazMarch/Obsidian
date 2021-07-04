#Ubuntu 
First allow all subsystems


##### powershell as admin
```shell

dism.exe /online /enable-feature /featurename:Microsoft-Windows\-Subsystem-Linux /all /norestart

dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

wsl --set-default-version 2
```

Then install Ubuntu 

Go to `cd ~` and use `vim .bashrc`
Delete lines with `dircolors` and test below

In the end of .bashrc write 


##### .bashrc
```shell
eval "$(dircolors -p | \
    sed 's/ 4[0-9];/ 01;/; s/;4[0-9];/;01;/g; s/;4[0-9] /;01 /' | \
    dircolors /dev/stdin)"
```

After that use `source .bashrc` to apply changes

