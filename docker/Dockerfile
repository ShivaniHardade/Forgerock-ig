FROM gcr.io/forgerock-io/java-17:latest

# Define installation and instance directories as environment variables
ENV INSTALL_DIR=/opt/ig \
    IG_INSTANCE_DIR=/var/ig

# Copy application files to the installation directory
COPY --chown=forgerock:root . "${INSTALL_DIR}"

# Ensure proper permissions and make the startup script executable
RUN mkdir -p "${IG_INSTANCE_DIR}" \
    && chown -R forgerock:root "${IG_INSTANCE_DIR}" "${INSTALL_DIR}" \
    && chmod -R g+rwx "${IG_INSTANCE_DIR}" "${INSTALL_DIR}" \
    && chmod +x "${INSTALL_DIR}/bin/start.sh"

# Switch to a non-root user for better security
USER 11111

# Use an array form ENTRYPOINT to avoid shell interpretation issues
ENTRYPOINT ["/opt/ig/bin/start.sh", "/var/ig"]
