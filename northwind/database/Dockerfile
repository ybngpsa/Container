FROM mysql:5.7

# Set the root password
ENV MYSQL_ROOT_PASSWORD=changeit

# write one or more DOcker command to copy the *.sql into /docker-entrypoint-initdb.d

ADD 0-northwind-default-current-timestamp.sql /docker-entrypoint-initdb.d
ADD 1-northwind-data.sql /docker-entrypoint-initdb.d

#HEALTHCHECK --interval=30s --timeout=30s --start-period=15s --retries=3 CMD mysqladmin ping -uroot -pchangeit || exit 1
HEALTHCHECK --interval=30s --timeout=30s --start-period=15s --retries=3 \
   CMD mysqladmin ping -uroot -p${MYSQL_ROOT_PASSWORD} || exit 1

# where MySQL stores the database   
VOLUME /var/lib/mysql

# EXPOSE 3306
# VOLUME /var/lib/mysql