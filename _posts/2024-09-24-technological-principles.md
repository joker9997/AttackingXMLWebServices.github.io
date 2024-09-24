---
title: "Technological Principles of Broken Access Control"
date: 2024-09-24
categories: [Security, Vulnerabilities]
---

# Technological Principles of Broken Access Control
 
 <iframe src="https://giphy.com/embed/3oEjHHOaHimAspYVVu" width="480" height="288" style="" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/producthunt-euro-2016-terminal-on-mac-3oEjHHOaHimAspYVVu"></a></p>
 
Broken Access Control vulnerabilities arise when an application does not properly enforce access restrictions, allowing unauthorized users to gain privileges or access resources they shouldn’t. These weaknesses are often a result of poor coding practices or improper configurations in web applications.

## How Access Control Works

Access control systems are designed to restrict users to only the resources and operations they are allowed to interact with. In a typical web application, this involves verifying that users:
- Can only access pages or data they are permitted to view.
- Can perform only actions allowed by their role (e.g., view, edit, delete).

**Access control** is divided into two main types:
- **Horizontal Access Control**: Ensures users can access only their own data (e.g., a user’s bank account info) and not others.
- **Vertical Access Control**: Restricts actions based on the user's role (e.g., admin vs regular user).

When these controls are not correctly implemented, users can gain unintended access to data or perform actions they should not be able to.

## Common Variations of Broken Access Control

Here are some common types of **Broken Access Control** vulnerabilities:

### 1. **Insecure Direct Object References (IDOR)**
IDOR occurs when an application exposes a reference to an internal object, such as a file, database entry, or user account, in the URL or request. If this reference isn’t validated properly, attackers can manipulate it to access unauthorized resources.
- **Example**: Changing a URL parameter like `/user/1234` to `/user/1235` might allow an attacker to view another user’s data.

### 2. **Privilege Escalation**
Privilege escalation occurs when a user gains elevated permissions due to a flaw in access control enforcement.
- **Example**: A user registered as a "guest" may find a way to escalate their role to an "admin" by manipulating a poorly secured privilege-checking function.

### 3. **Missing Function-Level Access Control**
This happens when certain critical functions in a web application (e.g., delete or update) are not protected by access control checks.
- **Example**: If an attacker knows the URL for deleting a user, they may access it directly, bypassing the restrictions.

### 4. **Forced Browsing**
In forced browsing, attackers manipulate URLs or parameters to access pages or functionalities that should be restricted.
- **Example**: By modifying URLs, users may be able to access hidden sections of the site without appropriate permissions.

## How It Happens: Technical Flaws

Here are some of the common flaws that lead to Broken Access Control:
1. **Improperly Implemented Role-Based Access Control (RBAC)**: If RBAC is not enforced consistently across the application, users may access unauthorized areas.
2. **Inconsistent Session Management**: Applications that do not properly track user sessions may allow attackers to "reuse" old sessions and access restricted data.
3. **Hardcoding Sensitive Data**: Storing sensitive information in URLs or client-side components that can be manipulated by users.
4. **Missing or Weak Authentication Checks**: Failing to verify the identity and permissions of users before granting access.

## Technologies Involved

Access control relies on a combination of **backend** and **frontend** technologies:
- **Backend Technologies**: Responsible for managing user roles, authentication, and access control logic (e.g., databases, server-side languages like PHP, Node.js).
- **Frontend Technologies**: Sometimes handle authorization logic, but this is risky since client-side validation can be bypassed (e.g., JavaScript).

To ensure secure access control, developers need to carefully architect the system’s permissions and regularly audit the code for vulnerabilities.

## Stay Secure

To prevent Broken Access Control, developers must:
- Implement **strong session management**.
- Validate access rights **server-side** for every request.
- Regularly review access control rules as the application evolves.

In the next post, we will explore various **security approaches** and **best practices** to mitigate these vulnerabilities and ensure secure access control.

### Sources:
- [OWASP Cheat Sheet on Access Control](https://cheatsheetseries.owasp.org/cheatsheets/Access_Control_Cheat_Sheet.html)

<div class="comments-section">
    <h3>Comments</h3>
    
    <!-- Static comments -->
    <div class="comment">
        <strong>Oleksandr Lanskyi</strong>: <p>Great insights on broken access control! Looking forward to reading more.</p>
    </div>
    <div class="comment">
        <strong>Kyrylo Koelsnicehnko</strong>: <p>Very informative blog! Keep up the good work.</p>
    </div>
    <div class="comment">
        <strong>Arseniia Bohdanova.</strong>: <p>Interesting perspectives. I learned a lot from this post.</p>
    </div>

    <form id="comment-form">
        <input type="text" id="comment-author" placeholder="Your Name" required>
        <textarea id="comment-text" placeholder="Your Comment" required></textarea>
        <button type="submit">Submit Comment</button>
    </form>
    <div id="comments-list"></div>
</div>
<script>
    // Add event listener to the comment form
    document.getElementById('comment-form').onsubmit = function(e) {
        e.preventDefault();
        
        var author = document.getElementById('comment-author').value;
        var text = document.getElementById('comment-text').value;
        var commentsList = document.getElementById('comments-list');

        // Create a new comment element
        var comment = document.createElement('div');
        comment.className = 'comment';
        comment.innerHTML = `<strong>${author}</strong>: <p>${text}</p>`;
        
        // Append the new comment to the comments list
        commentsList.appendChild(comment);
        
        // Reset the form fields
        document.getElementById('comment-form').reset();
    };
</script>