---
title: Sécurité Azure pour les applications cloud-native
description: Architecting Cloud Native .NET Apps for Azure (fr) Sécurité Azure pour les applications natives Cloud
ms.date: 06/30/2019
ms.openlocfilehash: 13b5ad7a883a83014913fa0a6a020610c28c524f
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989140"
---
# <a name="azure-security-for-cloud-native-apps"></a>Sécurité Azure pour les applications cloud-native

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Les applications cloud-natives peuvent être à la fois plus faciles et plus difficiles à sécuriser que les applications traditionnelles. En revanche, vous devez sécuriser des applications plus petites et consacrer plus d’énergie pour construire l’infrastructure de sécurité. La nature hétérogène des langages et des styles de programmation dans la plupart des déploiements de services signifie également que vous devez accorder plus d’attention aux bulletins de sécurité de nombreux fournisseurs différents.

D’un autre côté, les petits services, chacun avec son propre magasin de données, limitent la portée d’une attaque. Si un attaquant compromet un système, il est probablement plus difficile pour l’attaquant de faire le saut vers un autre système qu’il ne l’est dans une application monolithique. Les limites des processus sont des limites solides. En outre, si une base de données de sauvegarde fuit, alors les dommages sont plus limités, que cette base de données ne contient qu’un sous-ensemble de données et est peu susceptible de contenir des données personnelles.

## <a name="threat-modeling"></a>Modélisation des menaces

Peu importe si les avantages l’emportent sur les inconvénients des applications cloud-natives, le même état d’esprit holistique de sécurité doit être suivi. La sécurité et la sécurité de la pensée doivent faire partie de chaque étape de l’histoire du développement et des opérations. Lors de la planification d’une demande, posez des questions telles que :

- Quel serait l’impact de la perte de ces données?
- Comment pouvons-nous limiter les dommages causés par l’injection de données mauvaises dans ce service ?
- Qui devrait avoir accès à ces données?
- Existe-t-il des politiques de vérification concernant le processus d’élaboration et de mise en œuvre?

