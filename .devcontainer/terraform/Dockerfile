FROM mcr.microsoft.com/vscode/devcontainers/base:debian

# Install Terraform
RUN apt-get update \
    && apt-get install -y --no-install-recommends ca-certificates curl gnupg \
    && install -m 0755 -d /etc/apt/keyrings \
    && curl -fsSL https://apt.releases.hashicorp.com/gpg \
       | gpg --dearmor -o /etc/apt/keyrings/hashicorp-archive-keyring.gpg \
    && chmod a+r /etc/apt/keyrings/hashicorp-archive-keyring.gpg \
    && echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(. /etc/os-release && echo "$VERSION_CODENAME") main" \
       > /etc/apt/sources.list.d/hashicorp.list \
    && apt-get update \
    && apt-get install -y --no-install-recommends terraform \
    && rm -rf /var/lib/apt/lists/*
# Optional: Install tflint and terraform-docs
RUN apt-get update \
    && apt-get install -y --no-install-recommends unzip \
    && curl -fsSL -o /tmp/tflint.zip https://github.com/terraform-linters/tflint/releases/latest/download/tflint_linux_amd64.zip \
    && unzip -o /tmp/tflint.zip -d /usr/local/bin \
    && chmod 0755 /usr/local/bin/tflint \
    && curl -fsSL https://github.com/terraform-docs/terraform-docs/releases/download/v0.24.0/terraform-docs-v0.24.0-linux-amd64.tar.gz \
       | tar -xz -C /usr/local/bin \
    && chmod 0755 /usr/local/bin/terraform-docs \
    && rm -f /tmp/tflint.zip \
    && rm -rf /var/lib/apt/lists/*
    