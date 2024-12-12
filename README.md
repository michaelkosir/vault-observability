# Vault Observability Demo
This repository provides a demo of observability for HashiCorp Vault. It is not meant to be exact production settings for logging/monitoring Vault.

# Observability
Observability is the ability to measure the internal states of a system by examining its outputs. In the context of HashiCorp Vault, the key outputs to examine are log files, telemetry metrics, and data scraped from API endpoints. The following items are being captured for Vault Observability:

- Vault Operational Logs
- Vault Audit Logs
- Vault Telemetry
- Host Metrics

# Versions
As this repository is for demo purposes, I have locked software versions to verify repeatability. Update these at your own risk.

```
vault    = 1.18.2-1
elastic  = 8.16.1
grafana  = 11.4.0
```

# Usage
### Terraform (AWS)
Use an AMI with Ubuntu 24.04 (Noble). Provide enough Disk, Memory, and CPU for the demo.
```terraform
resource "aws_instance" "example" {
  ...
  
  user_data = file("cloud-config.yml")
}
```

### Multipass
[Multipass](https://multipass.run/install) orchestrates virtual Ubuntu instances.
```shell
cd ...

multipass launch -n vault --cloud-init cloud-config.yml -d 25G -m 8G -c 4

multipass info vault
multipass shell vault
```
