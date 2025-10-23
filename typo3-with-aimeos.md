# TYPO3 Multi-Instance Local Setup - Cheat Sheet

## Important Files & Locations

**Windows Host File:** `C:\Windows\System32\drivers\etc\hosts`

---

## 1. Database Setup

### Method A: Using phpMyAdmin

#### Enable Large File Upload

1. **Create upload folder:**
   ```
   C:\wamp64\apps\phpmyadmin5.2.1\upload
   ```

2. **Edit config file:** `C:\wamp\apps\phpmyadminX.X.X\config.inc.php`
   ```php
   /* >>> ADD THIS LINE <<< */
   $cfg['UploadDir'] = 'upload';
   
   /* End of servers configuration */
   ?>
   ```

3. **Copy SQL file** to the upload folder

4. **Restart WAMP**

5. **Import via phpMyAdmin:**
   - Open phpMyAdmin → Import tab
   - Select file from "Upload directory" dropdown

---

### Method B: Using Command Line

#### Basic Import
```bash
mysql -u root -p database_name < "C:\path\to\file.sql"
```

**Example:**
```bash
mysql -u root -p new_orwo_multi < "C:\wamp64\apps\phpmyadmin5.2.1\upload\t3multi_live1_20250723.sql"
```

#### Import with Foreign Key Issues

```bash
# Step 1: Disable foreign key checks
mysql -u root -p database_name -e "SET FOREIGN_KEY_CHECKS=0;"

# Step 2: Import SQL file
mysql -u root -p database_name < "C:\path\to\file.sql"

# Step 3: Re-enable foreign key checks
mysql -u root -p database_name -e "SET FOREIGN_KEY_CHECKS=1;"
```

#### Single Command (All-in-One)
```bash
mysql -u root -p database_name -e "SET FOREIGN_KEY_CHECKS=0; SOURCE C:/path/to/file.sql; SET FOREIGN_KEY_CHECKS=1;"
```

**Example:**
```bash
mysql -u root -p new_multi_ins -e "SET FOREIGN_KEY_CHECKS=0; SOURCE C:/Users/rahman.habib/Desktop/project/typo3/orwo_multi/Multimandanten-Instanz/09.2025/test_multimandant_live_kopie.sql; SET FOREIGN_KEY_CHECKS=1;"
```

---

## 2. TYPO3 Instance Setup

1. **Download TYPO3 instance** from:
   ```
   O:\04-Softwareentwicklung\TYPO3\Multimandanten-Instanz
   ```

2. **Configure settings.php:**
   - Update database credentials
   - Update `trustedHostsPattern`
   - Adjust other environment-specific settings

---

## 3. Create Symbolic Links

**⚠️ Run CMD as Administrator**

1. **Navigate to packages directory:**
   ```bash
   cd C:\wamp64\www\orwo_multi\packages
   ```

2. **Create symbolic link:**
   ```bash
   mklink /D link_name C:\path\to\target\directory
   ```

**Example:**
```bash
mklink /D aimeos_frontend c:\git-typo3\aimeos_frontend
```

### mklink Syntax
```bash
mklink /D [link_name] [target_path]
```
- `/D` - Creates a directory symbolic link
- `link_name` - Name of the symbolic link to create
- `target_path` - Path to the actual directory

---

## Quick Reference

| Task | Command/Location |
|------|------------------|
| Host file | `C:\Windows\System32\drivers\etc\hosts` |
| phpMyAdmin upload | `C:\wamp64\apps\phpmyadmin5.2.1\upload` |
| Config file | `C:\wamp\apps\phpmyadminX.X.X\config.inc.php` |
| Packages directory | `C:\wamp64\www\orwo_multi\packages` |
| CMD as admin | **Required** for MySQL imports & symbolic links |
| TYPO3 source | `O:\04-Softwareentwicklung\TYPO3\Multimandanten-Instanz` |

---

## Notes

- Always run CMD as **Administrator** for database operations and symbolic links
- Restart WAMP after configuration changes
- Use forward slashes (`/`) in SOURCE paths for MySQL commands
- Symbolic links require administrator privileges on Windows
- Replace `database_name`, `link_name`, and paths with your actual values