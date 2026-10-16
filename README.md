<div align="center">
	<a href="https://www.qloapps.com"><img src="https://forums.qloapps.com/assets/uploads/system/site-logo.png?v=hkl8e1230fo" alt="QloApps"></a>
	<br>
	<p>
		<b>QloApps - An open source and free platform to launch your own hotel booking website</b>
	</p>
</div>

<p align="center">
	<a href="https://qloapps.com/download/"><img src="https://img.shields.io/badge/Download-Download%20QloApps%20-brightgreen" alt="Download"></a>
	<a href="https://docs.qloapps.com/"><img src="https://img.shields.io/badge/Documentation-Blog-yellowgreen" alt="Documentation"></a>
	<a href="https://forums.qloapps.com/"><img src="https://img.shields.io/badge/Forum-Help%2FSupport-green" alt="Forum"></a>
	<a href="https://qloapps.com/addons/"><img src="https://img.shields.io/badge/Addons-Plugins-blueviolet" alt="Addons"></a>
	<a href="https://qloapps.com/contact/"><img src="https://img.shields.io/badge/Contact-Get%20In%20Touch-blue" alt="Contact us"></a>
	<a href="/LICENSE.md"><img src="https://img.shields.io/badge/License-OSL%20V3-green" alt="License"></a>
	<img src="https://img.shields.io/badge/Status-Archived%20%2F%20Closed-inactive" alt="Project Status">
</p>

---

> [!NOTE]
> ### 📌 Project Status: Closed / Archived
> **This repository is currently closed and archived.** Active development is discontinued by the maintainer. The codebase has been fully verified, configured, and tested locally with PHP 8.5 compatibility and local MariaDB integration. All information below is provided for archival, reference, and deployment purposes.

---

