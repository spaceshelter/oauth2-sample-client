# Orbitar OAuth2 Node.js Client Sample

This is a Node.js Express sample application that demonstrates the complete OAuth2 flow for Orbitar.

## Features

This sample demonstrates:
- Authorization code flow
- Token exchange
- API requests with access tokens
- Token refresh
- Embedded app card landing page simulation

## Requirements

- Node.js 14+
- npm packages: express, express-session, axios

## Running the Sample

1. Install dependencies:
   ```bash
   npm install
   ```

2. Edit the configuration section in `index.js` to add your client credentials:
   ```javascript
   const config = {
     clientId: 'YOUR_CLIENT_ID',
     clientSecret: 'YOUR_CLIENT_SECRET',
     // other config...
   };
   ```

3. Run the application:
   ```bash
   npm start
   ```

4. Access the application at http://localhost:3000

## Configuration

The sample uses the following configuration structure:

```javascript
const config = {
  // Replace with your client credentials
  clientId: 'YOUR_CLIENT_ID',
  clientSecret: 'YOUR_CLIENT_SECRET',
  
  // Application settings
  port: 3000,
  scope: 'status',
  redirectUri: 'http://localhost:3000/callback',
  
  // This would be your Initial Authorization URL in the client app settings
  initialAuthUrl: 'http://localhost:3000/start',
  
  // Orbitar endpoints
  authorizationEndpoint: 'https://orbitar.space/oauth2/authorize',
  tokenEndpoint: 'https://api.orbitar.space/api/v1/oauth2/token',
  apiEndpoint: 'https://api.orbitar.space/api/v1/status'
};
```

## Security Notes

This sample disables SSL certificate verification for ease of development. This is **NOT** suitable for production. In a production environment:

1. Ensure proper SSL certificate validation
2. Store client secrets securely
3. Use HTTPS for all communication
4. Implement proper state validation and CSRF protection
5. Use secure, randomly generated session keys