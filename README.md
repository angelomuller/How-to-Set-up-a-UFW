# Setting-up-a-UFW-

Uncomplicated Firewall as the name suggests, its a tool for Linux environments that simplifies the process of setting up firewall rules and help protect the network security in a few simple steps.
The main feature of UFW is the capacity of allowing or denying incoming and outgoing traffic on the network, and that's what we'll demonstrate in this project. It's important to note that all tools presented here have more than one utility and just a sample of it's range will be explored in this presentation.

# Preparing the environment

First we need to download all required tools on Kali, which is the Linux version we'll be using in order to perform the UFW trial.
- Install Apache2: _The most widely used web server for Linux._
- Install OpenSSH Server: _SSH is a powerfull tool with many useful features, but in this case will be used to encrypt the communication between machines._
- Finally, install and run UFW.
- Have a separate ready for testing, with _Bridge adapter_ set  (I'm running a Windows 10 VM).

![Screenshot_1](https://github.com/user-attachments/assets/0b0eacd5-8f51-4c6b-b83d-e1a271de2c85)

![Screenshot_2](https://github.com/user-attachments/assets/8f0e534c-d318-4268-bcd9-3688470af8b6)

![Screenshot_3](https://github.com/user-attachments/assets/e9c24576-9fc5-4dd1-b679-cd8304c35685)

![Screenshot_4](https://github.com/user-attachments/assets/001fea7e-47dc-48f5-b140-4b35cb8fd42e)

# Starting the tests

First, make sure both machines are visible by pinging each other.

![Screenshot_5](https://github.com/user-attachments/assets/5fa11e77-e217-4eee-943d-74f0c39a27a7)

![Screenshot_6](https://github.com/user-attachments/assets/40004935-1acf-4932-93a1-2f75da05ff20)

Now we'll be _allowing outgoing_ traffic in the network and _denying any incoming traffic_ on the UFW so we can start configuring the rules.

![Screenshot_7](https://github.com/user-attachments/assets/2809a182-af85-4f77-913b-9bdfe2551487)
![Screenshot_8](https://github.com/user-attachments/assets/45e01145-6d02-4e83-ab09-eae72760bd1f)

Note that simply forgetting to run the command as root (cmd sudo) will prevent it from enabling the function properly.

![Screenshot_9](https://github.com/user-attachments/assets/a30e30d7-e7a1-485f-9424-6bc50bad94bb)

After denying incoming traffic, we'll block ICMP (Internet Control Message Protocol) requests.
ICMP have many functions, such as diagnostic purposes, checking if a host is reacheable - like we justs did via pinging - and traceroute, to track packets traffic.
In order to perform this change in the rules, it's vital to have a backup of the files.

![Screenshot_10](https://github.com/user-attachments/assets/8ecc8de1-ee49-443c-98e3-930cd723ace7)

Open the file that you've just created by running the command _sudo nano /etc/ufw/before.rules_  and change the following rules:

![Screenshot_11](https://github.com/user-attachments/assets/785231b8-7705-47ba-b28a-fd10fa4cf88e)

![Screenshot_12](https://github.com/user-attachments/assets/a0448996-e2df-4027-a429-861987cd10cd)

Reload the UFW in order to update the rules.

![Screenshot_13](https://github.com/user-attachments/assets/c41a6d43-b9b3-41df-9ee6-043c7e49a38d)

As stated before, services like _ping_ and _traceroute_ use ICMP as backbone for troubleshooting network issues, so disabling ICMP will prevent both services from working. Try pinging the VM to verify that ICMP is being blocked.

![Screenshot_14](https://github.com/user-attachments/assets/c90030a0-2bba-4547-b78a-0ed0510b49ee)

If everything is going as the screenshots above, you're doing good! This part of the practice is done, so now you can copy the backup back to its original file and reload the firewall.

![Screenshot_15](https://github.com/user-attachments/assets/d4bf9dc8-1f2e-4b14-8262-790e22ed076b)

# Experimenting with Remote Desktop application and SSH Server

Using tools such as Remote Desktop and SSH Server to perform ICMP requests are effective practices to ensure your configurations are being deployed properly.
If you haven't installed yet, start by adding _OpenSSH Server_ under the tab _Apps > Optional features_ in your Windows machine.

![Screenshot_16](https://github.com/user-attachments/assets/42f38504-85eb-4467-97f0-5e1a15b4dc71)

With SSH Server installed, you'll enable it and run via the tab _services_ > _OpenSSH Authentication Agent_ as shown below.

![Screenshot_17](https://github.com/user-attachments/assets/408225c3-5f36-4b16-aed1-476f2f08ebfc)

Now do the same on the _OpenSSH Server_ tab.

![Screenshot_18](https://github.com/user-attachments/assets/59878c7f-f608-42ff-a7c2-de3b1ffea06c)








