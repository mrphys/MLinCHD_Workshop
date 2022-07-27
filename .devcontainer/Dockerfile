FROM tensorflow/tensorflow:2.9.1-gpu

ARG DEBIAN_FRONTEND=noninteractive

# Create non-root user.
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME && \
    useradd --uid $USER_UID --gid $USER_GID -m $USERNAME && \
    # Add user to sudoers.
    apt-get update && \
    apt-get install -y sudo && \
    echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME && \
    chmod 0440 /etc/sudoers.d/$USERNAME && \
    # Change default shell to bash.
    usermod --shell /bin/bash $USERNAME

# Other packages.
RUN apt-get update && \
    apt-get install -y git-all texlive-latex-recommended texlive-latex-extra texlive-fonts-recommended dvipng cm-super
RUN pip install matplotlib ipykernel
