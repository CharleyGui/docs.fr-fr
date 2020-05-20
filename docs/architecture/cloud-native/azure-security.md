---
title: Sécurité Azure pour les applications Cloud natives
description: Architecture des applications .NET natives Cloud pour Azure | Sécurité Azure pour les applications Cloud natives
ms.date: 05/13/2020
ms.openlocfilehash: a39b64477eb9e896c6603e5609ede653bfee1e07
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614251"
---
# <a name="azure-security-for-cloud-native-apps"></a>Sécurité Azure pour les applications Cloud natives

Les applications natives du Cloud peuvent être à la fois plus simples et plus difficiles à sécuriser que les applications traditionnelles. À l’inconvénient, vous devez sécuriser des applications plus petites et dédier plus d’énergie pour créer l’infrastructure de sécurité. La nature hétérogène des langages de programmation et des styles dans la plupart des déploiements de service signifie également que vous devez faire attention aux bulletins de sécurité de nombreux fournisseurs différents.

Du côté du basculement, les services plus petits, chacun avec leur propre magasin de données, limitent l’étendue d’une attaque. Si une personne malveillante compromet un système, il est probablement plus difficile pour l’attaquant de passer à un autre système que dans une application monolithique. Les limites de processus sont des limites fortes. En outre, en cas de fuite d’une sauvegarde de base de données, le dommage est plus limité, car cette base de données contient uniquement un sous-ensemble de données et il est peu probable qu’elle contienne des données personnelles.

## <a name="threat-modeling"></a>Modélisation des menaces

Peu importe si les avantages compensent les inconvénients des applications Cloud natives, la même mentalité de la sécurité holistique doit être suivie. La sécurité et la réflexion sécurisée doivent faire partie de chaque étape de l’histoire du développement et des opérations. Lorsque vous planifiez une application, posez des questions telles que :

- Quel sera l’impact de cette perte de données ?
- Comment pouvons-nous limiter les dommages causés par l’injection de données incorrectes dans ce service ?
- Qui doit avoir accès à ces données ?
- Existe-t-il des stratégies d’audit autour du processus de développement et de mise en œuvre ?

