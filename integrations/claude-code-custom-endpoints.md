# Claude Code Custom Server Endpoints Configuration

This document covers how to configure Claude Code to work with custom server endpoints, particularly for using alternative AI models through API-compatible services.

## Z.AI GLM-4.5 Integration

Z.AI provides an Anthropic API-compatible endpoint that allows Claude Code to communicate with GLM-4.5 models seamlessly without any code modifications.

### Prerequisites

1. Obtain an API key from Z.AI: https://z.ai/manage-apikey/apikey-list
2. Have Claude Code installed on your system

### Configuration Methods

#### Method 1: Script-Based Setup (Recommended)

Download and run the official configuration script:

```bash
curl -O "http://bigmodel-us3-prod-marketplace.cn-wlcb.ufileos.com/1753683755292-30b3431f487b4cc1863e57a81d78e289.sh?ufileattname=claude_code_prod_zai.sh"

# Make the script executable and run it
chmod +x claude_code_prod_zai.sh
./claude_code_prod_zai.sh
```

#### Method 2: Manual Environment Variable Configuration

Set the following environment variables in your shell configuration file (`.bashrc`, `.zshrc`, etc.):

```bash
export ANTHROPIC_BASE_URL=https://api.z.ai/api/anthropic
export ANTHROPIC_AUTH_TOKEN={YOUR_API_KEY}
```

Replace `{YOUR_API_KEY}` with your actual API key from Z.AI.

### Verification

After configuration:
1. Restart your terminal or source your shell configuration file
2. Launch Claude Code
3. Grant file access permissions when prompted
4. The tool should now be using GLM-4.5 models through Z.AI's endpoint

### Benefits

- **No Code Modifications**: Works with existing Claude Code installation
- **API Compatibility**: Z.AI provides full Anthropic API compatibility
- **Alternative Model Access**: Access to GLM-4.5 models through familiar interface

### Troubleshooting

1. **Environment Variables Not Recognized**
   - Ensure you've restarted your terminal or run `source ~/.bashrc` (or appropriate config file)
   - Verify variables are set: `echo $ANTHROPIC_BASE_URL`

2. **Authentication Errors**
   - Double-check your API key is correct
   - Ensure the API key has proper permissions on Z.AI platform

3. **Connection Issues**
   - Verify network connectivity to `https://api.z.ai`
   - Check if corporate firewall/proxy might be blocking the connection

## Generic Custom Endpoint Configuration

The same pattern can be used for other API-compatible services:

```bash
export ANTHROPIC_BASE_URL=https://your-custom-endpoint.com/api
export ANTHROPIC_AUTH_TOKEN=your-auth-token
```

This makes Claude Code highly flexible for integrating with various AI model providers that offer Anthropic-compatible APIs.

## Security Considerations

- Never commit API keys to version control
- Use environment variables or secure credential management systems
- Regularly rotate API keys
- Monitor API usage for unauthorized access

## Additional Resources

- [Z.AI Documentation](https://docs.z.ai)
- [Claude Code Official Documentation](https://docs.anthropic.com/en/docs/claude-code)