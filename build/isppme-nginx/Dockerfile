FROM bitnami/node:12-prod

COPY build/isppme-nginx/install_app.sh /install_app

RUN /install_app isppme https://github.com/kingraphaii/isppme

FROM frappe/erpnext-nginx:edge

COPY --from=0 /home/frappe/frappe-bench/sites/ /var/www/html/
COPY --from=0 /rsync /rsync
RUN echo -n "isppme" >> /var/www/html/apps.txt

VOLUME [ "/assets" ]

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["nginx", "-g", "daemon off;"]