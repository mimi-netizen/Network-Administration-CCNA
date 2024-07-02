# Basic Router/Switch Configuration & Verification Lab

Default Username and Password: `cisco`

---

1: Router Connection to Switch

Connect the Cisco Routers to the Cisco Switches

---

2: enable command

The `enable` command is used in the Cisco IOS (Internetwork Operating System) command-line interface (CLI) to enter privileged EXEC mode, also known as "enable mode" or "privilege level 15." When you first access a Cisco device through the console or a Telnet/SSH session, you typically start in user EXEC mode, indicated by the router prompt ending with a greater-than sign (`>`).

Here's an example of the user EXEC mode prompt:

```bash
Router>
```

To access privileged EXEC mode and gain elevated privileges for configuration and management, you use the `enable` command. Once you've entered this command, you may be prompted for a password, depending on the device's configuration.

```bash
Router> enable
Password:
```

After entering the correct password, the prompt changes to indicate that you are now in privileged EXEC mode. The prompt typically changes to reflect the device's hostname followed by the `#` symbol.

```bash
Router#
```

In privileged EXEC mode, you have access to more advanced commands, including those for configuration and monitoring. Be cautious when making configuration changes in this mode, as they can have a significant impact on the device's operation.

It's important to note that the `enable` command and privilege levels are part of the security features in Cisco IOS, allowing administrators to control access to different levels of commands based on user credentials and roles. Additionally, the `disable` command is used to exit privileged EXEC mode and return to user EXEC mode.

---

3: reload command

The `reload` command in Cisco IOS is used to reboot or restart a Cisco device, such as a router or switch. This command is typically executed from privileged EXEC mode (`Router#` prompt). When you issue the `reload` command, the device will go through the process of restarting, reloading the operating system and configuration. This can be useful in various scenarios, such as applying configuration changes that require a reboot or resolving certain issues.

Here's an example of how to use the `reload` command:

```bash
Router# reload
```

After entering the command, the device may prompt you to confirm the reload and ask whether you want to save the configuration before reloading. If you have made configuration changes that you want to save, it's advisable to answer "yes" to save the configuration before the reload.

Keep in mind that issuing a `reload` command will temporarily disconnect network services provided by the device, so it's generally recommended to perform this operation during a maintenance window or a time when network disruption is acceptable.

Additionally, you can include various options with the `reload` command to specify parameters like the time delay before reloading or to cancel a scheduled reload. For example:

```bash
Router# reload in 10
```

This command schedules a reload in 10 minutes.

```bash
Router# reload cancel
```

This command cancels a previously scheduled reload.

Always exercise caution when using the `reload` command, especially on production devices, and ensure that you have a backup of the device's configuration. Regularly saving configurations and understanding the potential impact of a device reload are essential practices in network administration.

---

4: show running-config command

The `show run` command in Cisco IOS is a widely used command that allows users to view the current running configuration of a Cisco device. This command is typically entered in privileged EXEC mode (`Router#` prompt). The `show run` command displays the active configuration of the device, including all the configured settings, parameters, and current status.

Here's an example of how to use the `show run` command:

```bash
Router# show run
```

After entering this command, the router or switch will display its running configuration, which is the configuration currently in use. The output will include information about interfaces, routing settings, security policies, and other configuration parameters.

The running configuration is the configuration that is currently active in the device's memory. It may include changes that have been made but not yet saved to the startup configuration (the configuration that is loaded when the device starts up). If you make changes to the configuration and want to save them, you can use the `write memory` or `copy running-config startup-config` command.

Additionally, you can use specific keywords with the `show run` command to display only parts of the configuration. For example:

- `show run interface <interface>`: Displays the configuration for a specific interface.
- `show run | section <keyword>`: Displays only the sections of the configuration that contain the specified keyword.
- `show run | include <keyword>`: Displays lines that include the specified keyword.

The `show run` command is a powerful tool for network administrators to quickly assess the current state of a device's configuration and troubleshoot any issues. It's commonly used in combination with other show commands to gather information about different aspects of the device's operation.

---

5: show startup-config command

The `show startup-config` command in Cisco IOS is used to display the contents of the startup configuration file stored in the device's non-volatile memory (NVRAM). This command allows you to view the configuration that will be loaded and applied when the device is restarted or powered on.

