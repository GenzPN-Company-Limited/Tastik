# 🥲 Error Login Account

## Bug Fix: Handling Special Characters in Account Credentials

***

### **Issue**

If your Apple Music account email or password contains special characters (e.g., `~!@#$%^&*()_+{}":><?"`), the wrapper may fail to process the credentials correctly. This can result in login errors or unexpected behavior.

***

### **Solution**

To handle special characters in your email or password, wrap the credentials in **single quotes** (`'`) when running the wrapper command. This ensures that the shell interprets the credentials correctly.

***

#### **Correct Command Syntax**

```bash
sudo ./wrapper -M 20020 -L 'email':'password'
```

***

#### **Example**

If your email is `alex@gmail.com` and your password is `Alexg1osd@(#$`, use the following command:

```bash
sudo ./wrapper -M 20020 -L 'alex@gmail.com':'Alexg1osd@(#$'
```

***

### **Why This Works**

* Special characters like `!`, `@`, `#`, `$`, etc., have special meanings in the shell.
* Wrapping the credentials in single quotes (`'`) tells the shell to treat the entire string as a literal value, ignoring any special characters.

***

### **Additional Notes**

* Ensure there are no spaces between the email, colon (`:`), and password.
*   If your password contains a single quote (`'`), escape it using a backslash (`\`). For example:

    ```bash
    sudo ./wrapper -M 20020 -L 'alex@gmail.com':'Alexg1osd@(#$\''
    ```
