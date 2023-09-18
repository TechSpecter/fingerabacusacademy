FROM debian:11 as base
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN apt-get update \
 && apt-get install -y \
    bash-completion \
    apt-transport-https \ 
    build-essential \
    ca-certificates \
    dnsutils \
    gnupg \
    fzf \
    sudo \
    curl \
    fzf \
    jq \
    bat \
    wget \
    git \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /tmp/
ARG DEST=/usr/local/bin

# Install tmux - terminal multiplexer
ARG TMUXVER=3.3a
RUN curl -fsSL "https://github.com/tmux/tmux/releases/download/$TMUXVER/tmux-$TMUXVER.tar.gz" | tar -xzf - \
  && cd "tmux-$TMUXVER" && ./configure && make && make install

# Install nvim from release deb distribution
ARG NVIMVER=0.9.2
RUN cd /tmp/ \
  && curl -sLO https://github.com/neovim/neovim/releases/download/v${NVIMVER}/nvim-linux64.deb \
  && apt install ./nvim-linux64.deb

# Install specific Node.js
ARG NODEVER=lts
RUN curl -fsSL "https://deb.nodesource.com/setup_$NODEVER.x" | bash - && apt-get install -y nodejs

# Install glow - terminal based Markdown rendering
ARG GLOWVER=1.5.1
RUN curl -fsSLO "https://github.com/charmbracelet/glow/releases/download/v${GLOWVER}/glow_${GLOWVER}_amd64.deb" && dpkg -i "./glow_${GLOWVER}_amd64.deb"

# Install yq - YAML query tool
ARG YQVER=4.35.1
RUN curl -fsSL "https://github.com/mikefarah/yq/releases/download/v${YQVER}/yq_linux_amd64" -o "$DEST/yq" && chmod +x "$DEST/yq"

# Install gitui - a git TUI
ARG GITUIVER=0.24.3
RUN curl -fsSL "https://github.com/extrawurst/gitui/releases/download/v${GITUIVER}/gitui-linux-musl.tar.gz" | tar -C "$DEST" -xzf -

# Install lf - a terminal file manager
ARG LFVER=31
RUN curl -fsSL "https://github.com/gokcehan/lf/releases/download/r${LFVER}/lf-linux-amd64.tar.gz" | tar -C "$DEST" -xzf - lf

# Install shfmt - shell script formatter
ARG SHFMTVER=3.7.0
RUN curl -fsSL "https://github.com/mvdan/sh/releases/download/v${SHFMTVER}/shfmt_v${SHFMTVER}_linux_amd64" -o "$DEST/shfmt" && chmod +x "$DEST/shfmt"

# Clean up temp dir
RUN rm -rf /tmp/*

# Set up non-root user
ARG USERNAME=rahul
RUN adduser \
  --quiet \
  --disabled-password \
  --shell /bin/bash \
  --home /home/$USERNAME \
  --gecos "Dev User" \
  $USERNAME \
  && chown $USERNAME:$USERNAME /tmp/

RUN mkdir /home/$USERNAME/.npm-global \
  && chown $USERNAME:$USERNAME /home/$USERNAME/.npm-global

USER $USERNAME
WORKDIR /home/$USERNAME
ENV TERM xterm-256color

# Install global npm modules for Node.js
RUN npm config set prefix "/home/$USERNAME/.npm-global"
RUN npm install -g \
    url-decode-encode-cli \
    pnpm

# Install ijq
ARG IJQVER=0.4.0
RUN curl \
    --silent \
    --location \
    --url "https://git.sr.ht/~gpanders/ijq/refs/download/v$IJQVER/ijq-$IJQVER-linux-amd64.tar.gz" \
    | tar \
      --extract \
      --gunzip \
      --file - \
      --directory /home/$USERNAME/bin/ \
      --strip-components 1 \
      --wildcards \
      ijq-$IJQVER/ijq

# Off we go - based on tmux, the terminal multiplexer
CMD ["tmux", "-u", "new", "-s", "main"]