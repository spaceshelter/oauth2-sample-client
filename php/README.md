# Orbitar OAuth2 PHP Client Sample

This is a single-file PHP application that demonstrates the complete OAuth2 flow for Orbitar.

## Features

This sample demonstrates:
- Authorization code flow
- Token exchange
- API requests with access tokens
- Token refresh
- Embedded app card landing page simulation

## Requirements

- PHP 7.4+
- PHP Extensions: curl, json, session

## Running the Sample

1. Edit the configuration section in `index.php` to add your client credentials:
   ```php
   $config = [
       'client_id' => 'YOUR_CLIENT_ID',
       'client_secret' => 'YOUR_CLIENT_SECRET',
       // other config...
   ];
   ```

2. Run a PHP server:
   ```bash
   php -S localhost:3000
   ```

3. Access the application at http://localhost:3000

## Implementation Notes

This sample uses a single `index.php` file with query string parameters to determine the action:

- `index.php` - Home page (default)
- `index.php?action=login` - Initiates the authorization flow
- `index.php?action=start` - Simulates the app card landing page
- `index.php?action=initiate-auth` - Initiates auth from landing page
- `index.php?action=callback` - OAuth2 callback handler
- `index.php?action=status` - Check API status with token
- `index.php?action=logout` - Logout

This approach eliminates the need for multiple files or URL rewriting.

## Configuration

The sample uses the following configuration structure:

```php
$config = [
    // Replace with your client credentials
    'client_id' => 'YOUR_CLIENT_ID',
    'client_secret' => 'YOUR_CLIENT_SECRET',
    
    // Application settings
    'scope' => 'status',
    'redirect_uri' => 'http://localhost:3000/index.php?action=callback',
    
    // This would be your Initial Authorization URL in the client app settings
    'initial_auth_url' => 'http://localhost:3000/index.php?action=start',
    
    // Orbitar endpoints
    'authorization_endpoint' => 'https://orbitar.local/oauth2/authorize',
    'token_endpoint' => 'https://api.orbitar.local/api/v1/oauth2/token',
    'api_endpoint' => 'https://api.orbitar.local/api/v1/status'
];
```

## Security Notes

This sample disables SSL certificate verification for ease of development. This is **NOT** suitable for production. In a production environment:

1. Ensure proper SSL certificate validation
2. Store client secrets securely
3. Use HTTPS for all communication
4. Implement proper state validation and CSRF protection
5. Use secure, randomly generated session keys