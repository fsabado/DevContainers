# Start from the universal base image
FROM mcr.microsoft.com/devcontainers/universal:2

# Use bash for RUN blocks that rely on bash-isms (&&, [[ ]], etc.)
SHELL ["/bin/bash", "-lc"]

# # Base OS packages (single layer) + cleanup in SAME layer
RUN apt-get update \
 && apt-get install -y --no-install-recommends \
      curl wget git unzip zip less tree htop jq lsb-release \
      build-essential ca-certificates bash-completion direnv \
 && rm -rf /var/lib/apt/lists/*

#  # Update and install common tools
RUN echo 'eval "$(direnv hook bash)"' >> /etc/bash.bashrc \
    && echo 'eval "$(direnv hook zsh)"' >> /etc/zsh/zshrc

# # Install additional packages, tools, or SDKs
RUN curl -fsSL https://d2lang.com/install.sh | sh -s --

# ==== SWITCH TO USER ====

USER codespace

# Suppress VS Code devcontainer welcome prompts for all users
# (Putting these under /usr/local/etc applies container-wide.)
RUN mkdir -p $HOME/.config/vscode-dev-containers/ \
    && touch $HOME/.config/vscode-dev-containers/first-run-notice-already-displayed \
    && touch $HOME/.config/vscode-dev-containers/conda-notice-already-displayed