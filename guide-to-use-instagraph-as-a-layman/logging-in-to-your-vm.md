# Logging in to your VM

### Preparing your remote access credentials

On your laptop's "Search" bar, look for "Windows Power Shell" for Windows users and "Terminal" for Mac users.

Create a new SSH key pair to be used for logging in to your VM remotely. Run the following on your terminal.

```sh
ssh-keygen -t ecdsa -C <username>
```

**Where:** `<username>` refers to the first part of the email you used to sign up for your Google Cloud account - **e.g. everything before the `@` in "xxx@gmail.com"**&#x20;

Follow the instruction prompts on your terminal to create your SSH key pair. Enter a password to encrypt your SSH key if you want to.

**Expected output:**

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

Next, print out the public key of the SSH key pair you just created by running:

```sh
cat .ssh/id_ecdsa.pub
```

Copy the entire output string by highlighting the string text pressing `CTRL+SHIFT+C` on windows and `CMD+C` on Mac.

{% hint style="info" %}
When copying from or pasting to your terminal, you need to use CTRL+SHIFT instead of just CTRL if you are on Windows. Mac users can stick with just CMD
{% endhint %}

Go back to your Google Cloud Console and click on the name of your newly created instance.

&#x20;

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Click on "Edit" on the navigation bar at the top.

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

Scroll down to the "SSH keys" section, click on "Add item", and paste the public key of the SSH key pair you copied earlier here. Then save your settings.

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Next, note down the **"External IP address"** of your VM under the **"Network Interfaces"** section. Copy it onto your notepad.

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Scroll back up to the top and click on the dropdown beside the "SSH" button. Then select "Open in browser window" from the dropdown.

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Follow the prompts in the new browser and you will end up in a terminal of your VM on this browser.

**Expected result:**

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

On this in-browser terminal, run the following to open up the authorized SSH keys file.

```
nano .ssh/authorized_keys
```

Add your SSH public key from earlier here, then save the file by pressing `CTRL+O, ENTER, CTRL+X`.&#x20;

Now reload your VM's SSH service by running:

```sh
sudo systemctl reload ssh
```

You can now close the in-browser terminal.

### Accessing your VM from your laptop natively

Now, go back to your laptop's terminal and run the following to access your VM using SSH tunneling.

```sh
ssh -L 8080:127.0.0.1:8080 <username>@<external-ip-address> -i .ssh\id_ecdsa -v
```

**Where:** `<username>` refers to the first part of the email you used to sign up for your Google Cloud account - **e.g. everything before the `@` in "xxx@gmail.com" ;** `<external-ip-address>` is the **"External IP address"** of your VM under the **"Network Interfaces"** section.

**Expected output:**

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
