Configuration de l'infrastructure:
	- Web1: 10.0.10.10 -> serveur web N°1
	- Web1: 10.0.10.20 -> serveur web N°2
	- mysqlmaster: 10.0.10.30
	- mysqlslave: 10.0.10.40

	Un client peut se sonnecter sur son site soit via web1 ou web2 et toute base de données créée, par le wordpress, est stockée sur mysqlmaster et répliqué sur mysqlslave.

Deploiement d'apache et wordpress :
	Il faut lancer le playbook.yml pour créer succesivement les deux serveurs web, avec exactement les même configuration (sauf l'ip). Il installe apache et wordpress, en le mettant en liaison avec le serveur mysql (slave et master).

	Le second playbook déploie sur le deux serveur mysqlmaster, qui réplique ensuite sur le slave, les bases de données de chaque clients. On peut rajouter des clients web en les ajoutant simplement dans la variable user prévue pour cela.

Hosts:
	Pour le premier playbook, seuls sont concernés les serveurs web, aux addresses ip 10.0.10.10 et 10.0.10.20.
	Le second playbook concerne les serveurs mysql slave et master, 10.0.10.30 et 10.0.10.40

Statut du projet:
	Toutes les machines sont en capacité de se joindre les unes les autres.
	mysqlmaster réplique bien correctement sur mysqlslave.
	Les clées ssh ont été bien échangées, aussi bien en itesciadmin ou root, mais que les configurations ne sont que en root. 