## Table of Contents
- [Project Status: Closed / Archived](#-project-status-closed--archived)
- [Source of the Code & Credits](#source-of-the-code--credits)
- [System Features](#system-features)
- [Technology Stack](#technology-stack)
- [System Requirements & Local Setup](#system-requirements--local-setup)
  - [PHP 8.5 Compatibility Notes](#php-85-compatibility-notes)
  - [MariaDB Configuration](#mariadb-configuration)
  - [Running the Local Development Server](#running-the-local-development-server)
  - [Post-Installation Steps](#post-installation-steps)
- [License](#license)
- [Resources & Support](#resources--support)

---

## Source of the Code & Credits

- **Original Project:** [QloApps (Open-Source Hotel Reservation System)](https://qloapps.com)
- **Upstream Repository:** [https://github.com/Qloapps/QloApps](https://github.com/Qloapps/QloApps)
- **Creator / Maintainer:** [Webkul Software](https://webkul.com) and the QloApps Community.
- **Documentation:** [https://docs.qloapps.com](https://docs.qloapps.com)
- **Official Forum:** [https://forums.qloapps.com](https://forums.qloapps.com)
- **Official Demo:** [https://demo.qloapps.com](https://demo.qloapps.com)

---

## System Features

QloApps is a dedicated Property Management System (PMS) and online booking engine designed for hotels, guest houses, and resorts.

### 🏨 Property Management (PMS)
- **Hotel & Room Configuration:** Manage multiple hotel properties, branches, room types, and individual room numbers.
- **Real-Time Availability Calendar:** Interactive calendar displaying booked, available, and reserved rooms.
- **Front-Desk Walk-In Bookings:** Allows hotel staff to take offline or on-desk bookings directly through the admin back-office.
- **Room Status Tracking:** Real-time visibility into occupied, vacant, cleaned, and maintenance states.

### 🌐 Online Booking Engine
- **Customer Booking Portal:** Responsive booking flow with interactive date-picker, guest count, and room capacity filters.
- **Instant Booking Confirmations:** Automated email receipts and booking confirmations for guests and hotel managers.
- **Multilingual Support:** Supports translation across 60+ languages with language-specific content.
- **Multi-Currency:** Automatic and configurable currency conversions for global travelers.

### 💰 Rates, Pricing & Taxes
- **Seasonal & Dynamic Pricing:** Configure base prices, weekend rates, and custom seasonal price rules.
- **Discounts & Coupons:** Promotional vouchers, percentage/fixed discounts, and group discounts.
- **Tax Rules:** Flexible VAT, hospitality tax, and service fee configurations per hotel or region.

### 💳 Payments & Order Management
- **Payment Gateways:** Supports modular payment integration (PayPal, Stripe, Bank Wire, Cash on Arrival).
- **Invoice Generation:** Automatic PDF invoice generation for customer orders and booking checkouts.
- **Customer Profiles:** Customer order history, account management, and saved guest details.

### 🧩 Extensible Architecture
- **Hook-based Modular System:** Extend functionality using custom modules without editing core code.
- **Smarty 3 Templating:** Separated view layer for easy frontend customization and theme development.

---

## Technology Stack

- **Backend:** PHP 8.1–8.5 (Object-oriented MVC architecture)
- **Templates:** Smarty 3.x
- **Frontend:** HTML5, CSS3, JavaScript, jQuery
- **Database:** MySQL 5.7+ / 8.0+, MariaDB 10.5+ to 11.4+
- **Web Server:** Apache (with `mod_rewrite`), Nginx, or PHP CLI Server for development

---

## System Requirements & Local Setup

### PHP 8.5 Compatibility Notes
While standard QloApps supports PHP 8.1 to 8.4, this repository contains a compatibility update in [`classes/ConfigurationTest.php`](classes/ConfigurationTest.php) to support PHP 8.5+ runtimes.

Ensure the following PHP extensions are enabled:
- `pdo_mysql`, `gd`, `soap`, `curl`, `openssl`, `simplexml`, `dom`, `zip`, `phar`

### MariaDB Configuration
Create a dedicated database and user with privileges:
```bash
sudo mariadb -e "CREATE DATABASE IF NOT EXISTS qloapps CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci; \
CREATE USER IF NOT EXISTS 'qloapps'@'localhost' IDENTIFIED BY 'qloapps123'; \
CREATE USER IF NOT EXISTS 'qloapps'@'127.0.0.1' IDENTIFIED BY 'qloapps123'; \
GRANT ALL PRIVILEGES ON qloapps.* TO 'qloapps'@'localhost'; \
GRANT ALL PRIVILEGES ON qloapps.* TO 'qloapps'@'127.0.0.1'; \
FLUSH PRIVILEGES;"
```

### Running the Local Development Server
Launch the PHP built-in server with all required runtime extensions and configuration limits:
```bash
php -d extension=gd \
    -d extension=soap \
    -d upload_max_filesize=32M \
    -d post_max_size=32M \
    -d memory_limit=256M \
    -d max_execution_time=500 \
    -S 127.0.0.1:8000
```

Access the installation assistant at `http://127.0.0.1:8000/install/`.

### Post-Installation Steps
1. **Remove or Rename `/install`**:
   For security, QloApps blocks access to the admin dashboard and store until the installation folder is removed:
   ```bash
   mv install install_backup
   ```
2. **Access URLs**:
   - **Back-Office (Admin):** `http://127.0.0.1:8000/admin/`
   - **Front-Office (Store):** `http://127.0.0.1:8000/`
3. **Database Secrets**:
   The generated `config/settings.inc.php` file stores database credentials and cryptographic salt keys. It is ignored by `.gitignore` to prevent secret leakage.

---

## License

- **Core:** [Open Software License (OSL 3.0)](https://opensource.org/licenses/OSL-3.0)
- **Modules:** [Academic Free License (AFL 3.0)](https://opensource.org/licenses/AFL-3.0) / Proprietary Webkul licenses where indicated.

---

## Resources & Support

- **Official Website:** [https://qloapps.com](https://qloapps.com)
- **Documentation:** [https://docs.qloapps.com](https://docs.qloapps.com)
- **Community Forum:** [https://forums.qloapps.com](https://forums.qloapps.com)
- **Security Inquiries:** [mailto:support@qloapps.com](mailto:support@qloapps.com)
