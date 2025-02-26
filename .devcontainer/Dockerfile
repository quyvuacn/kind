FROM golang:1.21

# Tạo user non-root
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Cài đặt các dependencies
RUN apt-get update && apt-get install -y \
    sudo \
    git \
    curl \
    apt-transport-https \
    ca-certificates \
    gnupg \
    lsb-release \
    && rm -rf /var/lib/apt/lists/*

# Tạo user và thêm vào sudo group
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Tạo và set quyền cho workspace
WORKDIR /workspace
RUN chown $USERNAME:$USERNAME /workspace

# Thêm user vào docker group
RUN groupadd docker \
    && usermod -aG docker $USERNAME

# Chuyển sang user non-root
USER $USERNAME