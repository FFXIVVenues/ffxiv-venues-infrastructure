FROM quay.io/phasetwo/phasetwo-keycloak:latest as builder
ADD --chown=keycloak:keycloak https://github.com/wadahiro/keycloak-discord/releases/download/v0.5.0/keycloak-discord-0.5.0.jar /opt/keycloak/providers/myprovider.jar
# COPY --chown=keycloak:keycloak themes/ffxivvenues /opt/keycloak/themes/ffxivvenues
RUN /opt/keycloak/bin/kc.sh build

FROM quay.io/phasetwo/phasetwo-keycloak:latest
COPY --from=builder /opt/keycloak/ /opt/keycloak/

ENTRYPOINT ["/opt/keycloak/bin/kc.sh"]
CMD [ "start", "--optimized",  "--spi-theme-static-max-age=-1", "--spi-theme-cache-themes=false", "--spi-theme-cache-templates=false" ]