Toutes ces questions font partie d’un processus appelé [modélisation des menaces](https://docs.microsoft.com/azure/security/azure-security-threat-modeling-tool). Ce processus tente de répondre à la question de savoir quelles sont les menaces qui pèsent sur le système, la probabilité que les menaces soient et les dommages potentiels qu’elles en causent.

Une fois que la liste des menaces a été établie, vous devez décider si elles valent la peine d’être atténuées. Parfois, une menace est si peu probable et coûteuse à planifier pour qu’il ne vaut pas la peine de dépenser de l’énergie sur elle. Par exemple, un acteur au niveau de l’État pourrait injecter des changements dans la conception d’un processus qui est utilisé par des millions d’appareils. Maintenant, au lieu d’exécuter un certain morceau de code dans [l’anneau 3](https://en.wikipedia.org/wiki/Protection_ring), ce code est exécuté dans l’anneau 0. Cela permet un exploit qui peut contourner l’hyperviseur et exécuter le code d’attaque sur les machines en métal nu, permettant des attaques sur toutes les machines virtuelles qui fonctionnent sur ce matériel.

Les processeurs modifiés sont difficiles à détecter sans microscope et une connaissance avancée de la conception sur le silicium de ce processeur. Ce scénario est peu susceptible de se produire et coûteux à atténuer, donc probablement aucun modèle de menace ne recommanderait de construire la protection d’exploitation pour elle.

Les menaces les plus probables, `Id` telles que les contrôles `Id=2` `Id=3` d’accès cassés permettant des attaques par incrémentation (remplacer par l’injection SQL) ou SQL, sont plus attrayantes pour construire des protections contre. Les mesures d’atténuation de ces menaces sont tout à fait raisonnables pour construire et éviter les failles de sécurité embarrassantes qui salissent la réputation de l’entreprise.

## <a name="principle-of-least-privilege"></a>Principe du privilège minimum

L’une des idées fondatrices en matière de sécurité informatique est le Principe du moindre privilège (POLP). C’est en fait une idée fondamentale dans la plupart des formes de sécurité que ce soit numérique ou physique. En bref, le principe est que tout utilisateur ou processus devrait avoir le plus petit nombre de droits possibles pour exécuter sa tâche.

À titre d’exemple, pensez aux caissiers d’une banque : l’accès au coffre-fort est une activité rare. Donc, le caissier moyen ne peut pas ouvrir le coffre-fort eux-mêmes. Pour y avoir accès, ils doivent intensifier leur demande par l’intermédiaire d’un directeur de banque, qui effectue des contrôles de sécurité supplémentaires.

Dans un système informatique, un exemple fantastique est les droits d’un utilisateur se connectant à une base de données. Dans de nombreux cas, il existe un seul compte utilisateur utilisé pour construire la structure de la base de données et exécuter l’application. Sauf dans les cas extrêmes, le compte exécutant l’application n’a pas besoin de la possibilité de mettre à jour les informations schéma. Il devrait y avoir plusieurs comptes qui fournissent différents niveaux de privilège. L’application ne doit utiliser que le niveau d’autorisation que les subventions lisent et écrivent l’accès aux données dans les tableaux. Ce type de protection éliminerait les attaques qui visaient à laisser tomber les tables de base de données ou à introduire des déclencheurs malveillants.

Presque chaque partie de la construction d’une application cloud-native peut bénéficier de se rappeler le principe du moins de privilège. Vous pouvez le trouver en jeu lors de la configuration des pare-feu, des groupes de sécurité réseau, des rôles et des portées dans le contrôle d’accès basé sur les rôles (RBAC).

## <a name="penetration-testing"></a>test de pénétration ;

À mesure que les applications se compliquent, le nombre de vecteurs d’attaque augmente à un rythme alarmant. La modélisation des menaces est défectueuse en ce qu’elle a tendance à être exécutée par les mêmes personnes qui construisent le système. De la même manière que de nombreux développeurs ont du mal à envisager des interactions avec les utilisateurs, puis à construire des interfaces utilisateur inutilisables, la plupart des développeurs ont de la difficulté à voir chaque vecteur d’attaque. Il est également possible que les développeurs de construire le système ne sont pas bien versés dans les méthodologies d’attaque et de manquer quelque chose de crucial.

Les tests de pénétration ou les « tests de plume » impliquent d’amener des acteurs externes pour tenter d’attaquer le système. Ces attaquants peuvent être une société de conseil externe ou d’autres développeurs ayant de bonnes connaissances en sécurité d’une autre partie de l’entreprise. On leur donne carte blanche pour tenter de renverser le système. Fréquemment, ils trouveront des trous de sécurité étendus qui doivent être patchés. Parfois, le vecteur d’attaque sera quelque chose de totalement inattendu comme l’exploitation d’une attaque de phishing contre le PDG.

Azure lui-même est constamment en train de subir des attaques d’une [équipe de hackers à l’intérieur de Microsoft](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/). Au fil des ans, ils ont été les premiers à trouver des dizaines de vecteurs d’attaque potentiellement catastrophiques, les fermant avant qu’ils ne puissent être exploités à l’extérieur. Plus une cible est tentante, plus les acteurs éternels tenteront de l’exploiter et il y a quelques cibles dans le monde plus tentantes qu’Azure.

## <a name="monitoring"></a>Surveillance

Si un attaquant tente de pénétrer une application, il devrait y avoir un avertissement de celui-ci. Fréquemment, les attaques peuvent être repérées en examinant les journaux des services. Les attaques laissent des signes révélateurs qui peuvent être repérés avant qu’ils ne réussissent. Par exemple, un attaquant qui tente de deviner un mot de passe fera de nombreuses demandes à un système de connexion. La surveillance autour du système de connexion peut détecter des modèles bizarres qui sont hors de la ligne avec le modèle d’accès typique. Cette surveillance peut être transformée en une alerte qui peut, à son tour, alerter une personne des opérations pour activer une sorte de contre-mesure. Un système de surveillance très mature pourrait même prendre des mesures basées sur ces écarts en ajoutant de manière proactive des règles pour bloquer les demandes ou les réponses à la manette des gaz.

## <a name="securing-the-build"></a>Sécuriser la construction

Un endroit où la sécurité est souvent négligée est autour du processus de construction. Non seulement la construction devrait exécuter des contrôles de sécurité, tels que la numérisation pour le code non sécurisé ou les informations d’identification enregistrées, mais la construction elle-même doit être sécurisée. Si le serveur de construction est compromis, alors il fournit un vecteur fantastique pour introduire le code arbitraire dans le produit.

Imaginez qu’un attaquant cherche à voler les mots de passe des personnes qui se connectent à une application web. Ils pourraient introduire une étape de construction qui modifie le code de vérification pour refléter toute demande de connexion à un autre serveur. La prochaine fois que le code passe par la version, il est mis à jour en silence. La numérisation de vulnérabilité de code source n’attrapera pas ceci pendant qu’elle exécute avant la construction. De même, personne ne l’attrapera dans un examen de code parce que les étapes de construction vivent sur le serveur de construction. Le code exploité ira à la production où il peut récolter des mots de passe. Il n’y a probablement pas de registre de vérification des changements apportés au processus de construction, ou du moins personne ne surveille la vérification.

Il s’agit d’un parfait exemple d’une cible apparemment faible valeur qui peut être utilisé pour percer dans le système. Une fois qu’un attaquant viole le périmètre du système, il peut commencer à trouver des moyens d’élever ses autorisations au point qu’il peut causer un préjudice réel où il veut.

## <a name="building-secure-code"></a>Code sécurisé de construction

.NET Framework est déjà un cadre tout à fait sûr. Il évite certains des pièges du code non menté, comme la marche hors des extrémités des tableaux. Des travaux sont activement effectués pour corriger les trous de sécurité au fur et à mesure qu’ils sont découverts. Il y a même un programme de [primes aux insectes](https://www.microsoft.com/msrc/bounty) qui permet aux chercheurs de trouver des problèmes dans le cadre et de les signaler au lieu de les exploiter.

Il existe de nombreuses façons de rendre le code .NET plus sécurisé. Suivre les lignes directrices telles que les [lignes directrices de codage sécurisée pour l’article .NET](https://docs.microsoft.com/dotnet/standard/security/secure-coding-guidelines) est une étape raisonnable à prendre pour s’assurer que le code est sécurisé à partir de zéro. Le [top 10 OWASP](https://owasp.org/www-project-top-ten/) est un autre guide précieux pour construire le code sécurisé.

Le processus de construction est un bon endroit pour mettre des outils de numérisation pour détecter les problèmes dans le code source avant qu’ils ne le rendent en production. La plupart de chaque projet a des dépendances sur d’autres paquets. Un outil qui peut numériser pour les paquets obsolètes attrapera des problèmes dans une construction nocturne. Même lors de la construction d’images Docker, il est utile de vérifier et de s’assurer que l’image de base n’a pas de vulnérabilités connues. Une autre chose à vérifier est que personne n’a accidentellement vérifié les informations d’identification.

## <a name="built-in-security"></a>Sécurité intégrée

Azure est conçu pour équilibrer la convivialité et la sécurité pour la majorité des utilisateurs. Différents utilisateurs vont avoir des exigences de sécurité différentes, donc ils ont besoin d’affiner leur approche de la sécurité cloud. Microsoft publie beaucoup d’informations de sécurité dans le [Trust Center](https://azure.microsoft.com/support/trust-center/). Cette ressource devrait être la première étape pour les professionnels intéressés à comprendre le fonctionnement des technologies intégrées d’atténuation des attaques.

Au sein du portail Azure, le [azuréen Advisor](https://azure.microsoft.com/services/advisor/) est un système qui scanne constamment un environnement et formule des recommandations. Certaines de ces recommandations sont conçues pour économiser de l’argent aux utilisateurs, mais d’autres sont conçues pour identifier des configurations potentiellement précaires, comme le fait d’avoir un conteneur de stockage ouvert sur le monde et non protégé par un réseau virtuel.

## <a name="azure-network-infrastructure"></a>Infrastructure réseau Azure

Dans un environnement de déploiement sur site, beaucoup d’énergie est consacrée à la mise en place du réseautage. Mise en place de routeurs, commutateurs, et le tel est un travail compliqué. Les réseaux permettent à certaines ressources de parler à d’autres ressources et d’empêcher l’accès dans certains cas. Une règle de réseau fréquente consiste à restreindre l’accès à l’environnement de production de l’environnement de développement sur le risque hors-développement qu’un morceau de code à moitié développé tourne mal et supprime une bande de données.

Hors de la boîte, la plupart des ressources PaaS Azure ont seulement la configuration de réseau le plus basique et permissive. Par exemple, n’importe qui sur Internet peut accéder à un service d’application. Les nouvelles instances SQL Server sont généralement restreintes, de sorte que les parties externes ne peuvent pas y accéder, mais les plages d’adresses IP utilisées par Azure elle-même sont autorisées à passer. Ainsi, alors que le serveur SQL est protégé contre les menaces externes, un attaquant n’a qu’à mettre en place une tête de pont Azure d’où ils peuvent lancer des attaques contre toutes les instances SQL sur Azure.

Heureusement, la plupart des ressources Azure peuvent être placées dans un réseau virtuel Azure qui permet un contrôle d’accès plus fin. Semblable à la façon dont les réseaux sur site établissent des réseaux privés qui sont protégés du monde entier, les réseaux virtuels sont des îles d’adresses IP privées qui sont situés dans le réseau Azure.

![Figure 10-1 Un réseau](./media/virtual-network.png)
virtuel dans Azure**Figure 10-1**. Un réseau virtuel en Azure.

De la même manière que les réseaux sur site ont un pare-feu régissant l’accès au réseau, vous pouvez établir un pare-feu similaire à la limite du réseau virtuel. Par défaut, toutes les ressources d’un réseau virtuel peuvent toujours parler à Internet. Ce ne sont que les connexions entrantes qui nécessitent une certaine forme d’exception explicite pare-feu.

Avec le réseau établi, des ressources internes comme les comptes de stockage peuvent être configurés uniquement pour permettre l’accès par des ressources qui sont également sur le réseau virtuel. Ce pare-feu fournit un niveau de sécurité supplémentaire, si les clés de ce compte de stockage sont divulguées, les attaquants ne seraient pas en mesure de se connecter à elle pour exploiter les clés fuite. C’est un autre exemple du principe du moins de privilège.

Les nœuds d’un cluster Azure Kubernetes peuvent participer à un réseau virtuel comme d’autres ressources plus originaires d’Azure. Cette fonctionnalité s’appelle [Azure Container Networking Interface](https://github.com/Azure/azure-container-networking/blob/master/docs/cni.md). En effet, il alloue un sous-réseau dans le réseau virtuel sur lequel les machines virtuelles et les images de conteneurs sont alloués.

Poursuivant sur la voie de l’illustration du principe du moindre privilège, toutes les ressources d’un réseau virtuel n’ont pas besoin de parler à toutes les autres ressources. Par exemple, dans une application qui fournit une API Web sur un compte de stockage et une base de données SQL, il est peu probable que la base de données et le compte de stockage doivent se parler. Tout partage de données entre eux passerait par l’application Web. Ainsi, un [groupe de sécurité réseau (NSG)](https://docs.microsoft.com/azure/virtual-network/security-overview) pourrait être utilisé pour refuser le trafic entre les deux services.

Une politique de refus de communication entre les ressources peut être ennuyeux à mettre en œuvre, en particulier venant d’un contexte d’utilisation d’Azure sans restrictions de circulation. Sur d’autres nuages, le concept de groupes de sécurité réseau est beaucoup plus répandu. Par exemple, la politique par défaut sur AWS est que les ressources ne peuvent pas communiquer entre elles jusqu’à ce qu’elles soient activées par des règles d’un NSG. Bien que plus lent à développer cela, un environnement plus restrictif fournit un défaut plus sûr. L’utilisation de bonnes pratiques DevOps, en particulier en utilisant [Azure Resource Manager ou Terraform](infrastructure-as-code.md) pour gérer les autorisations peut faciliter le contrôle des règles.

Les réseaux virtuels peuvent également être utiles lors de la mise en place de la communication entre les ressources sur site et les ressources cloud. Un réseau privé virtuel peut être utilisé pour attacher les deux réseaux en toute transparence. Cela permet d’exécuter un réseau virtuel sans aucune sorte de passerelle pour les scénarios où tous les utilisateurs sont sur place. Il existe un certain nombre de technologies qui peuvent être utilisées pour établir ce réseau. Le plus simple est d’utiliser un [VPN site-site](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#s2smulti) qui peut être établi entre de nombreux routeurs et Azure. Le trafic est crypté et tunnelé sur Internet au même coût par byte que tout autre trafic. Pour les scénarios où plus de bande passante ou plus de sécurité est souhaitable, Azure offre un service appelé [Express Route](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#ExpressRoute) qui utilise un circuit privé entre un réseau sur place et Azure. Il est plus coûteux et difficile à établir, mais aussi plus sûr.

## <a name="role-based-access-control-for-restricting-access-to-azure-resources"></a>Contrôle d’accès basé sur les rôles pour restreindre l’accès aux ressources Azure

RBAC est un système qui fournit une identité aux applications en cours d’exécution en Azure. Les applications peuvent accéder à des ressources en utilisant cette identité au lieu ou en plus d’utiliser des clés ou des mots de passe.

## <a name="security-principals"></a>Principaux de sécurité

Le premier composant de RBAC est un directeur de sécurité. Un directeur de sécurité peut être un utilisateur, un groupe, un directeur de service ou une identité gérée.

![Figure 10-2 Différents types](./media/rbac-security-principal.png)
de directeurs de sécurité**Figure 10-2**. Différents types de principes de sécurité.

- Utilisateur - Tout utilisateur qui a un compte dans Azure Active Directory est un utilisateur.
- Groupe - Une collection d’utilisateurs de Azure Active Directory. En tant que membre d’un groupe, un utilisateur assume les rôles de ce groupe en plus du leur.
- Chef de service - Une identité de sécurité en vertu de laquelle les services ou les applications s’exécutent.
- Identité gérée - Une identité Azure Active Directory gérée par Azure. Les identités gérées sont généralement utilisées lors du développement d’applications cloud qui gèrent les informations d’identification pour l’authentification des services Azure.

Le principal de sécurité peut être appliqué à la plupart des ressources. Cela signifie qu’il est possible d’affecter un principal de sécurité à un conteneur fonctionnant au sein d’Azure Kubernetes, ce qui lui permet d’accéder aux secrets stockés dans Key Vault. Une fonction Azure pourrait obtenir une autorisation lui permettant de parler à une instance active d’annuaire pour valider un JWT pour un utilisateur d’appel. Une fois que les services sont activés avec un directeur de service, leurs autorisations peuvent être gérées granulairement en utilisant des rôles et des portées.

## <a name="roles"></a>Rôles

Un directeur de sécurité peut assumer de nombreux rôles ou, à l’aide d’une analogie plus vestimentaire, porter de nombreux chapeaux. Chaque rôle définit une série d’autorisations telles que « Lire les messages à partir du point de terminaison Azure Service Bus ». L’ensemble d’autorisation efficace d’un principal de sécurité est la combinaison de toutes les autorisations assignées à tous les rôles que le principal de sécurité a. Azure a un grand nombre de rôles intégrés et les utilisateurs peuvent définir leurs propres rôles.

![Figure 10-3 Définitions](./media/rbac-role-definition.png)
de rôle RBAC**Figure 10-3**. Définitions de rôleS RBAC.

Intégrés à Azure sont également un certain nombre de rôles de haut niveau tels que propriétaire, contributeur, lecteur et administrateur de compte utilisateur. Avec le rôle de propriétaire, un directeur de sécurité peut accéder à toutes les ressources et affecter des autorisations à d’autres. Un contributeur a le même niveau d’accès à toutes les ressources, mais il ne peut pas attribuer d’autorisations. Un lecteur ne peut afficher que les ressources Azure existantes et un administrateur de compte utilisateur peut gérer l’accès aux ressources Azure.

Des rôles intégrés plus granulaires tels que [DNS Zone Contributor](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#dns-zone-contributor) ont des droits limités à un seul service. Les directeurs de sécurité peuvent assumer n’importe quel nombre de rôles.

## <a name="scopes"></a>Étendues

Les rôles peuvent être appliqués à un ensemble restreint de ressources au sein d’Azure. Par exemple, en appliquant la portée à l’exemple précédent de lecture à partir d’une file d’attente de bus de service, vous pouvez réduire l’autorisation à une seule file d’attente: "Lire les messages à partir du point de terminaison `blah.servicebus.windows.net/queue1`Azure Service Bus "

La portée peut être aussi étroite qu’une seule ressource ou elle peut être appliquée à l’ensemble d’un groupe de ressources, d’un abonnement ou même d’un groupe de gestion.

Lorsque l’on teste si un directeur de sécurité a une certaine autorisation, la combinaison du rôle et de la portée est prise en compte. Cette combinaison fournit un mécanisme d’autorisation puissant.

## <a name="deny"></a>Deny

Auparavant, seules les règles de « permis » étaient autorisées pour le RBAC. Ce comportement a compliqué certaines portées à construire. Par exemple, permettre à un principal de sécurité d’accéder à tous les comptes de stockage, sauf un, il fallait accorder une autorisation explicite à une liste potentiellement interminable de comptes de stockage. Chaque fois qu’un nouveau compte de stockage a été créé, il faudrait l’ajouter à cette liste de comptes. Cela a ajouté des frais généraux de gestion qui n’était certainement pas souhaitable.

Les règles de refus ont préséance sur les règles d’autorisation. Maintenant, représentant la même portée "permettre à tous sauf un" pourrait être représenté comme deux règles "permettent à tous" et "refuser celui-ci spécifique". Refuser les règles non seulement faciliter la gestion, mais permettre des ressources qui sont très sûres en refusant l’accès à tout le monde.

## <a name="checking-access"></a>Vérification de l’accès

Comme vous pouvez l’imaginer, avoir un grand nombre de rôles et de portées peut rendre assez difficile la recherche de l’autorisation effective d’un directeur de service. Piling nier les règles en plus de cela, ne sert qu’à augmenter la complexité. Heureusement, il ya une calculatrice d’autorisations qui peuvent montrer les autorisations efficaces pour tout directeur de service. Il se trouve généralement sous l’onglet IAM dans le portail, comme le montre la figure 10-3.

![Calculatrice d’autorisation figure 10-4 pour un service](./media/check-rbac.png)
d’application Figure**10-4**. Calculatrice d’autorisation pour un service d’application.

## <a name="securing-secrets"></a>Sécurisation des secrets

Les mots de passe et les certificats sont un vecteur d’attaque courant pour les attaquants. Le matériel de craquage de mots de passe peut faire une attaque de force brute et essayer de deviner des milliards de mots de passe par seconde. Il est donc important que les mots de passe qui sont utilisés pour accéder aux ressources sont forts, avec une grande variété de caractères. Ces mots de passe sont exactement le genre de mots de passe qui sont presque impossibles à retenir. Heureusement, les mots de passe d’Azure n’ont pas besoin d’être connus par un humain.

De nombreux experts en sécurité [suggèrent](https://www.troyhunt.com/password-managers-dont-have-to-be-perfect-they-just-have-to-be-better-than-not-having-one/) que l’utilisation d’un gestionnaire de mot de passe pour garder vos propres mots de passe est la meilleure approche. Bien qu’il centralise vos mots de passe en un seul endroit, il permet également d’utiliser des mots de passe très complexes et de s’assurer qu’ils sont uniques pour chaque compte. Le même système existe au sein d’Azure : un magasin central de secrets.

## <a name="azure-key-vault"></a>Azure Key Vault

Azure Key Vault fournit un emplacement centralisé pour stocker des mots de passe pour des choses telles que des bases de données, des clés API et des certificats. Une fois qu’un secret est entré dans la voûte, il n’est jamais montré à nouveau et les commandes pour l’extraire et le voir sont délibérément compliqués. Les informations contenues dans le coffre-fort sont protégées à l’aide de modules de sécurité matériel validés par le chiffrement logiciel ou FIPS 140-2 de niveau 2.

L’accès au coffre-fort est assuré par l’intermédiaire des CNC, ce qui signifie que non seulement n’importe quel utilisateur peut accéder aux informations dans le coffre-fort. Dites qu’une application web souhaite accéder à la chaîne de connexion de base de données stockée dans Azure Key Vault. Pour y accéder, les applications doivent être exécutées à l’aide d’un directeur de service. Sous ce rôle assumé, ils peuvent lire les secrets du coffre-fort. Il existe un certain nombre de paramètres de sécurité différents qui peuvent limiter davantage l’accès qu’une application a à la chambre forte, de sorte qu’il ne peut pas mettre à jour les secrets, mais seulement les lire.

L’accès au coffre-fort clé peut être surveillé pour s’assurer que seules les applications attendues accèdent à la chambre forte. Les journaux peuvent être intégrés de nouveau dans Azure Monitor, déverrouillant la possibilité de configurer des alertes lorsque des conditions imprévues sont rencontrées.

## <a name="kubernetes"></a>Kubernetes

Au sein de Kubernetes, il y a un service similaire pour maintenir de petits morceaux d’informations secrètes. Les secrets de Kubernetes `kubectl` peuvent être définis via l’exécution typique.

Créer un secret est aussi simple que de trouver la version base64 des valeurs à stocker :

```console
echo -n 'admin' | base64
YWRtaW4=
echo -n '1f2d1e2e67df' | base64
MWYyZDFlMmU2N2Rm
```

Puis l’ajouter à `secret.yml` un fichier secrets nommé par exemple qui ressemble à l’exemple suivant:

```yml
apiVersion: v1
kind: Secret
metadata:
  name: mysecret
type: Opaque
data:
  username: YWRtaW4=
  password: MWYyZDFlMmU2N2Rm
```

Enfin, ce fichier peut être chargé dans Kubernetes en exécutant la commande suivante :

```console
kubectl apply -f ./secret.yaml
```

Ces secrets peuvent ensuite être montés en volumes ou exposés à des processus de conteneurs par le biais de variables de l’environnement. [L’approche d’application](https://12factor.net/) à douze facteurs pour les applications de construction suggère d’utiliser le plus petit dénominateur commun pour transmettre les paramètres à une application. Les variables de l’environnement sont le plus petit dénominateur commun, car elles sont prises en charge, peu importe le système d’exploitation ou l’application.

Une alternative pour utiliser les secrets intégrés de Kubernetes est d’accéder aux secrets de Azure Key Vault depuis Kubernetes. La façon la plus simple de le faire est d’attribuer un rôle RBAC au conteneur qui cherche à charger des secrets. L’application peut ensuite utiliser les API Azure Key Vault pour accéder aux secrets. Toutefois, cette approche nécessite des modifications au code et ne suit pas le modèle d’utilisation des variables de l’environnement. Au lieu de cela, il est possible d’injecter des valeurs dans un conteneur grâce à l’utilisation de [l’injecteur Azure Key Vault](https://mrdevops.io/introducing-azure-key-vault-to-kubernetes-931f82364354). Cette approche est en fait plus sécurisée que l’utilisation des secrets Kubernetes directement, car ils peuvent être consultés par les utilisateurs sur le cluster.

## <a name="encryption-in-transit-and-at-rest"></a>Chiffrement en transit et au repos

Il est important de protéger les données, qu’il s’agisse d’un disque ou d’un transit entre différents services. Le moyen le plus efficace d’empêcher les données de fuiter est de les chiffrer dans un format qui ne peut pas être facilement lu par d’autres. Azure prend en charge un large éventail d’options de cryptage.

### <a name="in-transit"></a>En transit

Il existe plusieurs façons de chiffrer le trafic sur le réseau azuréen. L’accès aux services Azure se fait généralement sur les connexions qui utilisent transport Layer Security (TLS). Par exemple, toutes les connexions aux API Azure nécessitent des connexions TLS. De même, les connexions aux points de terminaison dans le stockage Azure peuvent être limitées au travail uniquement sur les connexions cryptées TLS.

TLS est un protocole compliqué et le simple fait de savoir que la connexion utilise TLS n’est pas suffisant pour assurer la sécurité. Par exemple, TLS 1.0 est chroniquement précaire, et TLS 1.1 n’est pas beaucoup mieux. Même dans les versions de TLS, il existe différents paramètres qui peuvent rendre les connexions plus faciles à déchiffrer. La meilleure ligne de conduite est de vérifier et de voir si la connexion du serveur utilise des protocoles à jour et bien configurés.

Cette vérification peut être effectuée par un service externe tel que le test serveur SSL des laboratoires SSL. Un essai contre un critère d’évaluation Azure typique, dans ce cas, un point de terminaison de bus de service, donne un score presque parfait de A.

Même les services comme les bases de données Azure SQL utilisent le chiffrement TLS pour garder les données cachées. La partie intéressante sur le cryptage des données en transit à l’aide de TLS est qu’il n’est pas possible, même pour Microsoft, d’écouter sur la connexion entre les ordinateurs exécutant TLS. Cela devrait fournir un réconfort pour les entreprises concernées que leurs données peuvent être à risque de Microsoft proprement dit ou même un acteur d’État avec plus de ressources que l’attaquant standard.

![Figure 10-5 SSL labs rapport montrant une note de A pour un point de terminaison d’autobus de service. ](./media/ssl-report.png)
 **Figure 10-5**. Rapports de laboratoires SSL montrant une note de A pour un point de terminaison d’autobus de service.

Bien que ce niveau de cryptage ne sera pas suffisant pour toujours, il devrait inspirer confiance que les connexions Azure TLS sont tout à fait sécurisées. Azure continuera à faire évoluer ses normes de sécurité à mesure que le chiffrement s’améliorera. Il est bon de savoir qu’il ya quelqu’un qui regarde les normes de sécurité et la mise à jour Azure comme ils s’améliorent.

### <a name="at-rest"></a>Au repos

Dans toute application, il y a un certain nombre d’endroits où les données reposent sur le disque. Le code d’application lui-même est chargé à partir d’un mécanisme de stockage. La plupart des applications utilisent également une sorte de base de données comme SQL Server, Cosmos DB, ou même le stockage de table étonnamment rentable. Ces bases de données utilisent toutes un stockage fortement crypté pour s’assurer que personne d’autre que les applications avec les autorisations appropriées ne peuvent lire vos données. Même les opérateurs du système ne peuvent pas lire les données qui ont été cryptées. Ainsi, les clients peuvent rester confiants que leurs informations secrètes restent secrètes.

### <a name="storage"></a>Stockage

La sous-jacente d’une grande partie d’Azure est le moteur de stockage Azure. Les disques de machine virtuelle sont montés sur le dessus du stockage Azure. Azure Kubernetes Services fonctionnent sur des machines virtuelles qui, elles-mêmes, sont hébergées sur Azure Storage. Même les technologies sans serveur, telles que Azure Functions Apps et Azure Container Instances, sont à court de disque qui fait partie du stockage Azure.

Si Azure Storage est bien crypté, il fournit une base pour que la plupart des autres soient également cryptés. Azure Storage [est crypté](https://docs.microsoft.com/azure/storage/common/storage-service-encryption) avec [FIPS 140-2](https://en.wikipedia.org/wiki/FIPS_140) conforme [256 bits AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard). Il s’agit d’une technologie de cryptage bien considérée ayant fait l’objet d’un examen universitaire approfondi au cours des une vingtaine d’années. À l’heure actuelle, il n’y a pas d’attaque pratique connue qui permettrait à quelqu’un sans connaissance de la clé de lire les données cryptées par AES.

Par défaut, les clés utilisées pour chiffrer Azure Storage sont gérées par Microsoft. Il existe de vastes protections en place pour éviter l’accès malveillant à ces clés. Toutefois, les utilisateurs ayant des exigences de chiffrement particulières peuvent également [fournir leurs propres clés de stockage](https://docs.microsoft.com/azure/storage/common/storage-encryption-keys-powershell) qui sont gérées dans Azure Key Vault. Ces clés peuvent être révoquées à tout moment, ce qui rendrait effectivement le contenu du compte de stockage en les utilisant inaccessible.

Les machines virtuelles utilisent le stockage crypté, mais il est possible de fournir une autre couche de cryptage en utilisant des technologies comme BitLocker sur Windows ou DM-Crypt sur Linux. Ces technologies signifient que même si l’image du disque était divulguée hors du stockage, il resterait presque impossible de le lire.

### <a name="azure-sql"></a>Azure SQL

Les bases de données hébergées sur Azure SQL utilisent une technologie appelée [Transparent Data Encryption (TDE)](/sql/relational-databases/security/encryption/transparent-data-encryption) pour s’assurer que les données restent cryptées. Il est activé par défaut sur toutes les bases de données SQL nouvellement créées, mais doit être activé manuellement pour les bases de données héritées. TDE exécute le cryptage en temps réel et le décryptage non seulement de la base de données, mais aussi des sauvegardes et des journaux de transaction.

Les paramètres de chiffrement `master` sont stockés dans la base de données et, sur le démarrage, sont lus en mémoire pour les opérations restantes. Cela signifie `master` que la base de données doit rester non cryptée. La clé réelle est gérée par Microsoft. Cependant, les utilisateurs ayant des exigences de sécurité exigeantes peuvent fournir leur propre clé dans Key Vault de la même manière que cela se fait pour Azure Storage. Le coffre-fort clé fournit des services tels que la rotation des clés et la révocation.

La partie « transparente » de TDS vient du fait qu’il n’y a pas de modifications des clients nécessaires à l’utilisation d’une base de données cryptée. Bien que cette approche assure une bonne sécurité, la fuite du mot de passe de base de données est suffisante pour que les utilisateurs puissent décrypter les données. Il y a une autre approche qui crypte des colonnes ou des tableaux individuels dans une base de données. [Toujours crypté](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted-azure-key-vault) s’assure qu’à aucun moment les données chiffrées n’apparaissent en texte clair à l’intérieur de la base de données.

La mise en place de ce niveau de cryptage nécessite de passer par un assistant dans SQL Server Management Studio pour sélectionner le type de cryptage et où dans Key Vault pour stocker les clés associées.

![Figure 10-6 Sélection des colonnes dans un](./media/always-encrypted.png)
tableau à crypté à l’aide de Always Encrypted**Figure 10-6**. Sélection de colonnes dans une table à crypté à l’aide de Always Encrypted.

Les applications client qui lisent les informations de ces colonnes cryptées doivent faire des allocations spéciales pour lire les données chiffrées. Les chaînes de connexion `Column Encryption Setting=Enabled` doivent être mises à jour et les informations d’identification des clients doivent être récupérées à partir du coffre-fort. Le client SQL Server doit alors être doté des clés de chiffrement de la colonne. Une fois cela fait, les autres actions utilisent les interfaces standard de SQL Client. C’est-à-dire que des outils comme Dapper et Entity Framework, qui sont construits au-dessus de SQL Client, continueront à fonctionner sans changements. Toujours crypté peut ne pas encore être disponible pour chaque pilote SQL Server sur chaque langue.

La combinaison de TDE et Always Encrypted, qui peuvent tous deux être utilisés avec des clés spécifiques au client, garantit que même les exigences de chiffrement les plus exigeantes sont prises en charge.

### <a name="cosmos-db"></a>Cosmos DB

Cosmos DB est la nouvelle base de données fournie par Microsoft dans Azure. Il a été construit à partir de zéro avec la sécurité et la cryptographie à l’esprit. Le chiffrement AES-256bit est la norme pour toutes les bases de données Cosmos DB et ne peut pas être désactivé. Couplé avec l’exigence de communication TLS 1.2, l’ensemble de la solution de stockage est cryptée.

![Figure 10-7 Le flux de cryptage](./media/cosmos-encryption.png)
des données dans Cosmos DB**Figure 10-7**. Le flux de cryptage des données au sein de Cosmos DB.

Bien que Cosmos DB ne fournisse pas de clés de chiffrement des clients, l’équipe a fait un travail important pour s’assurer qu’elle reste conforme à la PCI-DSS sans cela. Cosmos DB ne prend pas non plus en charge une sorte de chiffrement de colonne unique similaire à Azure SQL Always Encrypted encore.

## <a name="keeping-secure"></a>Assurer la sécurité

Azure dispose de tous les outils nécessaires pour sortir un produit hautement sécurisé. Cependant, une chaîne n’est aussi forte que son maillon le plus faible. Si les applications déployées au-dessus d’Azure ne sont pas développées avec un état d’esprit de sécurité approprié et de bons audits de sécurité, alors ils deviennent le maillon faible de la chaîne. Il existe de nombreux grands outils d’analyse statique, bibliothèques de cryptage, et les pratiques de sécurité qui peuvent être utilisés pour s’assurer que le logiciel installé sur Azure est aussi sécurisé que Azure lui-même. Les exemples incluent les [outils d’analyse statique,](https://www.whitesourcesoftware.com/) [les bibliothèques de cryptage,](https://www.libressl.org/)et les pratiques de [sécurité](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/).

>[!div class="step-by-step"]
>[Suivant précédent](security.md)
>[Next](devops.md)
