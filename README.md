# Solarwinds-MCP-for-Claude
This is a enterprise-grade MCP server that transforms Claude into a powerful SolarWinds management assistant, capable of handling everything from simple queries to complex infrastructure management tasks!
# SolarWinds MCP Server

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js Version](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-blue)](https://www.typescriptlang.org/)

A comprehensive Model Context Protocol (MCP) server that provides seamless integration between Claude AI and SolarWinds Orion platform for advanced network monitoring and management.

## 🌟 Features

- **Real-time Monitoring** - Live polling with event notifications
- **Advanced Queries** - Full SWQL (SolarWinds Query Language) support with intelligent caching
- **Alert Management** - View, acknowledge, and bulk process alerts
- **Performance Analytics** - Node performance metrics and trending
- **Infrastructure Reporting** - Comprehensive health, performance, and alert reports
- **Network Topology** - Discover and visualize network relationships
- **Bulk Operations** - Mass alert acknowledgment and batch processing
- **Production Ready** - Enterprise-grade security, logging, and error handling

## 🚀 Quick Start

### Prerequisites
- Node.js 18.0 or higher
- SolarWinds Orion platform with API access
- Claude Desktop application

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/solarwinds-mcp-server.git
   cd solarwinds-mcp-server
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Build the project:**
   ```bash
   npm run build
   ```

4. **Configure Claude Desktop:**
   
   Add to your Claude Desktop configuration file:
   
   **macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
   **Windows**: `%APPDATA%/Claude/claude_desktop_config.json`

   ```json
   {
     "mcpServers": {
       "solarwinds": {
         "command": "node",
         "args": ["/full/path/to/solarwinds-mcp-server/build/index.js"],
         "env": {}
       }
     }
   }
   ```

5. **Start using with Claude:**
   ```
   Connect to SolarWinds at hostname: your-server.com, username: your-user, password: your-pass
   ```

## 📊 Available Tools

### Connection Management
- `connect_solarwinds` - Connect to SolarWinds Orion with enhanced features
- `test_connection` - Test connection status
- `start_polling` / `stop_polling` - Control real-time polling

### Node Monitoring
- `get_nodes` - List all monitored nodes
- `get_node_by_id` - Get specific node details
- `get_nodes_by_status` - Filter nodes by status (Up/Down/Warning)
- `get_node_performance` - Get performance metrics for specific nodes
- `get_node_neighbors` - Discover network topology

### Alert Management
- `get_alerts` - View active alerts with filtering
- `acknowledge_alert` - Acknowledge single alerts
- `acknowledge_multiple_alerts` - Bulk alert acknowledgment
- `get_alert_summary` - Alert statistics and trends

### Infrastructure Monitoring
- `get_volumes` - Monitor disk volume usage
- `get_applications` - Application performance monitoring
- `get_interfaces` - Network interface statistics
- `get_events` - System event tracking

### Reporting & Analytics
- `get_health_summary` - Overall infrastructure health
- `generate_report` - Comprehensive reports (health/performance/alerts/full)
- `get_custom_properties` - Node custom properties

### Advanced Operations
- `execute_swql` - Run custom SWQL queries
- `clear_cache` / `get_cache_stats` - Cache management

## 💡 Usage Examples

### Basic Health Check
```
Show me the overall health summary and any critical alerts
```

### Incident Response
```
Show me all down nodes and critical alerts from the last 2 hours
```

### Performance Analysis
```
Get performance metrics for node ID 123 over the last 24 hours
```

### Custom Queries
```
Execute this SWQL: SELECT TOP 10 NodeName, ResponseTime FROM Orion.Nodes WHERE Status = 1 ORDER BY ResponseTime DESC
```

### Bulk Operations
```
Acknowledge all critical alerts with message "Under investigation by NOC team"
```

For more examples, see [Usage Examples](docs/usage-examples.md).

## 📚 Documentation

- **[Deployment Guide](docs/deployment-guide.md)** - Production deployment and configuration
- **[Usage Examples](docs/usage-examples.md)** - Real-world scenarios and commands
- **[API Reference](docs/api-reference.md)** - Complete tool documentation
- **[Troubleshooting](docs/troubleshooting.md)** - Common issues and solutions
- **[Contributing](docs/contributing.md)** - Development and contribution guidelines

## 🔧 Configuration

### Environment Variables
```bash
export SOLARWINDS_HOSTNAME="your-solarwinds-server.com"
export SOLARWINDS_USERNAME="monitoring-user"
export SOLARWINDS_PASSWORD="secure-password"
export SOLARWINDS_PORT="17778"
export SOLARWINDS_PROTOCOL="https"
```

### Configuration File
Copy `config/config.example.json` to `config/config.json` and customize:

```json
{
  "solarwinds": {
    "hostname": "solarwinds.company.com",
    "username": "api-user",
    "password": "secure-password",
    "port": 17778,
    "protocol": "https",
    "ignoreSsl": false
  },
  "cache": {
    "enabled": true,
    "defaultTtl": 300000
  },
  "logging": {
    "level": "info",
    "file": "./logs/solarwinds-mcp.log"
  }
}
```

## 🐳 Docker Deployment

### Using Docker Compose
```bash
docker-compose up -d
```

### Manual Docker Build
```bash
docker build -t solarwinds-mcp-server .
docker run -d --name solarwinds-mcp \
  -e SOLARWINDS_HOSTNAME=your-server.com \
  -e SOLARWINDS_USERNAME=user \
  -e SOLARWINDS_PASSWORD=pass \
  -v $(pwd)/logs:/app/logs \
  solarwinds-mcp-server
```

## 🧪 Testing

```bash
# Run all tests
npm test

# Run tests with coverage
npm run test:coverage

# Run integration tests (requires test SolarWinds instance)
npm run test:integration
```

## 📈 Performance

- **Intelligent Caching** - Reduces API calls and improves response times
- **Connection Pooling** - Efficient resource utilization
- **Bulk Operations** - Process multiple items simultaneously
- **Real-time Polling** - Live updates without constant querying

## 🔒 Security

- **SSL/TLS Support** - Secure communications
- **Credential Management** - Environment variable and vault support
- **Access Control** - Dedicated service accounts recommended
- **Audit Logging** - Complete operation tracking

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](docs/contributing.md) for details.

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- **Issues**: [GitHub Issues](https://github.com/yourusername/solarwinds-mcp-server/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/solarwinds-mcp-server/discussions)
- **Documentation**: [Wiki](https://github.com/yourusername/solarwinds-mcp-server/wiki)

## 🙏 Acknowledgments

- [Model Context Protocol](https://github.com/modelcontextprotocol) by Anthropic
- [SolarWinds Orion Platform](https://www.solarwinds.com/orion-platform)
- Community contributors and testers

## 📊 Status

- ✅ Core functionality complete
- ✅ Advanced features implemented
- ✅ Production ready
- ✅ Comprehensive testing
- ✅ Documentation complete
- 🔄 Continuous improvements

---

**Made with ❤️ for the network monitoring community**
