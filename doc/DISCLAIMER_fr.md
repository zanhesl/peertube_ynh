## Vue d'ensemble

### Qu'est-ce que PeerTube ?
PeerTube est une plateforme de streaming vid�o f�d�r�e (ActivityPub) utilisant P2P (BitTorrent) directement dans le navigateur Web, en utilisant <a href="https://github.com/feross/webtorrent"> WebTorrent </a>.

### Pourquoi PeerTube?

Nous ne pouvons pas cr�er d'alternatives de streaming vid�o FOSS � YouTube, Dailymotion, Vimeo... avec un logiciel centralis�. Une organisation seule ne peut pas avoir assez d'argent pour payer la bande passante et le stockage vid�o de son serveur.
Nous avons donc besoin d'un r�seau d�centralis� de serveurs � semant � des vid�os (comme [Hubzilla YunoHost](https://github.com/YunoHost-Apps/hubzilla_ynh), [Friendica YunoHost](https://github.com/YunoHost-Apps/friendica_ynh), [Mastodon YunoHost](https://github.com/YunoHost-Apps/mastodon_ynh)), [Diaspora](https://github.com/diaspora/diaspora) ([Diaspora YunoHost](https://github.com/YunoHost-Apps/diaspora_ynh)),[Funkwhale](https://funkwhale.audio) ([Funkwhale YunoHost](https://github.com/YunoHost-Apps/funkwhale_ynh)).
Mais ce n'est pas suffisant car une vid�o pourrait devenir c�l�bre et surcharger le serveur. C'est la raison pour laquelle nous devons utiliser un protocole P2P pour limiter la charge du serveur. Gr�ce � [WebTorrent](https://github.com/feross/webtorrent), nous pouvons faire du P2P (donc BitTorrent) dans le navigateur Web, d�s aujourd'hui.

### Pourquoi est-ce cool ?

Les serveurs sont g�r�s ind�pendamment par diff�rentes personnes et organisations. Ils peuvent appliquer des politiques de mod�ration extr�mement diff�rentes, afin que vous puissiez en trouver ou en cr�er une qui correspond parfaitement � vos go�ts.

En regardant une vid�o, vous aidez l'h�bergeur � la diffuser en devenant vous-m�me un diffuseur de la vid�o. Chaque instance n'a pas besoin de beaucoup d'argent pour diffuser les vid�os de ses utilisateurs.

## Points importants � lire avant l'installation

1. N�cessite un **domaine d�di�** comme **peertube.domain.tld**.
1. Le nom d'utilisateur de l'administrateur est: **root**.
1. **Le mot de passe administrateur et la configuration LDAP** seront envoy�s � l'adresse email indiqu�e au moment de l'installation.
1. L'URL ne peut pas �tre modifi�e une fois s�lectionn�e. Choisissez judicieusement le domaine.
1. Vous avez besoin de plus de **1 Go** de RAM. Si vous ne l'avez pas, veuillez cr�er une **m�moire swap**.

 
        $ dd if=/dev/zero of=/swapfile bs=1024 count=1048576
        $ mkswap /swapfile
        $ swapon /swapfile
        $ echo "/swapfile swap swap defaults 0 0" >> /etc/fstab

1. Cette application est **multi-instance** (vous pouvez avoir plus d'une instance PeerTube en cours d'ex�cution sur un serveur YunoHost)
1. **Si vous �tes h�berg� sur une machine virtuelle OVH ou rencontrez `gyp ERR! configure error`, veuillez passer � [ovh_fix](https://github.com/YunoHost-Apps/peertube_ynh/tree/ovh_fix)**

## Caract�ristiques sp�cifiques YunoHost

#### Support multi-utilisateur

* L'authentification LDAP est prise en charge, les instructions de configuration sont envoy�es � l'adresse email indiqu�e au moment de l'installation
* L'authentification HTTP n'est pas prise en charge
