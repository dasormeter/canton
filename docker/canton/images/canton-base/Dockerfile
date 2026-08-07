# Copyright (c) 2024 Digital Asset (Switzerland) GmbH and/or its affiliates. All rights reserved.
# SPDX-License-Identifier: Apache-2.0

FROM europe-docker.pkg.dev/da-images/public/docker/da-base-image:full-1.0.12@sha256:134d8e3391d66c893115a35b85dfc5708616cb846cec05918c8228310f83b867

# Create repeatable-migrations directory
WORKDIR /app/repeatable-migrations
WORKDIR /app

COPY target/canton .

COPY LICENSE.txt monitoring.conf parameters.conf storage.conf entrypoint.sh bootstrap-entrypoint.sc tools.sh logback.xml /app/

ARG base_version=latest

LABEL org.opencontainers.image.ref.name=canton-base:${base_version}

# Add label for security scanners, compliance tools, and auditing purposes
LABEL org.opencontainers.image.base.name="europe-docker.pkg.dev/da-images/public/docker/da-base-image:full-1.0.7"
LABEL org.opencontainers.image.base.digest="sha256:fb788e6f89eb6f28cee53dfc6c707d2d39aedcbc201d5c0c416e42b3da6f4fcd"

# point entrypoint to the amulet executable
ENTRYPOINT ["/usr/bin/tini", "--", "/app/entrypoint.sh"]
