FROM mcr.microsoft.com/vscode/devcontainers/base:ubuntu

# Install Terraform
RUN apt-get update && apt-get install -y \
    gnupg software-properties-common curl wget \
    && curl -fsSL https://apt.releases.hashicorp.com/gpg | apt-key add - \
    && apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main" \
    && apt-get update && apt-get install -y terraform

# Optional: Install tflint and terraform-docs
RUN curl -sSL -o /usr/local/bin/tflint https://github.com/terraform-linters/tflint/releases/latest/download/tflint_linux_amd64.zip \
    && unzip /usr/local/bin/tflint -d /usr/local/bin/ \
    && chmod +x /usr/local/bin/tflint \
    && curl -sSL -o /usr/local/bin/terraform-docs https://github.com/terraform-docs/terraform-docs/releases/latest/download/terraform-docs-linux-amd64 \
    && chmod +x /usr/local/bin/terraform-docs
    