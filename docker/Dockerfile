FROM gcr.io/forgerock-io/java-17:latest

# Default install directory for IG. Override this to set a different location.
ENV INSTALL_DIR /opt/ig

COPY --chown=forgerock:root . "${INSTALL_DIR}"

# Default home for IG config. Override this to set a different location.
ENV IG_INSTANCE_DIR /var/ig

RUN mkdir -p "${IG_INSTANCE_DIR}" \
    && chown -R forgerock:root "${IG_INSTANCE_DIR}" "${INSTALL_DIR}" \
    && chmod -R g+rwx "${IG_INSTANCE_DIR}" "${INSTALL_DIR}" \
    && chmod +x "${INSTALL_DIR}/bin/start.sh"  # Add this line to make the start script executable

USER 11111

ENTRYPOINT ${INSTALL_DIR}/bin/start.sh ${IG_INSTANCE_DIR}
