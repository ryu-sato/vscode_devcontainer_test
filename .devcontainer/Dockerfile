# 下の Dockerfile をベースに volume mount するディレクトリを mkdir && chown するようにした。
# ref. https://github.com/microsoft/vscode-dev-containers/blob/772ae22f59b818b2e023e6e45475937a38cc4853/containers/ruby-rails/.devcontainer/Dockerfile
# [Choice] Ruby version: 2, 2.7, 2.6, 2.5
ARG VARIANT=2
FROM mcr.microsoft.com/vscode/devcontainers/ruby:${VARIANT}

# Set timezone.
ENV TZ="Asia/Tokyo"

# Install Rails.
RUN gem install rails webdrivers

# Default value to allow debug server to serve content over GitHub Codespace's port forwarding service.
# The value is a comma-separated list of allowed domains.
ENV RAILS_DEVELOPMENT_HOSTS=".githubpreview.dev"

ARG NODE_VERSION="lts/*"
RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"

# [Optional] Comment/Uncomment this section to avoid/install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends graphviz

# [Optional] Uncomment this line to install additional gems.
# RUN gem install <your-gem-names-here>

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1
