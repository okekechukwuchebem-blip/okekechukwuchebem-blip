<<<<<<< HEAD
# Cybersecurity Journey

Hi, I'm OXPHISHHUTER but my real name is OKEKE HILARY. I'm transitioning into cybersecurity with a focus on GRC, SOC Analysis, and Penetration Testing. My goal is to be a well-rounded security professional by 2027.

## What I'm Learning
- GRC: NIST CSF, ISO 27001, Risk Assessment, Compliance (NDPA, CBN guidelines)
- SOC Operations: Wazuh SIEM, threat detection, incident response, log analysis
- Penetration Testing: Kali Linux, network scanning, vulnerability assessment

## Projects
- Password Generator – A Python script for generating secure passwords
- SOC Lab Setup – Building a home SOC lab with VirtualBox, Kali Linux, and Wazuh SIEM
- Risk Management Guide – Practical risk analysis framework for Nigerian banks

## Tools & Tech
Python | Bash | Kali Linux | Wazuh | VirtualBox | Vim | VS Code | Termux

## Daily Learning
- GRC lessons (daily at 2 PM)
- Python (Mon/Wed/Fri at 7 PM)
- Bash (Tue/Thu/Sat at 7 PM)

##Connect
-linkedIn: https://www.linkedin.com/in/hilary-okeke-878a6b406
=======
# Cybersecurity Journey - Password Automation & Logging

A comprehensive password automation and security management framework with extensive logging capabilities for audit trails and compliance.

## 📋 Overview

This project provides:
- **Secure password generation** with configurable complexity levels
- **Automated password rotation** with full audit logging
- **Policy enforcement** for password strength and compliance
- **Scheduled rotations** for multiple systems
- **Security event monitoring** and alerting
- **Comprehensive logging** that never exposes sensitive data
- **Audit trails** for compliance and forensics

## 🗂️ Project Structure

```
cybersecurity-journey/
├── docs/
│   └── PASSWORD_SECURITY_GUIDE.md      # Comprehensive security guide
├── src/
│   ├── password_manager.py             # Core password automation module
│   ├── advanced_features.py            # Advanced security features
│   └── example_usage.py                # Usage examples and demos
├── config/
│   └── rotation_config.yaml            # Configuration file
├── logs/                               # Log files (generated)
├── requirements.txt                    # Dependencies
└── README.md                           # This file
```

## 🚀 Getting Started

### Installation

```bash
# Clone or navigate to the project
cd cybersecurity-journey

# Install dependencies
pip install -r requirements.txt
```

### Quick Start

```bash
# Run the demo
python src/example_usage.py
```

This will:
1. Generate passwords with different complexity levels
2. Validate password strength
3. Perform automated password rotations
4. Create audit logs
5. Display examples of all features

## 💻 Usage Examples

### Basic Password Generation

```python
from src.password_manager import create_password_automation_system

logger, generator, manager = create_password_automation_system()

# Generate a high-complexity password
password = generator.generate(complexity="high")

# Validate password strength
is_valid, strength = generator.validate_strength(password)
print(f"Password strength: {strength}")
```

### Automated Password Rotation

```python
# Rotate password with logging
result = manager.rotate_password(
    system="database",
    target="prod_db_01",
    user="dba_team",
    complexity="critical"
)

if result["success"]:
    print(f"Rotation completed in {result['duration']:.2f}s")
else:
    print(f"Rotation failed: {result['error']}")
```

### Scheduled Rotations

```python
from src.advanced_features import ScheduledPasswordRotation, PasswordPolicy

policy = PasswordPolicy(logger)
scheduled = ScheduledPasswordRotation(manager, logger, policy)

# Schedule rotation every 30 days
scheduled.schedule_rotation("database", "prod_db", interval_hours=720)

# Execute due rotations
results = scheduled.execute_due_rotations(user="automation")
print(f"Executed: {results['successful']}/{results['total']}")
```

### Security Monitoring

```python
from src.advanced_features import SecurityAuditLog

audit = SecurityAuditLog(logger)

# Log security events
audit.log_failed_login_attempt("user123", "production_db", attempt_count=3)
audit.log_administrative_action("admin001", "password_reset", "user456")

# Get security summary
summary = audit.get_security_summary(hours=24)
print(f"Failed logins in last 24h: {summary['failed_logins']}")
```

## 🔐 Security Features

### Password Complexity Levels

| Level | Length | Requirements | Use Case |
|-------|--------|--------------|----------|
| Low | 12 | Letters + digits | Development |
| Medium | 16 | Letters + digits + 4 special | Staging |
| High | 20 | Letters + digits + 8 special | Production |
| Critical | 24 | Letters + digits + extended special | Critical systems |

### What Gets Logged

✅ **SAFE TO LOG:**
- Timestamp of rotation events
- System and target identifiers
- Username of person performing action
- Success/failure status
- Duration of operation
- Password strength metadata
- Policy violations

❌ **NEVER LOGGED:**
- Actual passwords
- Password hashes or derivatives
- Encryption keys
- Full API tokens
- Sensitive configuration

