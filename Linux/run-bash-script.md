# To run Bash Script anywhere on your computer 


1. Create a directory whereever you want to save your script files. In this example it is under home directory.
```
mkdir myscript
```

2. Add myscript path to your terminal configuration file. (either, .bashrc or .zshrc)

```
vim .zshrc
```
```
export PATH="$PATH:$HOME/myscript"
```
3. Reload the config file:

```
source .zshrc
```

`Final Note ==> you need to save all your script file in myscript directory. Then, anywhere on your computer you can run your scripts. DO NOT FORGET TO MAKE your script files executable:`

```
chmod 755 scripfilename.sh
```
```
chmod +x scriptfilename.sh
```

4. Now, anywhere on your computer just write your script file name and hit the enter.

```
scriptfilename.sh
```
