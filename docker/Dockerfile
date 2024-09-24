# Use a base image with Java installed
FROM gcr.io/forgerock-io/java-17:latest

# Set environment variables for installation directories
ENV IG_INSTANCE_DIR=/var/ig
ENV INSTALL_DIR=/opt/ig

# Create necessary directories and set permissions
RUN mkdir -p "${IG_INSTANCE_DIR}" "${INSTALL_DIR}/bin" \
    && chown -R forgerock:root "${IG_INSTANCE_DIR}" "${INSTALL_DIR}" \
    && chmod -R g+rwx "${IG_INSTANCE_DIR}" "${INSTALL_DIR}"

# Copy files from the local bin and other folders into the image
COPY --chown=forgerock:root bin/ "${INSTALL_DIR}/bin/"
COPY --chown=forgerock:root docker/ "${INSTALL_DIR}/docker/"
COPY --chown=forgerock:root kubernetes/ "${INSTALL_DIR}/kubernetes/"
COPY --chown=forgerock:root "local policies/" "${INSTALL_DIR}/local policies/"
COPY --chown=forgerock:root lib/ "${INSTALL_DIR}/lib/"  # Adding the lib subfolder

# Make start.sh executable
RUN chmod +x "${INSTALL_DIR}/bin/start.sh"

# Optionally expose the port the app runs on
EXPOSE 8080

# Define the command to run the application
CMD ["java", "-jar", "${INSTALL_DIR}/bin/start.sh"]
