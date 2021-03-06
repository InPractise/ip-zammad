# ip-zammad

Custom version of Zammad. [Original README.md](./ORIG_README.md).

# Initial Setup

Installed in Ubuntu 20.

```sh
# Follow requirements https://docs.zammad.org/en/latest/prerequisites/software.html
# Installed some libraries
# Installed Elasticsearch locally https://docs.zammad.org/en/latest/install/elasticsearch.html
# PostgreSQL was installed and configured
# Pulled source code to /opt/zammad
# Follow instructions here https://docs.zammad.org/en/latest/install/source.html
# Add database config
```

Then configured the actual application:

- Enabled SMTP in Google Workspace
- Created app password for support user
- Configured SMTP and IMAP in the application
- Configured DNS
- Other configurations

# Rebuild assets

To rebuild the assets:

```sh
cd /opt/zammad
git pull

su - zammad
cd /opt/zammad
export RAILS_ENV=production
export RAILS_SERVE_STATIC_FILES=true
rake assets:precompile
exit

systemctl restart zammad
systemctl restart nginx
```

# Check logs

```
less +F /opt/zammad/log/production.log
less +F /opt/zammad/log/scheduler_err.log
less +F /opt/zammad/log/scheduler_out.log
```
