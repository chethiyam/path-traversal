# path-traversal
Path traversal is a security vulnerability that allows attackers to access files outside a web application’s intended directory by manipulating input with sequences like `../`. This can lead to unauthorized access to sensitive files, resulting in data exposure or potential system compromise.
Path traversal is a type of security vulnerability where an attacker manipulates input to access files and directories that are outside the authorized scope of an application. This can allow attackers to read, modify, or delete sensitive files, potentially leading to a complete system compromise.

How Path Traversal Works:
User Input Handling: Web applications often take user input to specify files or directories. For example, a URL may include a filename as a parameter:
https://example.com/view?file=report.txt
Manipulation: In a path traversal attack, an attacker manipulates this input to traverse to a different file by using special characters like ../ (dot-dot-slash), which represents the parent directory. Example:
https://example.com/view?file=../../etc/passwd This would attempt to access the /etc/passwd file, which is outside the web root directory and could contain sensitive system information.
Common Path Traversal Sequences:
../: Move up one directory
../../: Move up two directories
%2e%2e%2f: URL-encoded equivalent of ../
/..: Move to the parent directory from the current one
Risks and Impact:
Unauthorized File Access: Attackers can read sensitive files (e.g., password files, configuration files, etc.).
Remote Code Execution: If attackers can upload or modify executable files, they might execute malicious code on the server.
Information Disclosure: Sensitive data exposure, like system details or application configurations.
Preventing Path Traversal:
Input Validation: Always validate and sanitize user input to ensure it doesn't contain special characters or sequences like ../.
Use Secure APIs: Use APIs that safely handle file paths without exposing underlying file system structure (e.g., realpath in PHP).
Access Control: Implement strict file access permissions to ensure the web server can only access specific directories.
Whitelisting: Allow only specific, trusted files to be accessed based on a whitelist.
Path Normalization: Normalize the file path to remove sequences like ../ before processing it.
