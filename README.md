# Table of contents

* [About the project](#about-the-project)
* [Installation](#installation)
* [Usage](#usage)
* [Authors](#authors)
* [License](#license)

# About the project

This Bash script automates the setup of a new Apache2 VirtualHost, complete with:

* Custom domain configuration (with optional www. subdomain)
* Directory structure creation
* Let's Encrypt SSL certificate setup

### Features

✍ **User inputs**
* Domain name (e.g. example.com)
* E-Mail address (used for Let's Encrypt registration)
* New system username
* Optional www. subdomain support

📂 **Directory structure:**
* Creates following directorys:
```
/var/www/<domain>/
├── httpdocs   # Web root
├── logs       # Apache logs
└── files      # Optional file storage
```

🔑 **User & permissions:**
* Adds new user (if not existing) with:
* Home directory at /var/www/<domain>
* /usr/sbin/nologin shell (no terminal access)
* Sets ownership and permissions for web and SFTP usage
* User belongs to www-data group

🛠️ **Apache configuration:**
* Creates basic HTTP VirtualHost with automatic redirect to HTTPS
* Enables rewrite and ssl modules
* Requests a Let's Encrypt certificate using Certbot
* On success, appends a full HTTPS VirtualHost configuration
* Removes default -le-ssl.conf created by Certbot to avoid conflicts

# Installation

Clone this repo:
```
git clone https://github.com/evarioooo/vhostgen-sh.git
```

Change directory to
```
cd vhostgen-sh
```

To run this script we should add permission

```
chmod +x vhostgen-sh
```

# Usage

```
./vhostgen-sh
```

# Authors

* [evarioooo](https://github.com/evarioooo)

# License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
