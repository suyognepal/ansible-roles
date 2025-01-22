# EdgeDB Ansible Playbook

This playbook contains multiple roles for installing and configuring EdgeDB and MongoDB. The roles are organized in the following folder structure:

* `roles/edgedb/`: contains roles for installing and configuring EdgeDB
* `roles/mongodb-replication/`: contains roles for installing and configuring MongoDB in a replication set

To run the playbooks, use the following command:


ansible-playbook -i ansible/inventory/{file}.ini ansible/sitefiles/{file}.yml \
                 --private-key=id_rsa.pem --extra-vars "@roles/{role}/vars/{file}.yml"

