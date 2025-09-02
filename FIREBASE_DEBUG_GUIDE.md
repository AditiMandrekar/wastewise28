# Firebase Connection Debug Guide

## Current Issue
The app is showing Firebase connection errors:
- `WebChannelConnection RPC 'Listen' stream transport errored`
- `Failed to get document because the client is offline`

## Debugging Steps

### 1. Check the Debug Panel
The login screen now includes a Firebase debug panel that shows:
- Connection status
- User authentication state
- Network connectivity
- Firebase configuration status

### 2. Common Solutions

#### Network Issues
- **Check internet connection**: Ensure device has stable internet
- **Firewall/Proxy**: Corporate networks may block Firebase
- **VPN**: Try disabling VPN if active

#### Firebase Configuration
- **Project Status**: Verify Firebase project is active
- **API Keys**: Check if API keys are valid and not restricted
- **Firestore Rules**: Ensure Firestore allows read/write operations

#### Development Environment
- **Metro Cache**: Clear Metro cache: `npx expo start --clear`
- **Node Modules**: Reinstall dependencies: `rm -rf node_modules && npm install`
- **Expo Cache**: Clear Expo cache: `npx expo install --fix`

### 3. Firebase Console Check
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Select project: `wastewise-6e82b`
3. Check:
   - Project is not suspended
   - Firestore is enabled
   - Authentication is enabled
   - API keys are not restricted

### 4. Test Commands
```bash
# Clear all caches
npx expo start --clear

# Check network connectivity
ping google.com

# Test Firebase project access
curl -X GET "https://firestore.googleapis.com/v1/projects/wastewise-6e82b/databases/(default)/documents"
```

### 5. Temporary Workarounds
If Firebase continues to fail:
1. **Offline Mode**: The app now handles offline scenarios better
2. **Retry Logic**: Automatic retries for failed requests
3. **Fallback UI**: Graceful degradation when offline

## Next Steps
1. Run the app and check the debug panel
2. Note the specific error messages
3. Try the solutions above
4. If issues persist, check Firebase project settings

## Debug Panel Information
The debug panel shows:
- ✅ **Connection Status**: Firebase connection test result
- 👤 **User Info**: Current authentication state
- 🌐 **Network Status**: Internet connectivity details
- ⏰ **Last Check**: When the connection was last tested

Use this information to identify the root cause of connection issues.
