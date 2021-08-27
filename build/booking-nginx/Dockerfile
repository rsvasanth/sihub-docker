FROM bitnami/node:14-prod

COPY build/booking-nginx/install_app.sh /install_app

RUN /install_app booking https://github.com/rsvasanth/booking.git

FROM frappe/erpnext-nginx:v13.9.1

COPY --from=0 /home/frappe/frappe-bench/sites/ /var/www/html/
COPY --from=0 /rsync /rsync
RUN echo -n "\n booking" >> /var/www/html/apps.txt

VOLUME [ "/assets" ]

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["nginx", "-g", "daemon off;"]