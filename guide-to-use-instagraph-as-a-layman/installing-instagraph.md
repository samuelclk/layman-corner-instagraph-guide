# Installing Instagraph

### Installing dependencies

Now that you are in your Google Cloud VM, run the following to install dependencies for Instagraph - i.e. Python, pip, virtualenv

```sh
sudo apt update -y && sudo apt upgrade -y
sudo apt install python3-pip
pip install virtualenv
```

Select `"Ok"/"Yes"` in general while going through any prompts that may appear on your terminal. Use your `Arrows` and `TAB` keys to navigate the terminal UI.

### Create a Python virtual environment

1\) Open your shell configuration file using:

```sh
sudo nano ~/.bashrc
```

2\) Paste the following line at the end of the file, on a new line.

```sh
export PATH="$HOME/.local/bin:$PATH"
```

Save and exit with `CTRL+O, ENTER, CTRL+X`.&#x20;

3\) Update the new shell settings.

```sh
source ~/.bashrc
```

4\) Create the virtual environment.

```sh
virtualenv venv
```

5\) Activate the virtual environment

```sh
source venv/bin/activate
```

### Installing & configuring Instagraph

1\) Clone the repository from [Yohei Nakajima](https://twitter.com/yoheinakajima)'s Github [profile](https://github.com/yoheinakajima/instagraph) by running:

```sh
git clone https://github.com/yoheinakajima/instagraph.git
```

2\) Go into the Instagraph directory you just downloaded and install the required Python packages

```sh
cd instagraph
pip install -r requirements.txt
```

3\) Because the latest version has some UI bugs, let's use an earlier version instead. Run:

```sh
git checkout 530d933
```

**Expected output:**

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

4\) Set up your OpenAI API key

```sh
mv .env.example .env
nano .env
```

Add your OpenAI API key to the .env file. Replace `<your-api-key>` with your actual OpenAI API key. Jump back to this previous section if you have not generated this key.

```
OPENAI_API_KEY=<your-api-key>
```

5\) Run the Flask app

```
python main.py
```

**Expected output:**

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>
