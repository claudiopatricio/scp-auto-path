# Secure Copy Bash Script with Auto Path feature

This script sends a file from a project directory to the same project directory of another server, this will allow you to work in a project and update the server files in a very easy way.

## Setup

First step is to set the setup variables inside the 'scp-auto-path' file.

```
_SERVER="localhost"
_USER="YOUR_USER"
_SERVERDIR="~/my-project/"
_LOCALDIR="/home/username/my-project"
```

Then you need to set the file as executable

```
$ chmod +x scp-auto-path
```

To execute in any directory you need to copy the executable to '/usr/bin/' or add the path to the user PATH variable (below an example to add it to .bashrc so you won't need to add it every time you open the console)

```
if [ -d "$HOME/scp-auto-path" ]; then
	PATH="$HOME/scp-auto-path:$PATH"
fi
```

## Example of use

The command below will send the file '\~/project-dir/src/lib/' to the remote server directory '\~/project-dir/src/lib/'

```
~/my-project/src/lib/ $ scp-auto-path lib-example.c
```

For this file, this will be the same as:

```
scp /home/username/my-project/lib-example.c YOUR_USER@$localhost:~/my-project/src/lib/
```

# How to create RSA key pair and send to server

To avoid writing the password everytime you send a file, you need to setup a RSA key pair and add it to authorized keys in the remote server.

```$ ssh-keygen -t rsa```

This will create the RSA key pair, you should keep the password empty! After creating the RSA key pair you need to send the public key to the remote server.

```
$ ssh-copy-id username@10.0.0.1
```

Now try to access the server with ssh, if it doesn't work, you should try to fix permissions in the remote server.

# Donate

If you like my work and want to contribute by donating money, check my [Donation page](http://anjo2.com/donate/)

# License
Copyright (c) 2018 Cláudio Patrício

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
