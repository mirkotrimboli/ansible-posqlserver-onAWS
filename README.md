# ansible-posqlserver-onAWS

Delivery of a PostgreSQL Stand Alone server on AWS

# Prerequisiti AWS

Assicurarsi che sulla macchina sia presente:

* Un volume aggiuntivo per i dati
* Service Group con regole Inbound aperte per la connessione SSH
* che sia stato dato un ip alla scheda di rete

Sul server Ansible:

* Fare il download con git clone
* All'interno dell'inventory path inserire la "chiave.pem" per l'accesso in SSH
* Modificare il file hosts del server ansible aggiungendo gli ip degli host da raggiungere e nominandoli come specificato in posqlpgpool.hosts

# Installazione e configurazione iniziale dei nodi 

se necessario modificare le variabili sotto group_vars/all/vars.yml

* datadev_name: nvme1n1
* postgresql_dir: "/postgresql"
* postgresql_data: "/postgresql/pg_data"
* postgresql_arc: "/postgresql/archive"

lanciare il playbook ansible con il comando:

* ansible-playbook -i posqlpgpool.hosts posqlpgpool.yml --key-file=./chiave.pem