# Tiation Python SDK

<div align="center">
  <img src="https://via.placeholder.com/800x200/1a1a2e/16213e?text=Tiation+Python+SDK" alt="Tiation Python SDK Banner" />
  
  <h3>Official Python SDK for Tiation APIs</h3>
  
  [![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/tiation/tiation-python-sdk)
  [![Python](https://img.shields.io/badge/python-3.8+-brightgreen.svg)](https://python.org)
  [![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
  [![Enterprise](https://img.shields.io/badge/enterprise-ready-purple.svg)](https://github.com/tiation)
</div>

## 🌟 Overview

The Tiation Python SDK provides a comprehensive, enterprise-grade interface for interacting with all Tiation services. Built with modern Python practices and designed for scalability, it offers seamless integration with your Python applications.

## ✨ Features

- **🚀 Full API Coverage**: Complete access to all Tiation services
- **🔒 Enterprise Security**: Built-in authentication and rate limiting
- **📊 Real-time Analytics**: Live metrics and business intelligence
- **🔄 Async Support**: Full asyncio support for high-performance applications
- **🛡️ Type Safety**: Complete type hints and mypy compatibility
- **📚 Rich Documentation**: Comprehensive docs with examples
- **⚡ High Performance**: Optimized for speed and efficiency

## 📦 Installation

```bash
pip install tiation-sdk
```

## 🚀 Quick Start

```python
from tiation import TiationClient

# Initialize client
client = TiationClient(api_key="your_api_key")

# Get business analytics
analytics = client.analytics.get_metrics()
print(f"Total revenue: ${analytics.revenue}")

# Manage automation workflows
workflow = client.automation.create_workflow({
    "name": "Customer Onboarding",
    "trigger": "user_signup",
    "actions": ["send_welcome_email", "create_profile"]
})
```

## 📚 Documentation

### Authentication

```python
from tiation import TiationClient

# API Key authentication
client = TiationClient(api_key="your_api_key")

# OAuth2 authentication
client = TiationClient(
    client_id="your_client_id",
    client_secret="your_client_secret",
    oauth_token="your_oauth_token"
)
```

### Core Services

#### Analytics & Metrics
```python
# Get business metrics
metrics = client.analytics.get_metrics(
    start_date="2024-01-01",
    end_date="2024-12-31"
)

# Real-time dashboard data
dashboard = client.analytics.get_dashboard()
```

#### Automation Workflows
```python
# List workflows
workflows = client.automation.list_workflows()

# Execute workflow
result = client.automation.execute_workflow(
    workflow_id="workflow_123",
    parameters={"user_id": "user_456"}
)
```

#### Content Management
```python
# Create content
content = client.cms.create_content({
    "title": "New Product Launch",
    "body": "Exciting new features available now!",
    "category": "announcements"
})

# Update content
client.cms.update_content(content.id, {"status": "published"})
```

### Advanced Features

#### Async Support
```python
import asyncio
from tiation import AsyncTiationClient

async def main():
    client = AsyncTiationClient(api_key="your_api_key")
    
    # Async API calls
    metrics = await client.analytics.get_metrics()
    workflows = await client.automation.list_workflows()
    
    # Concurrent requests
    results = await asyncio.gather(
        client.analytics.get_dashboard(),
        client.cms.list_content(),
        client.automation.get_status()
    )

asyncio.run(main())
```

#### Error Handling
```python
from tiation import TiationClient, TiationError, RateLimitError

try:
    client = TiationClient(api_key="your_api_key")
    result = client.analytics.get_metrics()
except RateLimitError as e:
    print(f"Rate limit exceeded: {e.retry_after} seconds")
except TiationError as e:
    print(f"API error: {e.message}")
```

## 🔧 Configuration

### Environment Variables
```bash
export TIATION_API_KEY="your_api_key"
export TIATION_BASE_URL="https://api.tiation.com"
export TIATION_TIMEOUT=30
```

### Configuration File
```python
from tiation import TiationClient

client = TiationClient(
    api_key="your_api_key",
    base_url="https://api.tiation.com",
    timeout=30,
    max_retries=3,
    retry_delay=1.0
)
```

## 🏢 Enterprise Features

### Batch Operations
```python
# Batch create content
contents = client.cms.batch_create([
    {"title": "Article 1", "body": "Content 1"},
    {"title": "Article 2", "body": "Content 2"}
])

# Batch analytics
metrics = client.analytics.batch_metrics([
    {"metric": "revenue", "period": "monthly"},
    {"metric": "users", "period": "daily"}
])
```

### Webhook Integration
```python
from tiation.webhooks import WebhookProcessor

processor = WebhookProcessor(secret="your_webhook_secret")

@processor.event("user.created")
def handle_user_created(event):
    print(f"New user: {event.data.email}")
    # Trigger welcome workflow
    client.automation.execute_workflow(
        "welcome_workflow",
        {"user_id": event.data.id}
    )
```

## 🧪 Testing

```bash
# Run tests
pytest tests/

# Run with coverage
pytest --cov=tiation tests/

# Run specific test
pytest tests/test_analytics.py::test_get_metrics
```

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### Development Setup

```bash
# Clone repository
git clone https://github.com/tiation/tiation-python-sdk.git
cd tiation-python-sdk

# Install development dependencies
pip install -e ".[dev]"

# Run tests
pytest
```

## 📞 Support

- **Documentation**: [Python SDK Docs](https://docs.tiation.com/python-sdk)
- **API Reference**: [API Documentation](https://api.tiation.com/docs)
- **Issues**: [GitHub Issues](https://github.com/tiation/tiation-python-sdk/issues)
- **Enterprise Support**: [tiatheone@protonmail.com](mailto:tiatheone@protonmail.com)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<div align="center">
  <p>Built with ❤️ by <a href="https://github.com/tiation">Tiation</a></p>
  <p>Enterprise-grade Python SDK for modern businesses</p>
</div>
