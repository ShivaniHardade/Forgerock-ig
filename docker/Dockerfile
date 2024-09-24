FROM gcr.io/forgerock-io/java-17:latest

# Default install directory for IG
ENV INSTALL_DIR /opt/ig

# Copy application files
COPY --chown=forgerock:root . "${INSTALL_DIR}"

# Default home for IG config
ENV IG_INSTANCE_DIR /var/ig

# Prepare directories and set permissions
RUN mkdir -p "${IG_INSTANCE_DIR}" \
    && chown -R forgerock:root "${IG_INSTANCE_DIR}" "${INSTALL_DIR}" \
    && chmod -R g+rwx "${IG_INSTANCE_DIR}" "${INSTALL_DIR}" \
    && chmod +x "${INSTALL_DIR}/bin/start.sh"  # Make start.sh executable

# Use a non-root user to run the application
USER 11111

# Use the full path for ENTRYPOINT
ENTRYPOINT ["${INSTALL_DIR}/bin/start.sh", "${IG_INSTANCE_DIR}"]
