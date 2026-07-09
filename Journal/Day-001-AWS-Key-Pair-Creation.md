#  AWS Key Pair Creation

## Challenge Objective

The objective of this task was to create an AWS Key Pair that can be used for secure SSH access to EC2 instances.

AWS Key Pairs consist of:

* **Public Key** – Stored by AWS and attached to EC2 instances.
* **Private Key (.pem file)** – Downloaded and stored securely by the user. It is required to connect to the EC2 instance through SSH.

---

## Task Requirements

The task required:

* Creating a new AWS Key Pair.
* Selecting the correct key pair type.
* Downloading and securely storing the private key file.
* Verifying that the key pair was successfully created.

---

# Step-by-Step Process

## Step 1: Open AWS Management Console

Logged into the AWS Management Console.

Navigated to:

```
EC2 → Network & Security → Key Pairs
```

---

## Step 2: Create a New Key Pair

Clicked:

```
Create Key Pair
```

Provided the required details:

**Key Pair Name:**

```
kodekloud-key
```

**Key Pair Type:**

```
RSA
```

**Private Key Format:**

```
.pem
```

Then clicked:

```
Create Key Pair
```

---

## Step 3: Download Private Key

AWS automatically downloaded the private key file:

```
kodekloud-key.pem
```

This file is required later when connecting to EC2 instances using SSH.

---

# Problems I Encountered

## 1. Understanding the Purpose of a Key Pair

### Issue

Initially, I was confused about why AWS requires a key pair instead of a normal username and password.

### Solution

I learned that AWS uses public-key cryptography for secure authentication.

The private key acts as proof of ownership when connecting to an EC2 instance.

---

## 2. Difference Between Public Key and Private Key

### Issue

I was unsure about which key should be shared and which key should be protected.

### Solution

Understanding:

* Public Key → Safe to share with AWS.
* Private Key → Must be kept secret and never uploaded publicly.

The `.pem` file downloaded from AWS is the private key.

---

## 3. Protecting the Private Key File

### Issue

SSH requires proper permissions for private key files. Incorrect permissions can cause connection errors.

Example error:

```
WARNING: UNPROTECTED PRIVATE KEY FILE!
```

### Solution

Changed the file permissions:

```bash
chmod 400 kodekloud-key.pem
```

This allows only the owner to read the key.

---

# Verification

Checked that the key pair was successfully created in AWS EC2 Console.

The key pair appeared under:

```
EC2 → Key Pairs
```

The downloaded `.pem` file was stored safely for future EC2 SSH connections.

---

# Commands Used

```bash
chmod 400 kodekloud-key.pem
```

---

# Key Learnings

* Learned how AWS EC2 authentication works using key pairs.
* Understood the difference between public and private keys.
* Learned the importance of protecting private keys.
* Learned how SSH uses private keys for secure access.
* Improved understanding of AWS security basics.

---

# Outcome

✅ Created an AWS EC2 Key Pair successfully.

✅ Downloaded and secured the private key.

✅ Learned the basics of SSH authentication in AWS.

**Status:** ✔️ Completed Successfully
