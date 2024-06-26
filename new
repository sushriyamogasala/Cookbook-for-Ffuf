## Cookbook for Fuff on Kali Linux

### Table of Contents
1. Introduction to Fuff
2. Installation
3. Basic Usage
4. Advanced Usage
5. Real-World Scenarios
6. Tips and Best Practices
7. Troubleshooting
8. Resources

---

### 1. Introduction to Fuff

Fuff is a versatile and fast web fuzzer written in Go, designed for brute-forcing directories, parameters, and more. It's an essential tool for penetration testers and security researchers due to its speed and wide range of applications.

### 2. Installation

#### Installing Fuff on Kali Linux

1. **Update your system**:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. **Install Go (if not already installed)**:
   ```bash
   sudo apt install golang -y
   ```

3. **Download and install Fuff**:
   ```bash
   go install github.com/ffuf/ffuf/v2@latest
   ```

4. **Verify installation**:
   ```bash
   ffuf -h
   ```

### 3. Basic Usage

#### Basic Directory Brute-Forcing

To brute-force directories on a web server:

```bash
ffuf -u http://target.com/FUZZ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```

- `-u`: Specifies the URL with the `FUZZ` keyword indicating where to inject the payload.
- `-w`: Specifies the wordlist to use.

#### Parameter Brute-Forcing

To brute-force parameters:

```bash
ffuf -u http://target.com/page?FUZZ=test -w /usr/share/wordlists/parameters.txt
```

### 4. Advanced Usage

#### Multiple Wordlists

You can use multiple wordlists for complex fuzzing tasks:

```bash
ffuf -u http://target.com/FUZZ/BUZZ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -w /usr/share/wordlists/dirbuster/files.txt
```

#### POST Data Fuzzing

For fuzzing POST data:

```bash
ffuf -u http://target.com/login -w /usr/share/wordlists/usernames.txt:USERNAME -w /usr/share/wordlists/passwords.txt:PASSWORD -X POST -d 'username=USERNAME&password=PASSWORD'
```

- `-X POST`: Specifies the HTTP method.
- `-d`: Specifies the POST data with placeholders.

### 5. Real-World Scenarios

#### Discovering Hidden Endpoints

```bash
ffuf -u http://target.com/FUZZ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -mc 200
```

- `-mc 200`: Match HTTP status code 200 to filter results.

#### Subdomain Enumeration

```bash
ffuf -u http://FUZZ.target.com -w /usr/share/wordlists/subdomains.txt -mc 200,301,302
```

- Enumerate subdomains and filter based on status codes.

### 6. Tips and Best Practices

- **Use relevant wordlists**: Choose wordlists that suit the target's context (e.g., directory names, parameters).
- **Filter responses**: Use `-mc` and `-fc` to match or filter specific HTTP status codes.
- **Adjust request rate**: Use `-rate` to control the number of requests per second to avoid detection and IP bans.

### 7. Troubleshooting

- **Installation issues**: Ensure Go is installed correctly. Use `go env` to check Go environment variables.
- **Connection errors**: Verify the target URL and network connection.
- **Permissions**: Run commands with `sudo` if you encounter permission issues.

### 8. Resources

- [Fuff GitHub Repository](https://github.com/ffuf/ffuf)
- [Kali Linux Documentation](https://www.kali.org/docs/)
- [OWASP Wordlists](https://owasp.org/www-project-seclists/)

---

This cookbook provides a comprehensive guide to using Fuff on Kali Linux. Whether you're a beginner or an advanced user, this guide will help you utilize Fuff's powerful capabilities effectively.