Here's an example of how to use the `show startup-config` command:

```bash
Router# show startup-config
```

The output will display the configuration settings stored in NVRAM, including interface configurations, routing settings, security policies, and other parameters. The startup configuration represents the configuration that was saved to NVRAM using the `write memory` or `copy running-config startup-config` command.

Comparing the output of `show startup-config` with `show running-config` is useful to see if there are any unsaved changes in the running configuration that have not been written to the startup configuration. If you make changes to the running configuration and want to save them, you should use the `write memory` or `copy running-config startup-config` command.

Here's an example of how you might use these commands together:

```bash
Router# show running-config
... (display of running configuration)
Router# copy running-config startup-config
Destination filename [startup-config]?
Building configuration...
[OK]
Router# show startup-config
... (display of startup configuration, now reflecting the changes)
```

This sequence of commands ensures that any changes made to the running configuration are saved to the startup configuration, making them persistent across reboots.

Understanding the startup configuration is crucial for managing and maintaining Cisco devices, as it determines the initial configuration state of the device when it boots up.

---

6: dir command

The `dir` command in Cisco IOS is used to display the contents of a filesystem or directory on a Cisco router or switch. This command is typically used to view the files stored in flash memory or other storage devices on the device.

Here's an example of how to use the `dir` command:

```bash
Router# dir
```

The output will list the files and directories in the current working directory. In many cases, the default location is the device's flash memory.

Here's a brief explanation of some options and variations of the `dir` command:

1. **Display Files in a Specific Directory:**

   ```bash
   Router# dir flash:
   ```

   This command displays the files and directories in the flash memory. You can replace "flash:" with other filesystems or directories as needed.

2. **Display Detailed Information:**

   ```bash
   Router# dir /all
   ```

   The `/all` option provides more detailed information about the files, including size, date, and permissions.

3. **Display Information for a Specific File:**

   ```bash
   Router# dir flash:filename.txt
   ```

   This command displays information about a specific file, including its size, date, and permissions.

4. **Display Files in a Directory with a Specific Extension:**
   ```bash
   Router# dir flash:*.bin
   ```
   This command lists all files in the flash directory with a ".bin" extension.

The `dir` command is useful for checking the contents of storage devices, such as flash memory or USB drives, and for verifying the presence of specific files needed for operations, like software images or configuration files. Keep in mind that the available options may vary depending on the specific platform and IOS version.

---

7: config terminal command

The `config terminal` command in Cisco IOS is used to enter global configuration mode from privileged EXEC mode (`Router#` prompt). Once you are in global configuration mode, you can configure various parameters and settings on the Cisco device.

Here's an example of how to use the `config terminal` command:

```bash
Router# config terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#
```

After entering `config terminal`, the prompt changes to indicate that you are now in global configuration mode (`Router(config)#`). From this mode, you can configure a wide range of settings, including interface configurations, routing protocols, access control lists (ACLs), and more.

It's worth noting that the `config terminal` command is synonymous with its shorter form, `conf t`. You can use either `config terminal` or `conf t` to enter global configuration mode.

```bash
Router# conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#
```

Both commands serve the same purpose of entering global configuration mode, and network administrators often use the shorter `conf t` for brevity.

---

8: show interface command

The `show interface` command in Cisco IOS is used to display detailed information about the status and configuration of network interfaces on a Cisco router or switch. This command provides a comprehensive view of the operational characteristics of each interface, including Ethernet, Serial, GigabitEthernet, and other types of interfaces.

Here's an example of how to use the `show interface` command:

```bash
Router# show interface GigabitEthernet0/0
```

This command displays information specific to the GigabitEthernet0/0 interface. The output includes details such as:

- Interface status (up or down)
- Hardware and MAC address
- IP address and subnet mask
- MTU (Maximum Transmission Unit)
- Traffic statistics (input and output rates, errors, collisions, etc.)
- Interface configuration settings (if any)

Here are a few variations of the `show interface` command:

1. **Show All Interfaces:**

   ```bash
   Router# show interface
   ```

   This command displays information for all interfaces configured on the device.

2. **Show Brief Interface Status:**

   ```bash
   Router# show ip interface brief
   ```

   This command provides a brief overview of the IP configuration and status of all interfaces.

