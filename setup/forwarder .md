📡 Splunk Universal Forwarder Setup (macOS ➜ Ubuntu VM)
🧾 Overview
This guide details how to set up a Splunk Universal Forwarder on a macOS host device to send logs to a Splunk Enterprise instance running on an Ubuntu VM.

🧱 Architecture
[macOS Host (Forwarder)] ──────► [Ubuntu VM (Splunk Enterprise)]
              Port: 9997 (default)

🖥️ Step 1: Download Splunk Universal Forwarder for macOS
Go to Splunk Downloads - Forwarder.
Select macOS (Intel) and download the .pkg installer.
Install the package on your Mac.

🔐 Step 2: Configure the Forwarder
Open Terminal on your Mac and run:

```bash
sudo /Applications/SplunkForwarder/bin/splunk start --accept-license
```
Then, enable boot-start:
```bash
sudo /Applications/SplunkForwarder/bin/splunk enable boot-start
```

🌐 Step 3: Add Receiver (Ubuntu VM)
Set your Splunk Enterprise IP address and port 9997 (or other if configured):

```bash
sudo /Applications/SplunkForwarder/bin/splunk add forward-server <UBUNTU_VM_IP>:9997
```
✅ Example:

```bash
sudo /Applications/SplunkForwarder/bin/splunk add forward-server 192.168.1.110:9997
```

📂 Step 4: Specify Log Files to Monitor
Example: To monitor macOS system logs:

```bash
sudo /Applications/SplunkForwarder/bin/splunk add monitor /var/log
```
You can also add custom paths like:

```bash
sudo /Applications/SplunkForwarder/bin/splunk add monitor /Users/your-username/Documents/logs
```

🟢 Step 5: Confirm the Forwarder is Running
```bash
sudo /Applications/SplunkForwarder/bin/splunk status
```

📊 Step 6: Verify on Splunk Enterprise
Open the Splunk Dashboard on your Ubuntu VM.

Go to:
Settings → Forwarding and receiving → Forwarder management
Confirm MacBookPro.lan appears in the list.

Go to the Search & Reporting app and run:

"index= host="MacBookPro.lan""
✅ If logs show up, the forwarder is successfully connected.

🧰 Optional: Restart Forwarder Service
```bash
sudo /Applications/SplunkForwarder/bin/splunk restart
```
📁 Example File Paths
Type	Path
Forwarder Binary	/Applications/SplunkForwarder/bin/splunk
macOS System Logs	/var/log/

📝 Notes
Ensure port 9997 is open between the host and VM.

For custom inputs or SSL configuration, edit:
/Applications/SplunkForwarder/etc/system/local/inputs.conf
