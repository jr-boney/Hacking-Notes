

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

# API

When APIs are exposed unintentionally or not properly secured, they can provide attackers with access to sensitive information or functionality. To help identify APIs that are exposed publicly, you can use **Google Dorking** to search for specific patterns or files that may indicate vulnerable or exposed APIs.

Below are several **Google Dork queries** to help detect exposed **APIs** and related sensitive data.

### Google Dorks for Finding Exposed APIs:

#### 1. **Search for API Endpoints in URLs**:
APIs are often exposed through HTTP endpoints, and sometimes their URLs are publicly accessible. You can search for exposed API endpoints in URLs using these queries.

- `inurl:/api/` — This searches for URLs containing `/api/`, which is a common path for RESTful API endpoints.
- `inurl:/v1/` — Often APIs will have versioning in the URL (e.g., `/v1/`).
- `inurl:/endpoint/` — Search for URLs with the word "endpoint," which could indicate API functionality.
- `inurl:/api/v1/` — Search for `/api/v1/`, a common pattern for versioned APIs.
- `intitle:"index of" api` — Searches for API-related files that might be publicly indexed in directory listings.

#### 2. **Look for API Documentation Files**:
Sometimes, API documentation is publicly exposed, which can provide attackers with an insight into how to interact with the API.

- `filetype:pdf api documentation` — Looks for PDF files that may contain API documentation.
- `filetype:html "API Documentation"` — Finds HTML files with "API Documentation" in the content, which may expose API endpoints and usage.
- `filetype:txt api` — Looks for plain-text files with "api" in them, which may contain public-facing API documentation.
- `filetype:json "api"` — Searches for JSON files that may be used for API responses or configuration, potentially revealing sensitive endpoints.
- `filetype:yaml api` — Finds YAML files related to API configuration, which might expose private API endpoints or keys.

#### 3. **Search for API Keys or Credentials Exposed in Files**:
API keys are sometimes hardcoded into source code, configuration files, or documentation. The following dorks help search for exposed API keys.

- `filetype:env "API_KEY"` — Search for environment files that might contain API keys.
- `filetype:php "API_KEY"` — Look for PHP files that might contain API keys or secrets.
- `filetype:json "API_KEY"` — Search for JSON files containing `"API_KEY"`, which is a common key name for API keys in configurations.
- `filetype:txt "API_KEY"` — Search for plain-text files containing exposed API keys.
- `filetype:xml "apiKey"` — Search for XML files with `"apiKey"`, which may store API keys.
- `filetype:yaml "api_key"` — Search for YAML files that may store API keys.
- `filetype:js "API_KEY"` — Search for JavaScript files that might contain hardcoded API keys.

#### 4. **Look for Exposed Swagger or OpenAPI Specifications**:
Swagger and OpenAPI are common tools used to document and describe APIs. If not properly secured, these files could expose the structure and functionality of an API.

- `filetype:json swagger` — Search for JSON Swagger/OpenAPI documentation files.
- `filetype:yml swagger` — Search for YAML Swagger/OpenAPI documentation files.
- `inurl:/swagger/` — Search for URLs containing `/swagger/`, which is a common path for API documentation.
- `inurl:/swagger.json` — Searches for Swagger documentation files in JSON format.
- `inurl:/openapi.json` — Search for OpenAPI specification files in JSON format.
- `inurl:/api-docs/` — Search for the common path for Swagger or API documentation (`/api-docs/`).

#### 5. **Look for API Response Data Exposed in Files**:
Sometimes, API responses or logs are exposed directly through URL parameters or query strings. This might reveal sensitive API data or internal systems.

- `inurl:"API response" filetype:json` — Search for exposed JSON API responses that might leak sensitive data.
- `inurl:"API response" filetype:xml` — Search for exposed XML API responses.
- `inurl:"access_token"` — Searching for exposed access tokens or API tokens that might be found in API response logs or URL parameters.
- `inurl:"auth_token"` — Search for URLs that contain `auth_token`, which is often used in API authentication.

#### 6. **Search for Exposed API in CMS or Platform Files**:
If you are working with popular CMSs or frameworks (e.g., WordPress, Django, Node.js), it’s useful to look for certain API files or routes that could be exposed.

- `inurl:wp-json` — Search for exposed WordPress REST API endpoints (e.g., `/wp-json/`).
- `inurl:/admin/api/` — Search for admin API endpoints that may be exposed unintentionally.
- `inurl:/wp-admin/admin-ajax.php` — Exposes endpoints for interacting with WordPress through AJAX.
- `inurl:/api/v2/` — Look for endpoints related to API version 2.
- `filetype:php "wp_remote_get"` — Searches for PHP files that might use the `wp_remote_get` function to call external APIs.
- `inurl:/admin/ "api"` — Searches for API routes that are part of an admin panel, potentially exposing sensitive data.

#### 7. **Search for Exposed API Logs**:
Sometimes, logs may contain sensitive API data, such as API responses, access tokens, and other data that could be exploited.

- `filetype:log api` — Looks for `.log` files that may contain API-related information.
- `filetype:txt "API call"` — Search for text files with entries like `"API call"`, which might expose API access logs.
- `filetype:log "authorization header"` — Search for logs containing `authorization` headers, which might expose sensitive API tokens.

### How These Dorks Help:
- **Identifying Exposed APIs**: Many organizations accidentally expose sensitive API endpoints or documentation publicly. The dorks listed above will help locate such instances.
- **Finding Exposed API Keys and Secrets**: API keys, tokens, and other sensitive credentials are sometimes hardcoded in source code, configuration files, or exposed via API responses. These dorks can help identify these vulnerabilities.
- **Exposing Documentation or Endpoints**: Sometimes API documentation, like Swagger files, is accidentally made public. These dorks help to locate that information.

