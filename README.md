# FUTURE_CS_02
# Setting Up a Firewall with UFW

## Introduction to UFW (Uncomplicated Firewall)

UFW, or Uncomplicated Firewall, is a user-friendly command-line tool designed to simplify the management of firewall rules on Linux distributions, including Ubuntu, Debian, and Arch Linux. It serves as an accessible interface for configuring iptables, the underlying packet filtering framework.

## Installation of UFW

To install UFW, execute the following command in your terminal:

```bash
sudo apt-get install ufw
```

## Basic UFW Commands

### Enabling and Disabling the Firewall

- **Enable UFW:** Activates the firewall.
  ```bash
  sudo ufw enable
  ```

- **Disable UFW:** Deactivates the firewall.
  ```bash
  sudo ufw disable
  ```

### Checking the Status

- **Status:** Displays the current status of the firewall and lists active rules.
  ```bash
  sudo ufw status
  ```

- **Verbose Status:** Provides detailed information about the firewall status.
  ```bash
  sudo ufw status verbose
  ```

### Allowing and Denying Traffic

- **Allow a Port:** Permits traffic on a specific port.
  ```bash
  sudo ufw allow [port]
  ```
  *Example: Allow HTTP traffic on port 80*
  ```bash
  sudo ufw allow 80
  ```

- **Deny a Port:** Blocks traffic on a specific port.
  ```bash
  sudo ufw deny [port]
  ```
  *Example: Deny HTTP traffic on port 80*
  ```bash
  sudo ufw deny 80
  ```

### Allowing/Denying by IP Address

- **Allow by IP:** Allows traffic from a specified IP address.
  ```bash
  sudo ufw allow from [IP_address]
  ```
  *Example: Allow traffic from IP address `192.168.1.1`*
  ```bash
  sudo ufw allow from 192.168.1.1
  ```

- **Deny by IP:** Blocks traffic from a specified IP address.
  ```bash
  sudo ufw deny from [IP_address]
  ```
  *Example: Deny traffic from IP address `192.168.1.1`*
  ```bash
  sudo ufw deny from 192.168.1.1
  ```

### Default Policies

Set default policies for incoming and outgoing traffic:
```bash
sudo ufw default allow outgoing
sudo ufw default deny incoming
```

### Deleting Rules

- **Delete by Rule Number:** Removes a rule by specifying its number from the status list.
  ```bash
  sudo ufw delete [rule_number]
  ```

- **Delete by Specification:** Removes a rule by specifying the exact rule.
  ```bash
  sudo ufw delete allow [port]
  ```
  
## Advanced UFW Commands

### Allowing Specific Services

UFW supports predefined service names listed in `/etc/services`. For example:
```bash
sudo ufw allow ssh
sudo ufw allow http
```

### Allowing/Denying Ranges of IP Addresses

Allow or deny a range of IP addresses:
```bash
sudo ufw allow from [IP_range]
sudo ufw deny from [IP_range]
```
*Example: Allow all traffic from `192.168.0.0/24`*
```bash
sudo ufw allow from 192.168.0.0/24
```

### Rate Limiting

Implement rate limiting to protect against brute-force attacks:
```bash
sudo ufw limit ssh/tcp
```

## Logging

### Enable Logging

Activate logging to monitor firewall activity:
```bash
sudo ufw logging on
```

### Set Log Level

Adjust the verbosity of the logs:
```bash
sudo ufw logging low   # Low verbosity 
sudo ufw logging medium # Medium verbosity 
sudo ufw logging high   # High verbosity 
```

## Practical Examples

- **Allowing HTTP and HTTPS Traffic**
    ```bash
    sudo ufw allow http    # Port 80/tcp 
    sudo ufw allow https   # Port 443/tcp 
    ```

- **Allowing SSH Access Only from a Specific IP**
    ```bash
    sudo ufw allow from [specific_IP] to any port ssh 
    ```
    *Example: Allow SSH access only from `192.168.1.100`*
    ```bash
    sudo ufw allow from 192.168.1.100 to any port 22 
    ```

- **Denying All Incoming Traffic Except for SSH**
    ```bash
    sudo ufw default deny incoming 
    sudo ufw default allow outgoing 
    sudo ufw allow ssh 
    ```

- **Setting Up Rate Limiting for SSH**
    ```bash
    sudo ufw limit ssh/tcp 
    ```

## Conclusion

UFW provides an intuitive interface for managing firewall rules on Linux systems, significantly enhancing security by controlling network traffic. By utilizing the commands and examples outlined above, users can effectively configure and manage their firewall settings to meet their specific security needs.
