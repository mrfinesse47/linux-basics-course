To create a systemd service called `mercury.service` with the specified requirements, you can follow these steps:

1. Create a unit file for the `mercury.service` under `/etc/systemd/system/mercury.service`. You can use a text editor like `nano` or `vim` to create the file. Here's how you can do it using `nano`:

```bash
sudo nano /etc/systemd/system/mercury.service
```

2. Add the following content to the `mercury.service` unit file:

```ini
[Unit]
Description=Project Mercury Web Application
After=network.target

[Service]
User=mercury
WorkingDirectory=/opt/caleston-code/mercuryProject/
ExecStart=/usr/bin/python3 manage.py runserver 0.0.0.0:8000
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

This configuration specifies the service name, working directory, user to run as, the command to run, and restart behavior.

3. Save the file and exit the text editor.

4. Now, reload the systemd daemon to pick up the new unit file:

```bash
sudo systemctl daemon-reload
```

5. Enable the `mercury.service` to start at boot:

```bash
sudo systemctl enable mercury.service
```

6. Start the `mercury.service`:

```bash
sudo systemctl start mercury.service
```

You can check the status of the service to ensure it's running without errors:

```bash
sudo systemctl status mercury.service
```

This should create, enable, and start the `mercury.service` as requested, running it as the `mercury` user with the specified command.
