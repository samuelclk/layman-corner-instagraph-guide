# Installing Open Interpreter

### Installing dependencies

```sh
sudo apt update -y && sudo apt upgrade -y
sudo apt install python3-pip
```

Open up the shell configuration file with

```sh
sudo nano ~/.bashrc
```

and add the following line at the end of the file, on a new line.

```
export PATH="$PATH:$HOME/.local/bin"
```

Then, update your shell configuration file by running:

```sh
source ~/.bashrc 
```

### Installing Open Interpreter

Installing and firing up Open Interpreter is so easy it should be a crime.

**Step 1:** On the terminal of your cloud VM, run

```sh
pip install open-interpreter
```

**Step 2:** To start Open Interpreter, run

```sh
interpreter -y
```

or if you want to review each step before it executes the command, run

```
interpreter
```

**Step 3:** Enter your OpenAI API key when prompted

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

That's it - super easy, barely an inconvenience.
