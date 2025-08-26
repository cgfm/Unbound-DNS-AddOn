# Home Assistant Add-on: Unbound DNS

A simple and reliable DNS resolver for Home Assistant using Unbound.

![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]
![Supports armv7 Architecture][armv7-shield]

## About

This add-on provides a local DNS resolver using Unbound, a validating, recursive, caching DNS resolver. It's designed to be simple, secure, and fast.

## Features

- **Simple Configuration**: Works out of the box with minimal setup
- **Custom Configuration**: Use your own `unbound.conf` file for advanced settings
- **Multiple Architectures**: Supports amd64, aarch64, and armv7
- **Secure**: No unnecessary features, just DNS resolution
- **Fast**: Caching resolver for improved performance

## Installation

1. Navigate to Supervisor > Add-on Store > ⋮ > Repositories
2. Add this repository: `https://github.com/cgfm/Unbound-DNS-AddOn`
3. Refresh the add-on store
4. Install the "Unbound DNS" add-on
5. Start the add-on

## Configuration

### Basic Setup

The add-on works with default settings out of the box:

- Listens on port `5353` (both TCP and UDP)
- Allows access from all networks
- Uses Cloudflare DNS (1.1.1.1) as upstream

### Custom Configuration

For advanced users, you can provide your own `unbound.conf` file:

1. Place your custom `unbound.conf` file in the add-on's configuration directory
2. The add-on will automatically detect and use it on restart

The configuration directory path is: `/config/unbound/unbound.conf`

### Example Custom Configuration

```
server:
    interface: 0.0.0.0
    port: 5353
    access-control: 192.168.1.0/24 allow
    cache-min-ttl: 300
    cache-max-ttl: 86400
    do-ip6: no

forward-zone:
    name: "."
    forward-addr: 1.1.1.1
    forward-addr: 8.8.8.8
```

## Usage

After installation:

1. Configure your network devices to use your Home Assistant IP address with port `5353` as DNS server
2. Or configure Home Assistant's network settings to use `127.0.0.1:5353` as DNS resolver

## Support

- [GitHub Issues](https://github.com/cgfm/Unbound-DNS-AddOn/issues)
- [Home Assistant Community](https://community.home-assistant.io/)

## License

MIT License - see [LICENSE](https://github.com/cgfm/Unbound-DNS-AddOn/blob/main/LICENSE)

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[armv7-shield]: https://img.shields.io/badge/armv7-yes-green.svg