3. **Show Status of Specific Interface Type:**

   ```bash
   Router# show interface status
   ```

   This command shows the status (up or down) of all interfaces on the device.

4. **Show Interface Counters:**
   ```bash
   Router# show interfaces counters
   ```
   This command displays detailed interface counters, including packet counts, error counts, and other statistics.

The `show interface` command is a powerful troubleshooting tool, allowing network administrators to quickly assess the health and performance of network interfaces. By analyzing the information provided, administrators can identify issues, monitor traffic patterns, and make informed decisions about network management and optimization.

---

9: show version command

The `show version` command in Cisco IOS is used to display detailed information about the hardware and software configuration of a Cisco device, such as a router or a switch. This command provides a summary of the device's current operating state, including the hardware platform, software version, system uptime, and configuration register settings.

Here's an example of how to use the `show version` command:

```bash
Router# show version
```

The output of the `show version` command typically includes information such as:

- **System image file:** The filename of the IOS (Internetwork Operating System) software running on the device.
- **Cisco IOS Software version:** The version number of the installed software.
- **Router model and processor type:** Information about the hardware platform, including the model and type of processor.
- **Configuration register value:** The configuration register setting, which determines how the router boots and loads its software.
- **System uptime:** The amount of time the device has been running since the last reboot.
- **Flash memory and RAM size:** Information about the amount of flash memory and RAM installed on the device.

Here's a simplified example of what the output might look like:

```bash
Router# show version
Cisco IOS Software, 2800 Software (C2800NM-ADVIPSERVICESK9-M), Version 15.1(4)M8
...
Cisco 2811 (revision 1.0) with 251904K/10240K bytes of memory.
...
System image file is "flash:c2800nm-advipservicesk9-mz.151-4.M8.bin"
...
Router uptime is 1 week, 3 days, 4 hours, 30 minutes
...
```

The `show version` command is often used to gather essential information about a Cisco device, particularly during initial setup, troubleshooting, or when assessing the need for software upgrades. It provides a quick overview of the device's capabilities, software features, and current operating status.

---

10: no service password-encryption command

The `no service password-encryption` command in Cisco IOS is used to disable the encryption of passwords stored in the device's configuration file. By default, Cisco routers and switches encrypt certain passwords in the configuration file to enhance security. The `service password-encryption` command is used to enable password encryption, and conversely, the `no service password-encryption` command is used to disable it.

Here's an example of how to use the `no service password-encryption` command:

```bash
Router(config)# no service password-encryption
```

After entering this command in global configuration mode, the passwords in the configuration file will be stored in plaintext instead of being encrypted. This might be necessary in scenarios where you need to view or copy the configuration and want passwords to be displayed in their plain form.

It's important to note a few considerations:

1. **Security Implications:** Encrypting passwords in the configuration file adds a layer of security by protecting sensitive information. Disabling password encryption makes it easier for someone with access to the configuration file to see the passwords in clear text.

2. **Visibility of Passwords:** Without password encryption, passwords, such as the enable secret or line passwords, will be visible in the configuration file. This can be a security risk, especially if unauthorized individuals gain access to the configuration.

3. **Impact on Existing Configurations:** Disabling password encryption does not affect existing passwords; it only changes how new passwords are stored in the configuration. If you disable encryption, it's a good practice to change existing passwords to avoid exposing them in plaintext.

4. **Consideration for Security Best Practices:** While disabling password encryption may be necessary in specific situations, it is generally recommended to keep password encryption enabled as a security best practice.

Before making changes to password encryption settings, carefully assess the security requirements of your network environment and consider the potential risks associated with storing passwords in plaintext within the configuration file.

---

11: copy running-config startup-config command

The `copy running-config startup-config` command in Cisco IOS is used to save the currently running configuration to the startup configuration file in non-volatile memory (NVRAM). This command ensures that any changes made to the running configuration are saved and will persist across reboots or power cycles.

Here's an example of how to use the `copy running-config startup-config` command:

```bash
Router# copy running-config startup-config
```

Alternatively, a shorter form of the command is often used, which is:

```bash
Router# write memory
```

Both commands perform the same function—saving the running configuration to the startup configuration.

Explanation:

- `running-config`: Represents the current configuration that is actively running on the device.

