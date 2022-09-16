---
title: "Rediriger un nom de domaine géré par OVHcloud"
slug: redirection-nom-de-domaine
excerpt: "Découvrez les différents types de redirections et comment en créer une pour un nom de domaine géré par OVHcloud"
section: "Tâches courantes"
order: 01
---

**Dernière mise à jour le 15/09/2022**

## Objectif

La redirection d'un nom de domaine permet de rediriger celui-ci vers une nouvelle cible. Il existe différents types de redirections qui répondent à des besoins spécifiques.

**Découvrez les différents types de redirections et comment en créer une pour un nom de domaine géré par OVHcloud.**

## Prérequis

- Disposer d'un [nom de domaine](https://www.ovhcloud.com/fr/domains/)
- Être connecté à votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr){.external}.
- Être connecté à votre hébergement web (pour une redirection via un fichier [".htaccess"](#htaccess_Rewrite)).

## En pratique

### Comprendre la redirection d'un nom de domaine

La redirection d'un nom de domaine permet de rediriger un domaine/sous-domaine vers :

- un autre domaine/sous-domaine déjà existant :
**Exemple** : domain.tld
- une URL de site internet :
**Exemple** : http://www.domain.tld/welcome/

Pour faciliter les usages, l'[espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr) permet également de "rediriger" sans directement passer par l'interface de gestion de votre [zone DNS OVHcloud](https://docs.ovh.com/fr/domains/editer-ma-zone-dns/#les-enregistrements-dns) un domaine/sous-domaine vers :

- une adresse IP (IPv4 "entrée DNS A" ou IPv6 "entrée DNS AAAA"):
**Exemple** : 123.456.789.012
- un "nom canonique" :
**Exemple** : cname.domain.tld (le domaine est redirigé vers l'IP cible du nom canonique)

Ces deux dernières possibilitées ne seront pas détaillées dans ce guide.

Ces actions peuvent être réalisée de plusieurs manières :

- **depuis l'[espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr)** : un assistant de configuration permet de paramétrer votre redirection
- **depuis une méthode nécessitant de la programmation** : vous devrez créer vous-même la redirection dans un fichier (généralement un [".htaccess"](#htaccess_Rewrite)).

> [!warning]
>
> La mise en place d'une redirection peut avoir des conséquences sur le référencement de votre site internet. 
> Soyez vigilant quant aux manipulations que vous allez entreprendre ou contactez un [prestataire spécialisé](https://partner.ovhcloud.com/fr/) dans le référencement si nécessaire.
>

### Rediriger un nom de domaine via l'espace client

Une fois connecté à votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr){.external}, rendez-vous dans la partie `Web Cloud`, sélectionnez le domaine à rediriger dans la section `Noms de domaine`{.action}, puis cliquez sur l'onglet `Redirection`{.action}.

Pour ajouter une redirection, cliquez sur le bouton `Ajouter une redirection`{.action} :

![Présentation du menu redirection](images/RedirectionPanel.png){.thumbnail}

Le tableau affiche les redirections actives pour votre nom de domaine.

![Étape 1 pour l'ajout d'une redirection](images/adding_redirection_1.png){.thumbnail}

Dans la fenêtre, votre domaine à rediriger apparaît déjà. Renseignez uniquement le formulaire s'il vous souhaitez rediriger un sous-domaine.

La case `Rediriger aussi`{.action} peut être cochée pour rediriger également votre sous-domaine en *"www"* vers la même cible que votre domaine/sous-domaine.

Cliquez sur `Suivant`{.action} pour poursuivre à l'étape 2.

![Étape 2 pour l'ajout d'une redirection](images/adding_redirection_2.png){.thumbnail}

Choisissez maintenant vers quelle cible vous souhaitez rediriger le nom de domaine sélectionné. Deux choix possibles :

- **redirection vers une adresse web**

Redirige un nom de domaine vers un autre. Cette solution est idéale lorsque vous changez le nom de domaine de votre site internet.

- **redirection vers un serveur OVHcloud ou ailleurs**

> [!warning]
> 
> Pour cette option, la zone DNS active de votre domaine doit être celle présente dans votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr).
> 

Modifie la configuration DNS de votre domaine en le ciblant ailleurs (entrée DNS A, AAAA ou CNAME). Utile lorsque votre site internet n'est plus hébergé au même endroit.
Vous pouvez également réaliser cette action depuis la [zone DNS](https://docs.ovh.com/fr/domains/editer-ma-zone-dns/){.external}) active de votre domaine chez OVHcloud.

> [!warning]
> 
> À partir de ce point, ce guide abordera uniquement la redirection **vers une adresse web**. Concernant l'autre possibilité, rapprochez-vous de votre prestataire afin de connaître les enregistrements DNS que vous devrez modifier avant de poursuivre la démarche.
>

Pour une redirection **vers une adresse web**, choisissez le type de redirection que vous souhaitez mettre en place parmi les suivantes :

|Type de redirection|Description|
|---|---|
|Visible|Après la saisie du domaine redirigé, affiche le domaine cible dans la barre d'URL de votre navigateur internet au lieu du domaine redirigé|
|Invisible|Après la saisie du domaine redirigé, celui-ci reste affiché dans la barre d'URL de votre navigateur internet au lieu du domaine cible. <br> **Attention, cette action n'est pas compatible avec tous les sites et affecte le référencement de ce dernier**.|

La redirection invisible fonctionne avec une balise HTML *iFrame*. Celle-ci permet à votre domaine redirigé d'intégrer dans sa propre page HTML le contenu de l'autre page du domaine cible.

Cette encapsulation permet de s'assurer que les visiteurs de votre site ne puissent pas être en mesure de visualiser le domaine cible.

> [!warning]
>
> Attention, les pages encapsulées avec une balise *iFrame* peuvent ne pas être lues sur les smartphones. Leurs contenus n'est généralement pas pris en compte par les moteurs de recherche pour le référencement et l'indexation de votre site.
>

![Choix entre redirection visible et invisible](images/redirection_3xx_1.png){.thumbnail}

#### Pour une redirection visible

Pour la **redirection visible**, deux choix sont possibles.

|Type de redirection|Code HTTP|Description|
|---|---|---|
|Visible permanente|301|C'est le type de redirection « standard ».|
|Visible temporaire|302|Redirection à utiliser ponctuellement comme pour des événements éphémères.<br> Le positionnement sur les moteurs de recherche est moins bon qu'avec une redirection de type 301.|

Une fois votre choix fait, renseignez la cible de la redirection (l'adresse web/URL vers laquelle la redirection devra rediriger).

![Choix entre redirection visible permanente ou temporaire](images/redirection_3xx_2.png){.thumbnail}

Une fois les informations complétées, cliquez sur `Suivant`{.action}, assurez-vous que les informations affichées soient bien correctes, puis cliquez sur `Confirmer`{.action}.

> [!primary]
>
> La modification nécessite un temps de propagation de 4 à 24 heures maximum avant d’être pleinement effective.
>

#### Pour une redirection invisible

Concernant la redirection invisible (code HTTP 200), complétez les informations qui s'affichent (adresse web et options) puis cliquez sur `Suivant`{.action}. Assurez-vous que les informations affichées soient correctes avant de cliquer sur `Confirmer`{.action}.

|Champs|Description|
|---|---|
|Titre|Titre de votre site internet. Il s'affichera en tant que titre de page dans l'onglet des navigateurs internet.|
|Mots clés|Peuvent être utilisés par les moteurs de recherche pour partiellement référencer la page.|
|Description|Description concernant votre site internet. Elle sera utilisée par les moteurs de recherche dans leurs résultats.|

> [!primary]
>
> La modification nécessite un temps de propagation de 4 à 24 heures maximum avant d’être pleinement effective.
>

![Création d'une redirection invisible](images/invisible_redirection.png){.thumbnail}

### Rediriger un nom de domaine via un fichier ".htaccess" <a name="htaccess_Rewrite"></a>

> [!warning]
>
> OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
> 
> Nous mettons à votre disposition cette partie du guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [prestataire spécialisé](https://partner.ovhcloud.com/fr/) si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance sur ce qui va suivre. Plus d'informations dans la section [« Aller plus loin »](#go-further) de ce guide.
>

Les fichiers ".htaccess" sont des fichiers de configuration dans lesquels des commandes peuvent être spécifiées. Lors de l’exécution du code de votre site internet par le serveur web (Apache), les commandes seront interprétées et ainsi exécutées. Parmi celles-ci, il est possible de créer des redirections.

Manipuler un fichier ".htaccess" peut rendre innaccessible vos sites. En cas de doute, contactez un [prestataire spécialisé](https://partner.ovhcloud.com/fr/) .

Vous pouvez retrouver l'ensemble de notre documentation sur le ".htaccess" dans la section [« Aller plus loin »](#go-further) de ce guide.

> [!primary]
>
> Nous vous conseillons de **réaliser une sauvegarde de votre fichier .htaccess** avant d'y effectuer des modifications pour rétablir la version antérieure si besoin.
>

- **Redirect permanent**

Le code envoyé sera un code HTTP 301. Il prévient les robots des moteurs de recherche qu'il faut mettre à jour leurs liens vers la nouvelle adresse.

Voici le code à ajouter pour rediriger le site en entier :

```bash
Redirect permanent / http://domain.tld/
```

Pour changer un répertoire/fichier :

```bash
Redirect permanent /ancien_repertoire http://nouveau-site.tld/nouveau_repertoire
Redirect permanent /ancien_fichier.php http://site.tld/nouveau_fichier.php
```

- **Redirect gone**

Si un fichier n’existe plus, il est préférable de remplacer le message *404 document non trouvé* par un message plus explicite de type *410 le document n’existe plus* :

```bash
Redirect gone /supprime.html
```

- **Redirect seeother**

Si vous changez l’extension d’un fichier, *seeother* permet d'en modifier le type en envoyant un code HTTP 303 :

```bash
Redirect seeother /exemple.doc http://site.tld/exemple.pdf
```

- **Redirect Temp**

Une redirection temporaire de type HTTP 302 peut être utilisée lorsque vous déplacez temporairement des fichiers sur un autre site :

```bash
Redirect temp / http://autre_site_web.tld/site/
```

## Aller plus loin <a name="go-further"></a>

[Bloquer l’accès à mon site pour certaines adresses IP via un fichier ".htaccess"](https://docs.ovh.com/fr/hosting/mutualise-htaccess-comment-bloquer-certaines-ip-au-niveau-de-mon-site/).

[Protéger l'interface d'administration de votre site via le ".htaccess"](https://docs.ovh.com/fr/hosting/mutualise-htaccess-comment-proteger-lacces-a-un-repertoire-par-une-authentification/).

[Réécrire vos URLs grâce au « mod_rewrite »](https://docs.ovh.com/fr/hosting/htaccess-reecriture-url-mod-rewrite/).

[Effectuer d'autres opérations avec le fichier ".htaccess"](https://docs.ovh.com/fr/hosting/mutualise-htaccess-les-autres-operations-realisables-avec-des-fichiers-htaccess/).

[Comment éditer ma zone DNS ?](https://docs.ovh.com/fr/domains/editer-ma-zone-dns/)

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](https://partner.ovhcloud.com/fr/).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](https://www.ovhcloud.com/fr/support-levels/).

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>.