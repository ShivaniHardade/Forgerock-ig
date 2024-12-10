FROM gcr.io/forgerock-io/java-17:latest
ENV INSTALL_DIR /opt/ig
COPY --chown=forgerock:root . "${INSTALL_DIR}"
ENV IG_INSTANCE_DIR /var/ig
RUN mkdir -p "${IG_INSTANCE_DIR}" \
    && chown -R forgerock:root "${IG_INSTANCE_DIR}" "${INSTALL_DIR}" \
    && chmod -R g+rwx "${IG_INSTANCE_DIR}" "${INSTALL_DIR}" \
    && chmod +x "${INSTALL_DIR}/bin/start.sh" 
USER 11111
ENTRYPOINT ${INSTALL_DIR}/bin/start.sh ${IG_INSTANCE_DIR}
