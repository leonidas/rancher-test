# Rancher test environment for Leonidas

This is a simple Ansible environment for trying out Rancher.

## Note about LetsEncrypt SSL certificates

When setting up a Rancher server from this repository first time, the `letsencrypt` deployment needs to be done in three steps (enable letsencrypt support in vhost, create certs, enable ssl) because there is a chicken-egg problem:

1. start with `fooapp_ssl: false` and `fooapp_letsencrypt: false`, make sure everything works over HTTP
2. flip `fooapp_letsencrypt: true`, do not touch `fooapp_ssl` yet. Run the `fooapp` role, make sure `nginx` is restarted.
3. add a certificate for `fooapp` to the `letsencrypt` role, run the `letsencrypt` role
4. now you can flip `fooapp_ssl: true` and run the `fooapp` rule, make sure everything works over HTTPS

## Manual steps

Rancher gives a good copy-pasteable command for adding nodes,

## Next steps (TODO)

### For the test

- [ ] Figure out how SSL certificates and load balancers work under Rancher
- [ ] Try running some actual app like Jenkins
- [ ] How does one access container logs?

### For production

- [ ] Setup an external database (MySQL)
- [ ] Evaluate Cattle, Kubernetes, Mesos and Swarm modes and select multi-node deployment strategy
