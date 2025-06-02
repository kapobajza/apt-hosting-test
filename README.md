# Just testing apt hosting

Welcome. This is a sample repo used to test hosting debian packages on apt. It contains a simple binary, that will simply print "hello packaged world" once executed.

To install the package, follow these steps:

1. Download the GPG keyring and place it inside the `/usr/share/keyrings` directory
```sh
curl -fsSL https://kapobajza.github.io/apt-hosting-test/example-pgp-keyring.gpg | sudo tee /usr/share/keyrings/hello-world-keyring.gpg > /dev/null
```
2. Add the packaging info to a dedicated apt sources file:
```sh
echo "deb [signed-by=/usr/share/keyrings/hello-world-keyring.gpg arch=amd64] https://kapobajza.github.io/apt-hosting-test stable main" | sudo tee /etc/apt/sources.list.d/example.list
```
3. Now you can install the package:
```sh
sudo apt update
sudo apt install hello-world
```
4. You can run the program to test it:
```sh
$ hello-world
```
