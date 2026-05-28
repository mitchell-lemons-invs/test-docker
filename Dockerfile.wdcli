FROM ubuntu:22.04

# Install Node.js and other runtime dependencies
RUN apt-get update && apt-get install -y \
    curl \
    ca-certificates \
    nodejs \
    npm \
    && rm -rf /var/lib/apt/lists/*

# Copy the entire wdcli folder to a sensible location
COPY wdcli/ /opt/wdcli/

# Make the binary executable (permissions can get lost in copy)
RUN chmod +x /opt/wdcli/bin/wdcli

# Symlink it so `wdcli` works as a command from anywhere
RUN ln -s /opt/wdcli/bin/wdcli /usr/local/bin/wdcli

# Verify it works at build time
RUN wdcli version

CMD ["/bin/bash"]