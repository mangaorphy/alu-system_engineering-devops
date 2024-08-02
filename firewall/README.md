# Block All Incoming Traffic Except Mandatory Ports

This solution demonstrates how to configure the Uncomplicated Firewall (ufw) on a web server (web-01) to block all incoming traffic, except for the following TCP ports:

- 22 (SSH)
- 443 (HTTPS SSL)
- 80 (HTTP)

## Requirements

1. The solution must be applied to the web-01 server (it can also be applied to lb-01 and web-02, but it won't be checked).
2. The ufw firewall must be configured to block all incoming traffic, except for the specified TCP ports.

## Solution

1. Install the ufw firewall:

   ```
   sudo apt-get update
   sudo apt-get install ufw
   ```

2. Configure the ufw firewall to block all incoming traffic, except for the specified TCP ports:

   ```
   sudo ufw default deny incoming
   sudo ufw allow 22/tcp
   sudo ufw allow 443/tcp
   sudo ufw allow 80/tcp
   sudo ufw enable
   ```

   Explanation:
   - `sudo ufw default deny incoming`: This sets the default rule to deny all incoming traffic.
   - `sudo ufw allow 22/tcp`: This allows incoming traffic on TCP port 22 (SSH).
   - `sudo ufw allow 443/tcp`: This allows incoming traffic on TCP port 443 (HTTPS SSL).
   - `sudo ufw allow 80/tcp`: This allows incoming traffic on TCP port 80 (HTTP).
   - `sudo ufw enable`: This enables the ufw firewall.

3. Verify the ufw firewall configuration:

   ```
   sudo ufw status
   ```

   The output should show that the firewall is active and the specified TCP ports are allowed, while all other incoming traffic is denied.

## Conclusion

By following the steps above, you can configure the ufw firewall on the web-01 server to block all incoming traffic, except for the specified TCP ports (22, 443, and 80). This helps to secure the server by only allowing the necessary traffic to the web application.
