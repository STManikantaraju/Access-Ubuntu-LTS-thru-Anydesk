# Access-Ubuntu-LTS-thru-Anydesk

<img width="1919" height="1030" alt="image" src="https://github.com/user-attachments/assets/0d61d535-0acc-4aea-a844-e47fd2f4d576" />

The error display_server_not_supported happens because the remote Ubuntu machine is using **Wayland**, which AnyDesk does not fully support for remote control.


To fix this, you need to switch Ubuntu's display server back to **Xorg (X11)**. Since you cannot connect via AnyDesk right now, you must run these commands directly on the remote machine's physical terminal (or via an SSH connection).


**The Fix: Switch Wayland to Xorg**

You will need an admin account to make this change. Run the following commands:

**1.	Open the login configuration file:**

sudo nano /etc/gdm3/custom.conf

(If you use a different desktop environment like Kubuntu, replace gdm3 with sddm).

**2.	Enable Xorg:**

Scroll down using your arrow keys and find this line:
#WaylandEnable=false

**3.	Uncomment the line:**

Delete the # symbol so it looks exactly like this:

WaylandEnable=false

**4.	Save and Exit:**

o	Press Ctrl + O then Enter to save.

o	Press Ctrl + X to exit the nano editor.

**5.	Restart the display manager to apply changes:**

sudo systemctl restart gdm3

(Note: This will temporarily kick any active users out to the login screen).
________________________________________

Once restarted, you should be able to connect via AnyDesk without issues. If you want to make sure it goes smoothly, let me know:

•	Are you able to access the **physical machine** or connect to it via SSH to run these commands?

•	Which **Ubuntu version** is the remote machine running?

I can give you alternative steps if you are locked out of the machine completely.