### Logging Levels

- **CRITICAL**: Security breaches, unauthorized access
- **ERROR**: Rotation failures, authentication errors
- **WARNING**: Policy violations, unusual patterns
- **INFO**: Successful rotations, routine operations
- **DEBUG**: Detailed operation steps (dev only)

## 📊 Log Files

The system creates three separate log files:

1. **password_audit.log** - All password operations and access attempts
2. **password_rotation.log** - Detailed rotation events
3. **password_errors.log** - Errors and security issues

Each file:
- Auto-rotates at 10MB
- Keeps 5 backup copies
- Uses ISO 8601 timestamps
- Never contains sensitive data

## ⚙️ Configuration

Edit `config/rotation_config.yaml` to customize:

```yaml
password_generation:
  default_complexity: high
  min_length: 16

password_policy:
  max_age_days: 90
  failed_attempts_limit: 5

rotation_schedule:
  database:
    interval: 720  # 30 days
```

## 🔍 Compliance & Standards

This framework implements best practices from:
- **NIST SP 800-63**: Digital Identity Guidelines
- **PCI DSS**: Payment Card Industry Security Standards
- **SOC 2**: Security & Availability Trust Service Criteria
- **OWASP**: Top 10 Security Guidelines

## 📈 Audit Trail Features

- **Immutable logs**: Cryptographically signed audit trail
- **Retention policies**: Configurable retention periods
- **Searchable logs**: Export to JSON for analysis
- **Compliance ready**: Pre-formatted for regulatory audits

## 🧪 Testing

```bash
# Run all examples
python src/example_usage.py

# Run advanced features demo
python src/advanced_features.py

# View generated logs
cat logs/password_audit.log
cat logs/password_rotation.log
cat logs/password_errors.log
```

## 📝 API Reference

### PasswordLogger

```python
log_rotation_start(system, user, target)
log_rotation_success(system, user, target, duration)
log_rotation_failure(system, user, target, error)
log_password_generation(length, complexity)
log_access_attempt(user, system, success)
log_policy_violation(violation_type, details)
```

### PasswordGenerator

```python
generate(complexity="high") -> str
validate_strength(password) -> (bool, str)
```

### PasswordRotationManager

```python
rotate_password(system, target, user, complexity, verify_callback) -> dict
get_rotation_history(system=None, limit=10) -> list
export_audit_log(filename) -> None
```

### ScheduledPasswordRotation

```python
schedule_rotation(system, target, interval_hours)
get_due_rotations() -> list
execute_due_rotations(user="automation") -> dict
```

### SecurityAuditLog

```python
log_failed_login_attempt(user, system, attempt_count)
log_unauthorized_access_attempt(user, resource, action)
log_administrative_action(admin_user, action, target)
get_security_summary(hours=24) -> dict
alert_if_suspicious(threshold=5)
```

## 🛡️ Best Practices

1. **Never store passwords in code** - Use environment variables or vaults
2. **Enable log rotation** - Prevent disk space issues
3. **Encrypt logs** - Protect sensitive audit trails
4. **Monitor failures** - Set up alerts for suspicious activity
5. **Regular audits** - Review logs periodically
6. **Test recovery** - Practice password recovery procedures
7. **Backup vaults** - Ensure critical credentials are backed up
8. **Update policies** - Adjust complexity as threats evolve

## 🔗 Integration Examples

### With HashiCorp Vault

```python
# Store rotated password in Vault
vault_client.secrets.kv.v2.create_or_update_secret_version(
    path=f"production/database",
    secret_dict={"password": new_password}
)
manager.logger.audit_logger.info(f"Password stored in Vault")
```

### With AWS Secrets Manager

```python
# Store in AWS
secrets_client.put_secret_value(
    SecretId="prod/database",
    SecretString=new_password
)
manager.logger.audit_logger.info(f"Password stored in AWS Secrets Manager")
```

## 📚 Further Reading

- See [PASSWORD_SECURITY_GUIDE.md](docs/PASSWORD_SECURITY_GUIDE.md) for detailed security guidelines
- Review NIST SP 800-132 for password hashing recommendations
- Check OWASP Guidelines for authentication best practices

## 🤝 Contributing

Contributions are welcome! Areas for enhancement:
- Integration with external vault services
- Machine learning-based anomaly detection
- Multi-factor authentication support
- Hardware security module (HSM) integration
- Blockchain-based audit trail

## 📄 License

This project is provided as-is for educational and enterprise security purposes.

## ⚠️ Security Notice

This framework is designed for production password management. However:
- Always test in non-production environments first
- Ensure proper access controls are in place
- Review logs regularly for security issues
- Keep dependencies updated
- Never commit secrets to version control

## 📞 Support

For issues or questions:
1. Check the documentation in `docs/`
2. Review examples in `src/example_usage.py`
3. Check log files for error details
4. Examine configuration in `config/rotation_config.yaml`

---

**Last Updated**: 2026-05-24
**Version**: 1.0.0
>>>>>>> 0ad1dd2 (feat: Add password rotation configuration and security guide)