- `startup-config`: Represents the configuration that will be loaded and applied when the device starts up or is rebooted. This configuration is stored in non-volatile memory (NVRAM) and is retained even if the device loses power.

By using the `copy running-config startup-config` or `write memory` command, you ensure that any changes made to the configuration during the current session are permanently saved, preventing the loss of configuration changes after a reboot.

It's worth noting that the command `write memory` is considered a legacy command, and while it is still widely used, the preferred and more descriptive command is `copy running-config startup-config`. Both commands accomplish the same task of saving the running configuration to the startup configuration.

---

12: do show run command

The `do show run` command in Cisco IOS is used to display the running configuration of a device without leaving the configuration mode. The `do` keyword allows you to run EXEC-level commands from within configuration mode.

Here's an example of how to use the `do show run` command:

```bash
Router(config)# do show run
```

This command is particularly useful when you are in global configuration mode or any other configuration submode and want to quickly view the running configuration without exiting the current mode.

Explanation:

- `do`: The `do` keyword allows you to run EXEC-level commands from within configuration mode.

- `show run`: This is the EXEC-level command used to display the running configuration. It shows the active configuration settings of the device.

By using `do show run`, you can view the running configuration without having to exit the current configuration mode. It's a convenient way to check the impact of your configuration changes or to verify the current configuration without leaving the configuration session.

---

13: copy run flash: command

The `copy running-config flash:` command in Cisco IOS is used to save the current running configuration to a file in the flash memory of the device. This command is useful for creating a backup of the running configuration on the device's flash storage, allowing you to store different configuration versions or to save the configuration before making significant changes.

Here's an example of how to use the `copy running-config flash:` command:

```bash
Router# copy running-config flash:backup-config.txt
```

In this example, the running configuration is copied to a file named "backup-config.txt" in the flash memory. You can specify a different filename if desired.

Explanation:

- `running-config`: Represents the current configuration that is actively running on the device.

- `flash:`: Specifies the destination as the flash memory.

- `backup-config.txt`: Specifies the filename to save the running configuration in the flash memory.

After executing this command, the running configuration is saved to the specified file in the flash memory. This file can be later retrieved, copied to another device, or used to restore the configuration on the same device if needed.

It's important to note that the flash memory is a type of non-volatile storage on Cisco devices and is often used to store the device's operating system (IOS image) and other files. Saving the running configuration to the flash memory can be a good practice for backup purposes, but it's recommended to use meaningful filenames to easily identify and manage different configuration versions.

---

14: cisco console configuration

These commands are typically used in the configuration of the console line on a Cisco device. Let's break down each command:

1. **`line console 0`**: This command is used to enter the configuration mode for the console line. It specifies that the configuration commands that follow are meant for the console interface (often used for connecting to the device via a physical console port).

   ```bash
   Router(config)# line console 0
   Router(config-line)#
   ```

   After entering this command, you are in the configuration mode for the console line (`Router(config-line)#`).

2. **`exec-timeout 30 0`**: This command sets the timeout for the console session. In this case, it sets an idle timeout of 30 minutes and a absolute timeout of 0 minutes (no absolute timeout). If there is no activity within the console session for 30 minutes, the session will automatically log out.

   ```bash
   Router(config-line)# exec-timeout 30 0
   ```

3. **`password cisco`**: This command sets the password required for accessing the console line. In this example, the password is set to "cisco." This means that anyone attempting to access the console line will be prompted for this password.

   ```bash
   Router(config-line)# password cisco
   ```

4. **`login`**: This command enables password authentication for the console line. It ensures that users trying to access the console line are prompted for a password.

   ```bash
   Router(config-line)# login
   ```

After configuring these commands, the console line is secured with a password ("cisco" in this case), and users attempting to access the console line will be prompted for a password. Additionally, the console session has an idle timeout of 30 minutes, after which the session will automatically log out if there is no activity.

Keep in mind that using simple and easily guessable passwords like "cisco" is not a good security practice. In a production environment, you should use strong, secure passwords to enhance the security of your network devices.

---

15: enable secret cisco command

The `enable secret` command in Cisco IOS is used to set a password that controls access to privileged EXEC mode. Privileged EXEC mode, often represented by the `Router#` prompt, provides access to higher-level configuration commands and more advanced capabilities than user EXEC mode.

