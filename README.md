# Cookbook for Ffuf on Kali Linux

![image](https://github.com/sushriyamogasala/Cookbook-for-Fuff-/assets/104165177/65befb47-b6b8-48a2-a702-c386e27faa76)

### Table of Contents
1. Introduction to Ffuf
2. Installation
3. Basic Usage
4. Advanced Usage
5. Real-World Scenarios
6. Tips and Best Practices
7. Troubleshooting
8. Resources

---

### 1. Introduction to Ffuf

Ffuf (FFUF) is a powerful and fast tool for discovering hidden parts of a website by automating the process of testing many different inputs against a web server and analyzing the responses. It is particularly useful for security testing and bug hunting.

#### Key Features
- **Purpose**: Discover hidden elements of a website that are not easily accessible or visible.
- **Fuzzing**: Automates sending numerous requests with different inputs to uncover hidden directories, files, or parameters.
- **Speed**: Designed to be fast and efficient, capable of handling large wordlists and high volumes of requests quickly.

### 2. Installation

#### Installing Ffuf on Kali Linux

1. **Update your system**:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. **Install Ffuf**:
   ```bash
   sudo apt-get install ffuf
   ```

3. **Verify installation**:
   ```bash
   ffuf -h
   ```
![image](https://github.com/sushriyamogasala/Cookbook-for-Fuff-/assets/104165177/4b5a5c64-7f02-412a-8f9b-0cf5cf14eda7)

- Use the command:ffuf -h.We can find the help page we can explore the tool with this command.

![image](https://github.com/sushriyamogasala/Cookbook-for-Fuff-/assets/104165177/b28b2a59-5926-4f66-8512-7220abfb69cc)


### 3. Basic Usage

#### Basic Directory Brute-Forcing

To brute-force directories on a web server:

```bash
ffuf -u http://example.com/FUZZ -w wordlist.txt
```
- `-u http://example.com/FUZZ`: The target URL with `FUZZ` as the placeholder.
- `-w wordlist.txt`: The wordlist file containing different names to test.

#### File Discovery with Specific Extensions

For file discovery, you can use the same command. To include specific file extensions from the wordlist, use the -e flag.

To discover files with specific extensions:

```bash
ffuf -w wordlist.txt -u http://website.com/FUZZ -e .aspx,.html,.php,.txt
```
Example for a maximum fuzzing time of 60 seconds:

Command : ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u https://geeksforgeeks.org/FUZZ -maxtime 60

![image](https://github.com/sushriyamogasala/Cookbook-for-Fuff-/assets/104165177/ca1db429-cd03-4960-b6c0-b39553fd9b8e)

### 4. Advanced Usage

#### Filtering Responses

Ffuf offers options to filter responses by status codes, line counts, response sizes, word counts, and regex patterns:

- **Status Code**: `-mc`
- **Number of Lines**: `-ml`
- **Regex Pattern**: `-mr`
- **Response Size**: `-ms`
- **Number of Words**: `-mw`

Example to get responses with status codes 200 and 302:

```bash
ffuf -w wordlist.txt -u http://website.com/FUZZ -e .aspx,.html -mc 200,302
```

#### Recursion

URL parameters ending with `FUZZ` support recursion. Use the `-recursion` flag to enable this feature:

- **Recursion Depth**: `-recursion-depth`
- **Maximum Time**: `-maxtime`
- **Maximum Time per Job**: `-maxtime-job`

Example with a maximum fuzzing time of 60 seconds:

```bash
ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u https://geeksforgeeks.org/FUZZ -maxtime 60
```

### 5. Real-World Scenarios

#### Discovering Hidden Endpoints

```bash
ffuf -u http://example.com/FUZZ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -mc 200
```

#### Subdomain Enumeration

```bash
ffuf -u http://FUZZ.example.com -w /usr/share/wordlists/subdomains.txt -mc 200,301,302
```

### 6. Tips and Best Practices

- **Use relevant wordlists**: Choose wordlists that suit the target's context (e.g., directory names, parameters).
- **Filter responses**: Use `-mc` and `-fc` to match or filter specific HTTP status codes.
- **Adjust request rate**: Use `-rate` to control the number of requests per second to avoid detection and IP bans.

### 7. Troubleshooting

- **Installation issues**: Ensure Ffuf is installed correctly.
- **Connection errors**: Verify the target URL and network connection.
- **Permissions**: Run commands with `sudo` if you encounter permission issues.

### 8. Resources

- [Ffuf GitHub Repository](https://github.com/ffuf/ffuf)
- [Kali Linux Documentation](https://www.kali.org/docs/)
- [OWASP Wordlists](https://owasp.org/www-project-seclists/)

---

This cookbook provides a comprehensive guide to using Ffuf on Kali Linux. Whether you're a beginner or an advanced user, this guide will help you utilize Ffuf's powerful capabilities effectively.
