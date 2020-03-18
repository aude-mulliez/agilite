
#Documentation sur la purge au transfert


##Tournees et releves


###Envoi


On fait de la mise à jour de la base après envoi en cas de succès.


###Reception

Pour chaque tournée reçue:
	
-> purgePointDeVenteDansLaTourneeReception : on enlève les points de vente dans la tournée qui ne sont plus reçus par l'API (on ne touche pas aux points de vente ici).

-> purgeReleveReception :  

- si on trouve le releve recu dans indexedDb, on ne le modifie pas.
	
- sinon on le rajoute

- les releves non reçus sont supprimés.

->	on ajoute / met à jour la tournée en base indexedDb



Cas du releve mis en remplacement ???



##Ordres de recherche



###Envoi


On fait de la mise à jour de la base après envoi en cas de succès.


###Reception

purgerORTablette :  On regarde les or en base indexedDb

- on supprime ceux que l'on ne reçoit pas

- ajout des reçus qui ne sont pas présent en base 

- si on trouve l'or recu dans indexedDb, on ne le modifie pas.





##Produits à remplacer


#Envoi

On fait de la mise à jour de la base après envoi en cas de succès.

#Reception






purgerProduitARemplacerTablette : On regarde les produits en base indexedDb,
si le produit n'est pas dans la liste des produits reçus ( et que ce n'est pas un releveSimple) on le supprime avec son produit remplacant et son produit remplacant alternatif dans le cas d'un bien durable.

Ajout : 

- On prend tous les produits à remplacer sauf les faits. 
- Produits remplacants : ajout des reçus qui ne sont pas présent en base (pour les autres on les garde inchangés)
- produits remplacants alternatifs :  ajout des reçus qui ne sont pas présent en base  ( avec typeVariete bien durable)





##Points de vente

En fin de transfert on effectue : 

- purgerPointDeVente : un nombre de jour précisé par l'équipe métier (aka NB_JOURS_AVANT_PURGE_NOUVEAU_PDV) détermine la durée pendant laquelle on conserve un point de vente qui vient d'être crée sur la tablette (7 à l'heure ou j'écris ce document). 