Here's an example of how to use the `enable secret` command:

```bash
Router(config)# enable secret cisco
```

In this example, the password for accessing privileged EXEC mode is set to "cisco." This password is hashed and stored securely in the device's configuration.

Key points:

1. **Hashed Password:** The password configured using `enable secret` is hashed using a one-way cryptographic algorithm (MD5 by default). This means that the actual password is not stored in the configuration; instead, a hash of the password is stored. This enhances security compared to the older `enable password` command, which stored passwords in a less secure manner.

2. **Security Best Practice:** It is recommended to use the `enable secret` command instead of the older `enable password` command for enhanced security. The use of strong and complex passwords is crucial for securing network devices.

3. **Password Recovery:** If you forget the `enable secret` password and need to recover access to the device, the process usually involves physical access to the device and is more involved than recovering a lost user password. This is intentional to enhance security.

4. **Verification:**

   ```bash
   Router# show running-config
   ...
   enable secret 5 $1$IM9B$U6rj6I3XAFouDdQQyXcxS.
   ...
   ```

   The hashed `enable secret` password is displayed in the running configuration. The actual hash will differ based on the specific password configured.

It's important to choose a strong and secure password for the `enable secret` to prevent unauthorized access to privileged EXEC mode. Additionally, consider using additional security measures, such as AAA (Authentication, Authorization, and Accounting) and role-based access control, to enhance the overall security of your network devices.

---

16: show flash command

The `show flash` command in Cisco IOS is used to display information about the flash memory on a Cisco device. Flash memory is a type of non-volatile storage used to store the device's operating system (IOS image) and other files. The `show flash` command provides details about the files in the flash memory and their sizes.

Here's an example of how to use the `show flash` command:

```bash
Router# show flash
```

The output of this command typically includes information such as:

- **Filesystem information:** This section shows the amount of free and used space in the flash memory.
- **Files in the flash:** This section lists the files stored in the flash memory, including the IOS image file and any other files.

Here's a simplified example of what the output might look like:

```bash
Router# show flash
System flash directory:
File  Length   Name/status
  1   12345678  c2800nm-advipservicesk9-mz.151-4.M8.bin
  2   9876543   backup-config.txt
...
```

In this example, the flash memory contains an IOS image file named "c2800nm-advipservicesk9-mz.151-4.M8.bin" and another file named "backup-config.txt."

Some variations of the `show flash` command include:

- **`show flash:`:** Allows you to view the contents of a specific directory within the flash memory.

  ```bash
  Router# show flash:
  ```

- **`show flash:filename`:** Displays detailed information about a specific file in the flash memory.
  ```bash
  Router# show flash:c2800nm-advipservicesk9-mz.151-4.M8.bin
  ```

The `show flash` command is commonly used to verify the presence of the correct IOS image, check available space, and identify other files stored in the flash memory. It's an essential command for managing and maintaining Cisco devices.

---

17: hostname command

The `hostname` command in Cisco IOS is used to set the hostname of a Cisco device. The hostname is a user-friendly label assigned to the device, and it is often used to identify the device in the network. Changing the hostname is a basic configuration task that allows you to customize the prompt that appears in the command-line interface (CLI) and helps distinguish one device from another.

Here's an example of how to use the `hostname` command:

```bash
Router> enable
Router# configure terminal
Router(config)# hostname MyRouter
MyRouter(config)#
```

In this example:

- `enable`: Enters privileged EXEC mode.
- `configure terminal`: Enters global configuration mode.
- `hostname MyRouter`: Sets the hostname to "MyRouter." The prompt changes accordingly.

After setting the hostname, the command-line prompt reflects the new hostname, making it easier for administrators to identify the device. For example:

```bash
MyRouter(config)#
```

It's important to note that changing the hostname does not impact the device's functionality or its operation in the network. The primary purpose is to provide a recognizable and meaningful label for the device.

Additionally, when configuring a hostname, you should follow certain guidelines:

1. The hostname should be alphanumeric and can include hyphens, but it cannot start or end with a hyphen.
2. The hostname is case-insensitive.
3. Some special characters are not allowed in the hostname.

Here's an example of how to verify the configured hostname:

```bash
MyRouter# show running-config | include hostname
hostname MyRouter
```

This command displays the current hostname configuration in the running configuration.
