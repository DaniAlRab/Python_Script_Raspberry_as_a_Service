Using systemd on Raspberry Pi
Create a systemd service file:
Create a service file for your Python script. For example, create a file named my_script.service in /etc/systemd/system/:

sh
Copy code
sudo nano /etc/systemd/system/my_script.service
Add the following content to the service file:

ini

[Unit]
Description=My Python Script
After=network.target

[Service]
ExecStart=/usr/bin/python3 /path/to/your_script.py
Restart=always
User=pi

[Install]
WantedBy=multi-user.target
Replace /path/to/your_script.py with the full path to your Python script.

Reload the systemd manager configuration:

sh
Copy code
sudo systemctl daemon-reload
Enable the service to start on boot:

sh
Copy code
sudo systemctl enable my_script.service
Start the service:

sh
Copy code
sudo systemctl start my_script.service
Verifying the service status
You can check the status of your service with the following command:

sh
Copy code
sudo systemctl status my_script.service
This method ensures your Python script will start automatically when the Raspberry Pi boots up and provides robust management options, such as automatic restarts if the script fails.
