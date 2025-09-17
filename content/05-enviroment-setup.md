# Enviroment Setup

## Assumptions
- All passwords were sourced from Kali Linux's `rockyou.txt` wordlist, accessed via the `wordlists` command.
- In real-world scenarios, attackers rarely have a guaranteed password list, but for testing purposes, a known list ensures tool functionality.
- To maintain focus on tool usage rather than password list generation, `rockyou.txt` was used instead of creating custom lists tailored to user profiles.
- It is assumed that the attacker knows the usernames, which is plausible within the context of this exercise.
- The attacker discovered the server's IP address by resolving the domain name, which was publicly shared in a social media post.

## Technical Details

- Due to the strict requirement that this assignment must not be internet-facing and must remain within a virtual environment, I chose not to fully implement the network setup shown in Figure 1. Instead, I placed both the attacker and defender machines on the same virtual network, as emulating the full network would have been unnecessary for the scope of this exercise.
- The command that I used to select the tools `shuf -n 4 rockyou.txt > user_passwords.txt` for user profiles on the server, and `shuf -n 4 rockyou.txt > db_passwords.txt`(This created a total of 8 potential password combinations). 

```{=latex}
\input{content/tables/password-table.tex}
```

![Visual representation of scenario](images/virtualnetwork.png)

### Attacker Machine

The attacker machine was chosen for its comprehensive suite of pre-installed security tools, which suited the requirements of this assignment. The only additional configuration involved updating all tools to their latest versions and manually assigning an IP address, as there was no DHCP server available within the virtual network. This setup provided a reliable and ready-to-use environment for conducting the required tests.

```{=latex}
\input{content/tables/attacker-stats.tex}
```

### Defender Machine

I selected Arch Linux for the defender machine because it is the Linux distribution I am most familiar with. Its lightweight nature allowed me to efficiently run the assignment on my laptop, and my experience with its package manager made installing and configuring the necessary tools straightforward. This familiarity ensured a smooth setup process and minimized time spent troubleshooting environment issues.


```{=latex}
\input{content/tables/defender-stats.tex}
```