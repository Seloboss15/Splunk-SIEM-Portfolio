✅ Step-by-Step: Install Splunk on Ubuntu (Free Version for Dev Use)
🧩 1. Download Splunk .deb package
Go to Splunk Downloads and copy the link to the .deb package (you’ll need to register/login).

Or use the latest public free trial version via terminal:

bash
wget -O splunk-latest.deb 'https://download.splunk.com/products/splunk/releases/9.1.1/linux/splunk-9.1.1-64e843ea36b1-linux-2.6-amd64.deb'

📦 2. Install the downloaded .deb file:
bash
sudo dpkg -i splunk-latest.deb

⚙️ 3. Start and accept license:
bash
sudo /opt/splunk/bin/splunk start --accept-license

Set admin username and password during setup.
🔐 4. Enable Splunk to Start at Boot (Optional):
bash
sudo /opt/splunk/bin/splunk enable boot-start

🌐 5. Access Splunk Dashboard
Open your browser and go to:
http://localhost:8000
Log in with the admin credentials you set.


