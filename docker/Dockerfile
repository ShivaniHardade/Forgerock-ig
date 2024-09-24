# Use the base image for Java
FROM gcr.io/forgerock-io/java-17:latest

# Set environment variables
ENV IG_INSTANCE_DIR="/var/ig"
ENV INSTALL_DIR="/opt/ig"

# Copy files to the specified directory in the image
COPY --chown=forgerock:root . ${INSTALL_DIR}

# Prepare directories and set permissions
RUN mkdir -p "${IG_INSTANCE_DIR}" \
    && chown -R forgerock:root "${IG_INSTANCE_DIR}" "${INSTALL_DIR}" \
    && chmod -R g+rwx "${IG_INSTANCE_DIR}" "${INSTALL_DIR}" \
    && ls -la "${INSTALL_DIR}/bin" \
    && chmod +x "${INSTALL_DIR}/bin/start.sh"  # Make start.sh executable

# Define the command to run the application
CMD ["${INSTALL_DIR}/bin/start.sh"]
