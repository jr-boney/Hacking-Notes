

### Key Google Dork Tags for Finding Leaked Sensitive Information

#### 1. **Look for `.env` Files with Database Credentials**:
   These queries will help find `.env` files containing sensitive information like database usernames and passwords.

   - `filetype:env DB_USERNAME`
   - `filetype:env DB_PASSWORD`
   - `filetype:env DB_HOST`
   - `filetype:env DB_PORT`
   - `filetype:env DB_NAME`
   - `filetype:env "DB_"` — This can help you find any `.env` files containing database-related variables.
   
   **Example**:  
   - `filetype:env DB_USERNAME`  
   - `filetype:env DB_PASSWORD`  
   These dorks search for `.env` files containing **database-related environment variables** like `DB_USERNAME` and `DB_PASSWORD`.

#### 2. **Search for Files Containing Database Information in Various Formats**:
   Database-related credentials might not only be in `.env` files, but also in other configuration files like `config.php`, `.yml`, `.json`, `.txt`, etc.

   - `filetype:php "define('DB_USER'"` — Search for PHP files that define database username constants.
   - `filetype:php "define('DB_PASSWORD'"` — Search for PHP files that define database password constants.
   - `filetype:yaml DB_USERNAME`
   - `filetype:json DB_USERNAME`
   - `filetype:txt DB_USERNAME`

   **Example**:
   - `filetype:php "define('DB_PASSWORD'"` searches for PHP files that might define sensitive database credentials using the `define()` function.

#### 3. **Search for `.git` Directories Exposing Sensitive Data**:
   If a project’s Git repository is exposed publicly, it could potentially contain sensitive information like credentials.

   - `intitle:index of .git`
   - `inurl:.git/config`

   **Example**:  
   - `intitle:index of .git` looks for publicly accessible `.git` directories, which may contain sensitive configuration files and credentials if not properly secured.

#### 4. **Search for `.sql` Files (Database Dumps)**:
   Database dumps are often saved as `.sql` files and can contain sensitive information, including usernames and passwords.

   - `filetype:sql "CREATE DATABASE"`
   - `filetype:sql "INSERT INTO"`
   - `filetype:sql "password"`
   - `filetype:sql "DB_PASSWORD"`

   **Example**:  
   - `filetype:sql "CREATE DATABASE"` can reveal SQL files that might contain sensitive data like database structures and potentially passwords.

#### 5. **Search for Exposed Backup Files**:
   Backup files (e.g., `.bak`, `.zip`, `.tar`, `.dump`) might contain full database dumps or application backups that contain passwords.

   - `filetype:bak DB_PASSWORD`
   - `filetype:bak "password"`
   - `filetype:zip DB_PASSWORD`
   - `filetype:dump DB_PASSWORD`

   **Example**:  
   - `filetype:bak DB_PASSWORD` looks for backup files that may contain database credentials.

#### 6. **Search for Configuration Files with Hardcoded Credentials**:
   Sometimes, developers hardcode credentials in configuration files. These can be exposed due to improper file permissions.

   - `filetype:php "DB_USER"`
   - `filetype:config "DB_PASSWORD"`
   - `filetype:properties DB_PASSWORD`
   - `filetype:json "password"`
   - `filetype:xml "DB_PASSWORD"`

   **Example**:  
   - `filetype:php "DB_USER"` searches for PHP files containing `DB_USER` credentials, often hardcoded into the file.