Toutes ces questions font partie d’un processus appelé [modélisation des menaces](https://docs.microsoft.com/azure/security/azure-security-threat-modeling-tool). Ce processus tente de répondre à la question des menaces qui pèsent sur le système, de la probabilité que les menaces se présentent et de leurs dommages potentiels.

Une fois la liste des menaces établie, vous devez décider si elles méritent une atténuation. Parfois, une menace est si improbable et coûteuse à planifier qu’il n’est pas utile de dépenser de l’énergie. Par exemple, un acteur de niveau État peut injecter des modifications dans la conception d’un processus qui est utilisé par des millions d’appareils. Maintenant, au lieu d’exécuter un certain morceau de code dans l' [anneau 3](https://en.wikipedia.org/wiki/Protection_ring), ce code est exécuté dans l’anneau 0. Cela permet une attaque qui peut contourner l’hyperviseur et exécuter le code d’attaque sur les systèmes nus, ce qui permet d’effectuer des attaques sur toutes les machines virtuelles qui s’exécutent sur ce matériel.

Les processeurs modifiés sont difficiles à détecter sans microscope et une connaissance approfondie de la conception sur le silicium de ce processeur. Ce scénario est peu probable et coûteux à atténuer. par conséquent, il est probable qu’aucun modèle de menace ne vous recommande de créer une protection contre les attaques.

Les menaces plus probables, telles que les contrôles d’accès rompus autorisant `Id` les attaques par incrémentation (remplacement `Id=2` avec `Id=3` dans l’URL) ou l’injection SQL, sont plus attrayantes pour créer des protections contre. Les atténuations pour ces menaces sont très raisonnables pour créer et empêcher des failles de sécurité gênantes qui frottent la réputation de l’entreprise.

## <a name="principle-of-least-privilege"></a>Principe du privilège minimum

L’une des idées de fondation en matière de sécurité informatique est le principe du moindre privilège (POLP). Il s’agit en fait d’une idée fondamentale pour la plupart des formes de sécurité qu’elles soient numériques ou physiques. En bref, le principe est que tout utilisateur ou processus doit avoir le plus petit nombre de droits possible pour exécuter sa tâche.

À titre d’exemple, imaginez les raconteurs d’une banque : l’accès à la sécurité est une activité rare. Le Teller moyen ne peut donc pas ouvrir le coffre-fort. Pour accéder à, ils doivent faire remonter leur demande par le biais d’un gestionnaire bancaire, qui effectue des vérifications de sécurité supplémentaires.

Dans un système informatique, un exemple fantastique est le droit d’un utilisateur qui se connecte à une base de données. Dans de nombreux cas, il existe un compte d’utilisateur unique utilisé pour créer la structure de la base de données et exécuter l’application. Sauf dans les cas extrêmes, le compte qui exécute l’application n’a pas besoin de pouvoir mettre à jour les informations de schéma. Il doit y avoir plusieurs comptes qui fournissent différents niveaux de privilège. L’application doit uniquement utiliser le niveau d’autorisation qui accorde l’accès en lecture et en écriture aux données dans les tables. Ce type de protection élimine les attaques visant à supprimer des tables de base de données ou à introduire des déclencheurs malveillants.

Presque toutes les parties de la création d’une application Cloud Native peuvent être utiles pour mémoriser le principe des privilèges minimum. Vous pouvez le trouver lors de la configuration des pare-feu, des groupes de sécurité réseau, des rôles et des étendues dans le contrôle d’accès en fonction du rôle (RBAC).

## <a name="penetration-testing"></a>test de pénétration ;

À mesure que les applications deviennent plus complexes, le nombre de vecteurs d’attaque augmente à un taux d’alarme. La modélisation des menaces est en défaut, car elle a tendance à être exécutée par les mêmes personnes qui créent le système. De la même façon que de nombreux développeurs ont des difficultés à mettre en œuvre les interactions de l’utilisateur, puis à créer des interfaces utilisateur inutilisables, la plupart des développeurs éprouvent des difficultés à voir chaque vecteur d’attaque. Il est également possible que les développeurs qui créent le système ne soient pas bien connus dans les méthodologies d’attaque et manquent de choses cruciales.

Les tests de pénétration ou le « test de PEN » impliquent que les acteurs externes essaient d’attaquer le système. Ces personnes malveillantes peuvent être une société de conseil externe ou d’autres développeurs disposant de bonnes connaissances en matière de sécurité provenant d’une autre partie de l’entreprise. Elles reçoivent une carte blanche pour tenter de corrompre le système. Souvent, ils trouveront des failles de sécurité importantes qui doivent être corrigées. Parfois, le vecteur d’attaque est un peu inattendu, comme l’exploitation d’une attaque par hameçonnage contre le PDG.

Azure lui-même subit constamment des attaques d’une [équipe de pirates au sein de Microsoft](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/). Au fil des années, elles ont été les premières à trouver des dizaines de vecteurs d’attaque potentiellement catastrophiques, à les fermer avant qu’elles puissent être exploitées en externe. Plus une cible est séduisante, plus il est probable que les acteurs externes essaient de l’exploiter et il y a quelques cibles dans le monde plus tentant que Azure.

## <a name="monitoring"></a>Surveillance

Si une personne malveillante tente de pénétrer dans une application, il doit y avoir un avertissement. Souvent, les attaques peuvent être repérées en examinant les journaux des services. Les attaques laissent des signes de signalisation qui peuvent être repérés avant qu’ils ne s’exécutent correctement. Par exemple, une personne malveillante tentant de deviner un mot de passe effectue de nombreuses demandes vers un système de connexion. La surveillance autour du système de connexion peut détecter les modèles bizarres qui sont hors ligne avec le modèle d’accès standard. Cette analyse peut être convertie en alerte qui peut, à son tour, alerter une personne chargée de l’activation d’une contre-mesure. Un système de surveillance très mature peut même prendre des mesures en fonction de ces écarts, en ajoutant de manière proactive des règles pour bloquer les demandes ou limiter les réponses.

## <a name="securing-the-build"></a>Sécurisation de la Build

L’un des emplacements où la sécurité est souvent négligée est le processus de génération. Non seulement la génération doit exécuter les vérifications de sécurité, telles que l’analyse de code non sécurisé ou les informations d’identification archivées, mais la build elle-même doit être sécurisée. Si le serveur de builds est compromis, il fournit un vecteur fantastique pour introduire du code arbitraire dans le produit.

Imaginez qu’une personne malveillante cherche à voler les mots de passe des personnes qui se connectent à une application Web. Ils peuvent introduire une étape de génération qui modifie le code extrait pour mettre en miroir toute demande de connexion à un autre serveur. La prochaine fois que le code passe par la build, il est mis à jour en mode silencieux. L’analyse des vulnérabilités du code source ne l’intercepte pas, car elle s’exécute avant la génération. De même, personne ne l’intercepte dans une revue de code, car les étapes de génération résident sur le serveur de builds. Le code exploité passe en production, où il peut collecter les mots de passe. Il se peut que le journal d’audit du processus de génération ne change pas ou qu’il ne surveille pas l’audit.

Il s’agit d’un parfait exemple d’une cible de valeur apparemment faible qui peut être utilisée pour s’arrêter dans le système. Une fois qu’une personne malveillante a franchi le périmètre du système, elle peut commencer à trouver des moyens d’élever ses autorisations au point qu’ils peuvent causer des dommages réels partout où ils aiment.

## <a name="building-secure-code"></a>Génération de code sécurisé

.NET Framework est déjà un Framework très sécurisé. Il évite certains des pièges du code non managé, tels que le parcours des extrémités des tableaux. Le travail est effectué activement pour résoudre les failles de sécurité à mesure qu’elles sont découvertes. Il existe même un programme de primes de [bogues](https://www.microsoft.com/msrc/bounty) qui payent des chercheurs pour trouver des problèmes dans l’infrastructure et les signaler au lieu de les exploiter.

Il existe de nombreuses façons d’améliorer la sécurité du code .NET. Les instructions suivantes, telles que les [instructions de codage sécurisé pour .net](https://docs.microsoft.com/dotnet/standard/security/secure-coding-guidelines) , sont une étape raisonnable à prendre pour garantir la sécurité du code. Le [OWASP Top 10](https://owasp.org/www-project-top-ten/) est un autre guide précieux pour créer du code sécurisé.

Le processus de génération est un bon endroit pour mettre en place des outils d’analyse pour détecter les problèmes dans le code source avant de le rendre en production. La plupart des projets ont des dépendances sur d’autres packages. Un outil qui peut rechercher les packages obsolètes détecte les problèmes dans une build nocturne. Même lors de la création d’images d’ancrage, il est utile de vérifier et de s’assurer que l’image de base n’a pas de vulnérabilités connues. Une autre chose à vérifier est que personne n’a archivé accidentellement des informations d’identification.

## <a name="built-in-security"></a>Sécurité intégrée

Azure est conçu pour équilibrer l’utilisation et la sécurité pour la majorité des utilisateurs. Les différents utilisateurs ont des exigences de sécurité différentes, donc ils doivent ajuster leur approche à la sécurité du Cloud. Microsoft publie une grande quantité d’informations de sécurité dans le [Centre](https://azure.microsoft.com/support/trust-center/)de gestion de la confidentialité. Cette ressource doit être la première étape pour les professionnels qui souhaitent comprendre le fonctionnement des technologies d’atténuation des attaques intégrées.

Dans le Portail Azure, le [Azure Advisor](https://azure.microsoft.com/services/advisor/) est un système qui analyse constamment un environnement et formule des recommandations. Certaines de ces recommandations sont conçues pour faire gagner de l’argent aux utilisateurs, mais d’autres sont conçues pour identifier les configurations potentiellement non sécurisées, telles que la présence d’un conteneur de stockage ouvert au monde et non protégé par un réseau virtuel.

## <a name="azure-network-infrastructure"></a>Infrastructure réseau Azure

Dans un environnement de déploiement local, une grande quantité d’énergie est dédiée à la configuration de la mise en réseau. La configuration de routeurs, de commutateurs et du travail est compliqué. Les réseaux permettent à certaines ressources de communiquer avec d’autres ressources et d’empêcher l’accès dans certains cas. Une règle de réseau fréquente consiste à limiter l’accès à l’environnement de production à partir de l’environnement de développement au cas où un morceau de code semi-développé s’exécute mal et supprime un SWATH de données.

Dès l’installation, la plupart des ressources Azure PaaS n’ont que la configuration réseau la plus simple et la plus permissive. Par exemple, quiconque sur Internet peut accéder à un app service. Les nouvelles instances de SQL Server sont généralement restreintes, de sorte que les tiers externes ne peuvent pas y accéder, mais les plages d’adresses IP utilisées par Azure lui-même sont autorisées par le biais de. Donc, alors que le serveur SQL est protégé contre les menaces externes, une personne malveillante doit uniquement configurer un serveur de tête de pont Azure à partir duquel il peut lancer des attaques contre toutes les instances SQL sur Azure.

Heureusement, la plupart des ressources Azure peuvent être placées dans un réseau virtuel Azure qui permet un contrôle d’accès plus affiné. De la même façon que les réseaux locaux établissent des réseaux privés protégés du monde plus étendu, les réseaux virtuels sont des îlots d’adresses IP privées qui se trouvent dans le réseau Azure.

![Figure 9-1 un réseau virtuel dans Azure](./media/virtual-network.png)

**Figure 9-1**. Un réseau virtuel dans Azure.

De la même façon que les réseaux locaux disposent d’un pare-feu qui régit l’accès au réseau, vous pouvez établir un pare-feu similaire à la limite du réseau virtuel. Par défaut, toutes les ressources d’un réseau virtuel peuvent toujours communiquer avec Internet. Il s’agit uniquement de connexions entrantes qui requièrent une certaine forme d’exception de pare-feu explicite.

Une fois le réseau établi, les ressources internes, comme les comptes de stockage, peuvent être configurées pour autoriser uniquement l’accès par des ressources qui se trouvent également sur le réseau virtuel. Ce pare-feu fournit un niveau de sécurité supplémentaire, si les clés de ce compte de stockage sont divulguées, les attaquants ne seraient pas en mesure de s’y connecter pour exploiter les clés divulguées. Voici un autre exemple du principe des privilèges minimum.

Les nœuds d’un cluster Azure Kubernetes peuvent participer à un réseau virtuel de la même façon que d’autres ressources qui sont plus natives pour Azure. Cette fonctionnalité est appelée [interface Azure Container Networking](https://github.com/Azure/azure-container-networking/blob/master/docs/cni.md). En effet, il alloue un sous-réseau au sein du réseau virtuel sur lequel les machines virtuelles et les images de conteneur sont allouées.

En poursuivant le chemin d’accès à l’illustration du principe du moindre privilège, toutes les ressources d’un réseau virtuel ne doivent pas communiquer avec chaque autre ressource. Par exemple, dans une application qui fournit une API Web sur un compte de stockage et une base de données SQL, il est peu probable que la base de données et le compte de stockage doivent communiquer l’un avec l’autre. Tout partage de données entre les deux va traverser l’application Web. Par conséquent, un [groupe de sécurité réseau (NSG)](https://docs.microsoft.com/azure/virtual-network/security-overview) peut être utilisé pour refuser le trafic entre les deux services.

Une stratégie de refus de la communication entre les ressources peut être gênante à implémenter, en particulier en provenance d’un arrière-plan d’Azure sans restrictions du trafic. Sur d’autres Clouds, le concept de groupes de sécurité réseau est bien plus répandu. Par exemple, la stratégie par défaut sur AWS est que les ressources ne peuvent pas communiquer entre elles jusqu’à ce qu’elles soient activées par les règles d’un groupe de sécurité réseau. Bien qu’il soit plus lent à développer, un environnement plus restrictif fournit une valeur par défaut plus sécurisée. L’utilisation de pratiques DevOps appropriées, en particulier l’utilisation de [Azure Resource Manager ou Terraform](infrastructure-as-code.md) pour gérer les autorisations, peut faciliter le contrôle des règles.

Les réseaux virtuels peuvent également être utiles lors de la configuration de la communication entre des ressources locales et Cloud. Un réseau privé virtuel peut être utilisé pour attacher en toute transparence les deux réseaux. Cela permet l’exécution d’un réseau virtuel sans aucune sorte de passerelle pour les scénarios où tous les utilisateurs sont sur site. Il existe un certain nombre de technologies qui peuvent être utilisées pour établir ce réseau. La méthode la plus simple consiste à utiliser un [VPN de site à site](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#s2smulti) qui peut être établi entre plusieurs routeurs et Azure. Le trafic est chiffré et tunnelé sur Internet au même coût par octet que tout autre trafic. Pour les scénarios où une plus grande bande passante ou plus de sécurité est souhaitable, Azure propose un service appelé [Express route](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#ExpressRoute) qui utilise un circuit privé entre un réseau local et Azure. Il est plus coûteux et difficile à établir mais aussi plus sécurisé.

## <a name="role-based-access-control-for-restricting-access-to-azure-resources"></a>Contrôle d’accès en fonction du rôle pour la restriction de l’accès aux ressources Azure

RBAC est un système qui fournit une identité aux applications s’exécutant dans Azure. Les applications peuvent accéder aux ressources à l’aide de cette identité au lieu de ou en plus d’utiliser des clés ou des mots de passe.

## <a name="security-principals"></a>Principaux de sécurité

Le premier composant dans RBAC est un principal de sécurité. Un principal de sécurité peut être un utilisateur, un groupe, un principal du service ou une identité gérée.

![Figure 9-2 différents types de principaux de sécurité](./media/rbac-security-principal.png)

**Figure 9-2**. Différents types de principaux de sécurité.

- Utilisateur : tout utilisateur disposant d’un compte dans Azure Active Directory est un utilisateur.
- Groupe : collection d’utilisateurs d’Azure Active Directory. En tant que membre d’un groupe, un utilisateur prend les rôles de ce groupe en plus de lui-même.
- Principal du service : identité de sécurité sous laquelle les services ou applications s’exécutent.
- Identité gérée : identité Azure Active Directory gérée par Azure. Les identités gérées sont généralement utilisées lors du développement d’applications Cloud qui gèrent les informations d’identification pour l’authentification auprès des services Azure.

L’entité de sécurité peut être appliquée à la plupart des ressources. Cela signifie qu’il est possible d’affecter un principal de sécurité à un conteneur s’exécutant dans Azure Kubernetes, ce qui lui permet d’accéder aux secrets stockés dans Key Vault. Une fonction Azure peut prendre une autorisation qui lui permet de communiquer avec une instance de Active Directory pour valider un jeton JWT pour un utilisateur appelant. Une fois que les services sont activés avec un principal de service, leurs autorisations peuvent être gérées de manière granulaire à l’aide de rôles et d’étendues.

## <a name="roles"></a>Rôles

Un principal de sécurité peut prendre de nombreux rôles ou, à l’aide d’une analogie plus sartorial, porter de nombreux chapeaux. Chaque rôle définit une série d’autorisations telles que « lire les messages à partir d’Azure Service Bus point de terminaison ». Le jeu d’autorisations effectif d’un principal de sécurité est la combinaison de toutes les autorisations affectées à tous les rôles que possède le principal de sécurité. Azure dispose d’un grand nombre de rôles intégrés et les utilisateurs peuvent définir leurs propres rôles.

![Figure 9-3 définitions de rôle RBAC](./media/rbac-role-definition.png)

**Figure 9-3**. Définitions de rôle RBAC.

Intégré à Azure est également un certain nombre de rôles de haut niveau, tels que le propriétaire, le contributeur, le lecteur et l’administrateur de compte d’utilisateur. Avec le rôle de propriétaire, un principal de sécurité peut accéder à toutes les ressources et affecter des autorisations à d’autres utilisateurs. Un contributeur a le même niveau d’accès à toutes les ressources, mais il ne peut pas affecter d’autorisations. Un lecteur peut uniquement afficher les ressources Azure existantes et un administrateur de compte d’utilisateur peut gérer l’accès aux ressources Azure.

Des rôles intégrés plus granulaires, tels que le [contributeur de zone DNS](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#dns-zone-contributor) , disposent de droits limités à un seul service. Les principaux de sécurité peuvent prendre un nombre quelconque de rôles.

## <a name="scopes"></a>Étendues

Les rôles peuvent être appliqués à un ensemble restreint de ressources dans Azure. Par exemple, en appliquant l’étendue à l’exemple précédent de lecture à partir d’une file d’attente Service Bus, vous pouvez limiter l’autorisation à une seule file d’attente : « lire les messages du point de terminaison de Azure Service Bus `blah.servicebus.windows.net/queue1` »

L’étendue peut être aussi limitée qu’une seule ressource, ou elle peut être appliquée à un groupe de ressources entier, un abonnement ou même un groupe d’administration.

Lorsque vous testez si une entité de sécurité dispose d’une autorisation spécifique, la combinaison du rôle et de l’étendue est prise en compte. Cette combinaison fournit un mécanisme d’autorisation puissant.

## <a name="deny"></a>Deny

Auparavant, seules les règles « Allow » étaient autorisées pour RBAC. Ce comportement rendait certaines étendues compliquées à générer. Par exemple, autoriser un principal de sécurité à accéder à tous les comptes de stockage, à l’exception d’une autorisation explicite accordée à une liste potentiellement infinie de comptes de stockage. Chaque fois qu’un nouveau compte de stockage a été créé, il doit être ajouté à cette liste de comptes. Cette surcharge de gestion supplémentaire n’était certainement pas souhaitable.

Les règles de refus sont prioritaires sur les règles d’autorisation. Maintenant, il est possible de représenter la même portée « Allow All sauf One » sous la forme de deux règles « Allow All » (autoriser tout) et « refuser celle-ci une seule spécifique ». Les règles de refus simplifient non seulement la gestion, mais autorisent les ressources qui sont plus sécurisées en refusant l’accès à tout le monde.

## <a name="checking-access"></a>Vérification de l’accès

Comme vous pouvez l’imaginer, le fait de disposer d’un grand nombre de rôles et d’étendues peut compliquer la recherche de l’autorisation effective d’un principal de service. Empilez les règles de refus en plus de cela, sert uniquement à accroître la complexité. Heureusement, il existe une calculatrice des autorisations qui peut afficher les autorisations effectives pour n’importe quel principal du service. Il se trouve généralement sous l’onglet IAM dans le portail, comme illustré à la figure 10-3.

![Figure 9-4 Calculatrice des autorisations pour un service d’application](./media/check-rbac.png)

**Figure 9-4**. Calculatrice des autorisations pour un app service.

## <a name="securing-secrets"></a>Sécurisation des secrets

Les mots de passe et les certificats sont un vecteur d’attaque courant pour les attaquants. Le matériel de craquage de mot de passe peut effectuer une attaque par force brute et tenter de deviner les milliards de mots de passe par seconde. Il est donc important que les mots de passe utilisés pour accéder aux ressources soient forts, avec un grand nombre de caractères. Ces mots de passe sont exactement le type de mot de passe presque impossible à mémoriser. Heureusement, les mots de passe dans Azure n’ont en fait pas besoin d’être connus par un homme.

De nombreux [experts en sécurité suggèrent](https://www.troyhunt.com/password-managers-dont-have-to-be-perfect-they-just-have-to-be-better-than-not-having-one/) que l’utilisation d’un gestionnaire de mots de passe pour conserver vos propres mots de passe est la meilleure approche. Bien qu’il centralise vos mots de passe dans un emplacement unique, il permet également d’utiliser des mots de passe très complexes et de s’assurer qu’ils sont uniques pour chaque compte. Le même système existe dans Azure : un magasin central pour les secrets.

## <a name="azure-key-vault"></a>Azure Key Vault

Azure Key Vault fournit un emplacement centralisé pour stocker des mots de passe pour des éléments tels que des bases de données, des clés API et des certificats. Une fois qu’une clé secrète est entrée dans le coffre, elle ne s’affiche plus et les commandes permettant de l’extraire et de l’afficher sont intentionnellement compliquées. Les informations contenues dans la sécurité sont protégées à l’aide des modules de sécurité matériels validés par chiffrement logiciel ou FIPS 140-2 niveau 2.

L’accès au coffre de clés est assuré par le biais de RBACs, ce qui signifie que les utilisateurs ne peuvent pas accéder aux informations contenues dans le coffre. Disons qu’une application Web souhaite accéder à la chaîne de connexion de base de données stockée dans Azure Key Vault. Pour accéder à, les applications doivent s’exécuter à l’aide d’un principal de service. Dans ce rôle, ils peuvent lire les secrets à partir du coffre. Un certain nombre de paramètres de sécurité différents peuvent limiter davantage l’accès d’une application au coffre, afin qu’elle ne puisse pas mettre à jour les secrets, mais uniquement les lire.

L’accès au coffre de clés peut être surveillé pour s’assurer que seules les applications attendues accèdent au coffre. Les journaux peuvent être intégrés dans Azure Monitor, ce qui vous permet de configurer des alertes lorsque des conditions inattendues sont rencontrées.

## <a name="kubernetes"></a>Kubernetes

Dans Kubernetes, il existe un service similaire pour la maintenance de petites parties d’informations confidentielles. Les secrets Kubernetes peuvent être définis via l' `kubectl` exécutable standard.

La création d’un secret est aussi simple que la recherche de la version base64 des valeurs à stocker :

```console
echo -n 'admin' | base64
YWRtaW4=
echo -n '1f2d1e2e67df' | base64
MWYyZDFlMmU2N2Rm
```

Ensuite, ajoutez-le à un fichier de secrets nommé, `secret.yml` par exemple, qui ressemble à l’exemple suivant :

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

Enfin, ce fichier peut être chargé dans Kubernetes en exécutant la commande suivante :

```console
kubectl apply -f ./secret.yaml
```

Ces secrets peuvent ensuite être montés dans des volumes ou exposés à des processus de conteneur via des variables d’environnement. L’approche à [12 facteurs](https://12factor.net/) pour créer des applications suggère d’utiliser le plus petit dénominateur commun pour transmettre les paramètres à une application. Les variables d’environnement sont le plus petit dénominateur commun, car ils sont pris en charge, quel que soit le système d’exploitation ou l’application.

Une alternative à l’utilisation des secrets Kubernetes intégrés consiste à accéder aux secrets dans Azure Key Vault à partir de Kubernetes. La façon la plus simple de procéder consiste à affecter un rôle RBAC au conteneur qui cherche à charger les secrets. L’application peut ensuite utiliser les API Azure Key Vault pour accéder aux secrets. Toutefois, cette approche nécessite des modifications du code et ne suit pas le modèle d’utilisation des variables d’environnement. Au lieu de cela, il est possible d’injecter des valeurs dans un conteneur à l’aide de l' [injecteur Azure Key Vault](https://mrdevops.io/introducing-azure-key-vault-to-kubernetes-931f82364354). Cette approche est en fait plus sécurisée que l’utilisation directe des secrets Kubernetes, car ils sont accessibles aux utilisateurs sur le cluster.

## <a name="encryption-in-transit-and-at-rest"></a>Chiffrement en transit et au repos

Le maintien de la sécurité des données est important, qu’il s’agisse d’un disque ou d’un transit entre différents services. Le moyen le plus efficace de conserver des données contre les fuites consiste à les chiffrer dans un format qui ne peut pas être facilement lu par d’autres utilisateurs. Azure prend en charge un large éventail d’options de chiffrement.

### <a name="in-transit"></a>En transit

Il existe plusieurs façons de chiffrer le trafic sur le réseau dans Azure. L’accès aux services Azure s’effectue généralement sur des connexions qui utilisent le protocole TLS (Transport Layer Security). Par exemple, toutes les connexions aux API Azure nécessitent des connexions TLS. De même, les connexions aux points de terminaison dans le stockage Azure peuvent être limitées pour ne fonctionner qu’avec des connexions chiffrées TLS.

Le protocole TLS est un protocole complexe qui sait simplement que la connexion utilisant TLS n’est pas suffisante pour garantir la sécurité. Par exemple, TLS 1,0 est chroniquement non sécurisé et TLS 1,1 n’est pas bien plus performant. Même dans les versions de TLS, il existe différents paramètres qui peuvent faciliter le déchiffrement des connexions. La meilleure marche à suivre consiste à vérifier si la connexion au serveur utilise des protocoles à jour et bien configurés.

Cette vérification peut être effectuée par un service externe, tel que le test de serveur SSL des laboratoires SSL. Une série de tests sur un point de terminaison Azure classique, dans ce cas un point de terminaison service bus, produit un score proche du parfait d’un.

Même les services comme les bases de données SQL Azure utilisent le chiffrement TLS pour conserver les données masquées. La partie intéressante du chiffrement des données en transit à l’aide de TLS est qu’il n’est pas possible, même pour Microsoft, d’écouter la connexion entre les ordinateurs exécutant TLS. Cela devrait permettre aux entreprises soucieuses que leurs données soient menacées par Microsoft, voire un acteur d’État, avec plus de ressources que l’attaquant standard.

![Figure 9-5 rapport des laboratoires SSL présentant le score d’un pour un point de terminaison Service Bus.](./media/ssl-report.png)

**Figure 9-5**. Rapport des laboratoires SSL présentant le score d’un pour un point de terminaison Service Bus.

Bien que ce niveau de chiffrement ne soit pas suffisant pour tout le temps, il doit s’inspirer de la fiabilité des connexions Azure TLS. Azure continuera à évoluer ses normes de sécurité à mesure que le chiffrement s’améliore. Il est agréable de savoir qu’une personne regarde les normes de sécurité et met à jour Azure à mesure qu’elles s’améliorent.

### <a name="at-rest"></a>Au repos

Dans toutes les applications, il existe un certain nombre d’emplacements où les données se trouvent sur le disque. Le code d’application lui-même est chargé à partir d’un mécanisme de stockage. La plupart des applications utilisent également un type de base de données, tel que SQL Server, Cosmos DB ou même le stockage de tables remarquablement rentable. Ces bases de données utilisent toutes un stockage fortement chiffré pour s’assurer que personne autre que les applications disposant des autorisations appropriées ne puisse lire vos données. Même les opérateurs système ne peuvent pas lire les données qui ont été chiffrées. Pour que les clients puissent rester confiants, leurs informations secrètes restent secrètes.

### <a name="storage"></a>Stockage

Le moteur de stockage Azure est l’un des fondements de la majeure partie d’Azure. Les disques de machines virtuelles sont montés sur le stockage Azure. Les services Azure Kubernetes s’exécutent sur des machines virtuelles qui, elles-mêmes, sont hébergées sur le stockage Azure. Même les technologies sans serveur, telles que les applications Azure Functions et les Azure Container Instances, manquent de disque et font partie du stockage Azure.

Si le stockage Azure est correctement chiffré, il fournit une base pour la plupart des autres éléments à crypter. Le stockage Azure [est chiffré avec le chiffrement](https://docs.microsoft.com/azure/storage/common/storage-service-encryption) [AES 256 bits](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)conforme à la norme [FIPS 140-2](https://en.wikipedia.org/wiki/FIPS_140) . Il s’agit d’une technologie de chiffrement bien considérée qui a fait l’objet d’un examen approfondi des 20 dernières années. À l’heure actuelle, il n’existe aucune attaque pratique connue qui permettrait à un utilisateur sans avoir connaissance de la clé de lire les données chiffrées par AES.

Par défaut, les clés utilisées pour le chiffrement du stockage Azure sont gérées par Microsoft. Des protections étendues sont en place pour empêcher tout accès malveillant à ces clés. Toutefois, les utilisateurs ayant des exigences particulières en matière de chiffrement peuvent également [fournir leurs propres clés de stockage](https://docs.microsoft.com/azure/storage/common/storage-encryption-keys-powershell) qui sont gérées dans Azure Key Vault. Ces clés peuvent être révoquées à tout moment, ce qui rend effectivement le contenu du compte de stockage à l’aide de celles-ci inaccessibles.

Les machines virtuelles utilisent un stockage chiffré, mais il est possible de fournir une autre couche de chiffrement à l’aide de technologies telles que BitLocker sur Windows ou DM-crypt sur Linux. Ces technologies signifient que même si l’image de disque a été divulguée à partir du stockage, elle reste presque impossible à lire.

### <a name="azure-sql"></a>Azure SQL

Les bases de données hébergées sur Azure SQL utilisent une technologie appelée [transparent Data Encryption (TDE)](/sql/relational-databases/security/encryption/transparent-data-encryption) pour s’assurer que les données restent chiffrées. Elle est activée par défaut sur toutes les bases de données SQL nouvellement créées, mais doit être activée manuellement pour les bases de données héritées. TDE exécute le chiffrement et le déchiffrement en temps réel de non seulement la base de données, mais également les sauvegardes et les journaux de transactions.

Les paramètres de chiffrement sont stockés dans la `master` base de données et, au démarrage, sont lus en mémoire pour les opérations restantes. Cela signifie que la `master` base de données doit rester non chiffrée. La clé réelle est gérée par Microsoft. Toutefois, les utilisateurs ayant des exigences de sécurité précises peuvent fournir leur propre clé dans Key Vault à peu près de la même façon que pour le stockage Azure. Le Key Vault fournit des services tels que la rotation et la révocation des clés.

La partie « transparente » de TDS vient du fait qu’il n’y a pas de modifications clientes nécessaires pour utiliser une base de données chiffrée. Bien que cette approche offre une bonne sécurité, la fuite du mot de passe de base de données est suffisante pour que les utilisateurs puissent déchiffrer les données. Il existe une autre approche qui chiffre les colonnes individuelles ou les tables d’une base de données. [Always Encrypted](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted-azure-key-vault) garantit qu’à aucun moment les données chiffrées apparaissent en texte brut à l’intérieur de la base de données.

La configuration de ce niveau de chiffrement nécessite l’exécution d’un assistant dans SQL Server Management Studio pour sélectionner le type de chiffrement et l’emplacement de stockage des clés associées dans Key Vault.

![Figure 9-6 sélection des colonnes d’une table à chiffrer à l’aide de Always Encrypted](./media/always-encrypted.png)

**Figure 9-6**. Sélection de colonnes dans une table à chiffrer à l’aide de Always Encrypted.

Les applications clientes qui lisent des informations à partir de ces colonnes chiffrées doivent apporter des autorisations spéciales pour lire les données chiffrées. Les chaînes de connexion doivent être mises à jour avec `Column Encryption Setting=Enabled` et les informations d’identification du client doivent être récupérées à partir de la Key Vault. Le client SQL Server doit ensuite être amorcé avec les clés de chiffrement de colonne. Une fois cette opération effectuée, les autres actions utilisent les interfaces standard du client SQL. Autrement dit, les outils tels que dapper et Entity Framework, qui reposent sur le client SQL, continuent de fonctionner sans modification. Always Encrypted n’est peut-être pas encore disponible pour chaque SQL Server pilote dans chaque langue.

La combinaison de TDE et Always Encrypted, qui peut être utilisée avec des clés spécifiques au client, garantit que même les exigences de chiffrement les plus précises sont prises en charge.

### <a name="cosmos-db"></a>Cosmos DB

Cosmos DB est la base de données la plus récente fournie par Microsoft dans Azure. Il a été conçu dès le départ avec la sécurité et le chiffrement à l’esprit. Le chiffrement AES-256bit est standard pour toutes les bases de données Cosmos DB et ne peut pas être désactivé. Couplée à l’exigence TLS 1,2 pour la communication, la solution de stockage complète est chiffrée.

![Figure 9-7 le déroulement du chiffrement des données dans Cosmos DB](./media/cosmos-encryption.png)

**Figure 9-7**. Le déroulement du chiffrement des données dans Cosmos DB.

Bien que Cosmos DB ne fournisse pas de clés de chiffrement client, un travail important a été effectué par l’équipe pour s’assurer qu’elle reste conforme à la norme PCI-DSS sans cela. Cosmos DB ne prend pas non plus en charge le type de chiffrement à une seule colonne similaire à la Always Encrypted de SQL Azure.

## <a name="keeping-secure"></a>Assurer la sécurité

Azure dispose de tous les outils nécessaires pour libérer un produit hautement sécurisé. Toutefois, une chaîne est aussi forte que son lien le plus faible. Si les applications déployées sur Azure ne sont pas développées à l’aide d’une bonne mentalité de sécurité et d’audits de sécurité corrects, ils deviennent le lien faible dans la chaîne. Un grand nombre d’outils d’analyse statiques, de bibliothèques de chiffrement et de pratiques de sécurité peuvent être utilisés pour s’assurer que les logiciels installés sur Azure sont aussi sécurisés qu’Azure lui-même. Les exemples incluent des [Outils d’analyse statique](https://www.whitesourcesoftware.com/), des [bibliothèques de chiffrement](https://www.libressl.org/)et des [pratiques de sécurité](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/).

>[!div class="step-by-step"]
>[Précédent](security.md) 
> [Suivant](devops.md)
