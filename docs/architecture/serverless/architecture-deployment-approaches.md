---
title: Approches de déploiement d’architecture-applications sans serveur
description: Guide sur les différentes façons dont les architectures d’entreprise sont déployées dans le Cloud, avec une comparaison entre IaaS, PaaS, les conteneurs et sans serveur.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 89a8e6a52331b563be334a867f563e9ded8d8cc4
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957960"
---
# <a name="architecture-deployment-approaches"></a>Approches du déploiement de l’architecture

Quelle que soit l’approche d’architecture utilisée pour concevoir une application métier, l’implémentation ou le déploiement de ces applications peut varier. Les entreprises hébergent des applications sur tout, du matériel physique aux fonctions sans serveur.

## <a name="n-tier-applications"></a>Applications multicouches

Le [modèle d’architecture à N niveaux](/azure/architecture/guide/architecture-styles/n-tier) est une architecture mature qui fait simplement référence aux applications qui séparent les différentes couches logiques en niveaux physiques distincts. L’architecture multiniveau est une implémentation physique de l’architecture à N couches. L’implémentation la plus courante de cette architecture comprend les éléments suivants :

- Une couche de présentation, par exemple une application Web.
- Une API ou une couche d’accès aux données, telle qu’une API REST.
- Une couche de données, telle qu’une base de données SQL.

![Architecture multiniveau](./media/n-tier-architecture.png)

Les solutions multiniveaux présentent les caractéristiques suivantes :

- Les projets sont généralement alignés sur des niveaux.
- Les tests peuvent être approchés différemment par niveau.
- Les niveaux fournissent des couches d’abstraction, par exemple la couche présentation ignore généralement les détails d’implémentation de la couche données.
- En règle générale, les couches interagissent uniquement avec les couches adjacentes.
- Les mises en production sont souvent gérées au niveau du projet et, par conséquent, de niveau. Une modification d’API simple peut nécessiter une nouvelle version d’une couche intermédiaire entière.

Cette approche offre plusieurs avantages, notamment :

- Isolation de la base de données (souvent, le serveur frontal ne dispose pas d’un accès direct à la base de données back end).
- La réutilisation de l’API (par exemple, les clients mobiles, de bureau et d’applications Web peuvent réutiliser les mêmes API).
- Possibilité de mettre à l’échelle les niveaux indépendamment les uns des autres.
- Isolation de la refactorisation : un niveau peut être refactorisé sans affecter les autres niveaux.

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>En local et infrastructure en tant que service (IaaS)

L’approche traditionnelle pour héberger des applications requiert l’achat de matériel et la gestion de toutes les installations logicielles, y compris le système d’exploitation. À l’origine, cela impliquait des centres de données et du matériel physiques coûteux. Les défis liés au fonctionnement du matériel physique sont nombreux, y compris :

- Le besoin d’acheter de l’excédent pour les scénarios « juste au cas » ou pics de demande.
- Sécurisation de l’accès physique au matériel.
- Responsabilité en cas de défaillance matérielle (défaillance de disque, par exemple).
- Température.
- Configuration des routeurs et des équilibreurs de charge.
- Redondance de l’alimentation.
- Sécurisation de l’accès aux logiciels.

![Approche IaaS](./media/iaas-approach.png)

La virtualisation du matériel via « machines virtuelles » active l’infrastructure en tant que service (IaaS). Les ordinateurs hôtes sont effectivement partitionnés pour fournir des ressources aux instances avec des allocations pour leur propre mémoire, UC et stockage. L’équipe provisionne les machines virtuelles nécessaires et configure les réseaux associés et l’accès au stockage.

Pour plus d’informations, consultez [architecture de référence N-Tier de machine virtuelle](/azure/architecture/reference-architectures/virtual-machines-windows/n-tier).

Bien que la virtualisation et l’infrastructure en tant que service (IaaS) répondent à de nombreux problèmes, elle est toujours très responsable des mains de l’équipe d’infrastructure. L’équipe gère les versions de système d’exploitation, applique des correctifs de sécurité et installe des dépendances tierces sur les ordinateurs cibles. Les applications se comportent souvent différemment sur les ordinateurs de production par rapport à l’environnement de test. Des problèmes surviennent en raison des différentes versions de dépendances et/ou des niveaux de référence de système d’exploitation. Bien que de nombreuses organisations déploient des applications multicouches sur ces cibles, de nombreuses entreprises tirent parti du déploiement vers un modèle natif plus Cloud tel que [Platform as a service](#platform-as-a-service-paas). Les architectures avec des microservices sont plus difficiles en raison des exigences de montée en charge pour l’élasticité et la résilience.

Pour plus d’informations, consultez [machines virtuelles](/azure/virtual-machines/).

## <a name="platform-as-a-service-paas"></a>PaaS (Platform as a Service)

PaaS (Platform as a service) offre des solutions configurées que les développeurs peuvent connecter directement. PaaS est un autre terme pour l’hébergement géré. Cela élimine la nécessité de gérer le système d’exploitation de base, les correctifs de sécurité et, dans de nombreux cas, les dépendances tierces. Les applications Web, les bases de données et les back-end mobiles sont des exemples de plateformes.

PaaS répond aux défis communs à IaaS. PaaS permet au développeur de se concentrer sur le code ou le schéma de base de données plutôt que sur la façon dont il est déployé. Les avantages de PaaS sont les suivants :

- Payez pour les modèles d’utilisation qui éliminent la surcharge liée à l’investissement sur des machines inactives.
- Le déploiement direct et les pipelines d’intégration continue, d’intégration continue (CI) et de livraison continue (CD) améliorés.
- Mises à niveau automatiques, mises à jour et correctifs de sécurité.
- Montée en puissance et montée en puissance du bouton de commande (mise à l’échelle élastique).

Le principal inconvénient de PaaS traditionnellement est le verrouillage des fournisseurs. Par exemple, certains fournisseurs PaaS prennent uniquement en charge ASP.NET, Node.js ou d’autres langages et plateformes spécifiques. Des produits tels que Azure App Service ont évolué pour prendre en charge plusieurs plateformes et prennent en charge une variété de langages et d’infrastructures pour l’hébergement d’applications Web.

![Architecture de plateforme en tant que service](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>SaaS (Software as a Service)

Le logiciel en tant que service ou SaaS est hébergé de manière centralisée et disponible sans installation ou configuration locale. SaaS est souvent hébergé en plus de PaaS en tant que plateforme pour le déploiement de logiciels. SaaS fournit des services pour s’exécuter et se connecter avec des logiciels existants. SaaS est souvent spécifique à l’industrie et à la verticale. SaaS est souvent concédé sous licence et fournit généralement un modèle client/serveur. La plupart des offres SaaS modernes utilisent des applications basées sur le Web pour le client. Les entreprises considèrent généralement SaaS comme une solution d’entreprise pour les offres de licence. Il n’est souvent pas implémenté comme un facteur d’architecture pour l’évolutivité et la facilité de maintenance d’une application. En effet, la plupart des solutions SaaS sont basées sur IaaS, PaaS et/ou serveurs back-end.

En savoir plus sur SaaS à l’aide d’un [exemple d’application](/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app).

## <a name="containers-and-functions-as-a-service-faas"></a>Conteneurs et fonctions en tant que service (FaaS)

Les conteneurs sont une solution intéressante qui offre des avantages de type PaaS sans la surcharge IaaS. Un conteneur est essentiellement un Runtime qui contient les éléments essentiels indispensables à l’exécution d’une application unique. Le noyau ou la partie principale du système d’exploitation hôte et des services tels que le stockage sont partagés sur un hôte. Le noyau partagé permet aux conteneurs d’être légers (certains sont de simples mégaoctets, par rapport à la taille en gigaoctet des machines virtuelles standard). Avec les hôtes déjà en cours d’exécution, les conteneurs peuvent être démarrés rapidement, ce qui facilite la haute disponibilité. La possibilité de créer rapidement des conteneurs fournit également des couches de résilience supplémentaires. L’ancrage est l’une des implémentations les plus populaires des conteneurs.

Les conteneurs présentent les avantages suivants :

- Légère et portable
- Autonome, il n’est donc pas nécessaire d’installer les dépendances
- Fournir un environnement cohérent indépendamment de l’hôte (s’exécute exactement comme sur un ordinateur portable comme sur un serveur Cloud)
- Peut être approvisionné rapidement pour la montée en puissance parallèle
- Peut être redémarré rapidement pour récupérer suite à une défaillance

Un conteneur s’exécute sur un hôte de conteneur (qui peut à son tour s’exécuter sur un ordinateur nu ou un ordinateur virtuel). Plusieurs conteneurs ou instances des mêmes conteneurs peuvent s’exécuter sur un seul hôte. Pour le basculement et la résilience véritables, les conteneurs doivent être mis à l’échelle entre les ordinateurs hôtes.

Pour plus d’informations sur les conteneurs d’ancrage, consultez [qu’est-ce que l’ancrage](../microservices/container-docker-introduction/docker-defined.md).

La gestion des conteneurs sur les hôtes nécessite généralement un outil d’orchestration tel que Kubernetes. La configuration et la gestion des solutions d’orchestration peuvent ajouter une surcharge et une complexité supplémentaires aux projets. Heureusement, de nombreux fournisseurs de Cloud fournissent des services d’orchestration via des solutions PaaS pour simplifier la gestion des conteneurs.

L’image suivante illustre un exemple d’installation de Kubernetes. Les nœuds de l’adresse d’installation sont mis à l’échelle et basculement. Ils exécutent des instances de conteneur de l’arrimeur qui sont gérées par le serveur principal. Le *kubelet* est le client qui relaie les commandes de Kubernetes vers l’ancrage.

![Kubernetes](./media/kubernetes-example.png)

Pour plus d’informations sur l’orchestration, consultez [Kubernetes sur Azure](/azure/aks/intro-kubernetes).

Functions as a service (FaaS) est un service de conteneur spécialisé qui est similaire à sans serveur. Une implémentation spécifique de FaaS, appelée [OpenFaaS](https://github.com/openfaas/faas), se trouve au-dessus des conteneurs pour fournir des fonctionnalités sans serveur. OpenFaaS fournit des modèles qui empaquetent toutes les dépendances de conteneur nécessaires pour exécuter un morceau de code. L’utilisation de modèles simplifie le processus de déploiement du code en tant qu’unité fonctionnelle. OpenFaaS cible les architectures qui incluent déjà des conteneurs et des orchestrateurs, car elle peut utiliser l’infrastructure existante. Bien qu’il fournisse des fonctionnalités sans serveur, il vous oblige spécifiquement à utiliser l’arrimeur et un orchestrateur.

## <a name="serverless"></a>Sans serveur

Une architecture sans serveur fournit une séparation claire entre le code et son environnement d’hébergement. Vous implémentez le code dans une *fonction* appelée par un *déclencheur*. Une fois cette fonction terminée, toutes les ressources nécessaires peuvent être libérées. Le déclencheur peut être manuel, un processus chronométré, une requête HTTP ou un chargement de fichier. Le résultat du déclencheur est l’exécution du code. Bien que les plateformes sans serveur varient, la plupart fournissent un accès à des API et des liaisons prédéfinies pour simplifier des tâches telles que l’écriture dans une base de données ou la mise en file d’attente des résultats.

Sans serveur est une architecture qui repose fortement sur l’abstraction de l’environnement hôte pour se concentrer sur le code. Il peut être considéré comme *moins serveur*.

Les solutions de conteneur fournissent aux développeurs des scripts de génération existants pour publier du code sur des images sans serveur. D’autres implémentations utilisent des solutions PaaS existantes pour fournir une architecture évolutive.

L’abstraction signifie que l’équipe DevOps n’a pas besoin d’approvisionner ou de gérer des serveurs, ni des conteneurs spécifiques. La plateforme sans serveur héberge du code, comme un script ou des exécutables empaquetés générés avec un kit de développement logiciel (SDK) associé, et alloue les ressources nécessaires pour que le code soit mis à l’échelle.

L’illustration suivante montre les quatre composants sans serveur. Une requête HTTP provoque l’exécution du code de l’API d’extraction. L’API d’extraction insère du code dans une base de données, et l’instruction INSERT déclenche plusieurs autres fonctions à exécuter pour effectuer des tâches telles que les tâches de calcul et l’exécution de la commande.

![Implémentation sans serveur](./media/serverless-implementation.png)

Les avantages des serveurs sans serveur sont les suivants :

- **Haute densité.** De nombreuses instances du même code sans serveur peuvent s’exécuter sur le même hôte par rapport aux conteneurs ou aux machines virtuelles. Les instances sont mises à l’échelle sur plusieurs hôtes montée en puissance et en résilience.
- **Micro-facturation.** La plupart des fournisseurs sans serveur facturent en fonction des exécutions sans serveur, ce qui permet de réaliser des économies considérables dans certains scénarios.
- **Mise à l’échelle instantanée.** Sans serveur peut être mis à l’échelle pour faire correspondre automatiquement et rapidement les charges de travail.
- **Délai de commercialisation plus rapide.** Les développeurs se concentrent sur le code et le déploient directement sur la plateforme sans serveur. Les composants peuvent être libérés indépendamment l’un de l’autre.

Le plus souvent, sans serveur, il est abordé dans le contexte de Compute, mais il peut également s’appliquer aux données. Par exemple, [Azure SQL](/azure/sql-database) et [Cosmos DB](/azure/cosmos-db) fournissent des bases de données Cloud qui ne nécessitent pas la configuration d’ordinateurs hôtes ou de clusters. Ce guide se concentre sur le calcul sans serveur.

## <a name="summary"></a>Résumé

Il existe un large éventail de choix disponibles pour l’architecture, y compris une approche hybride. Sans serveur simplifie l’approche, la gestion et le coût des fonctionnalités d’application au détriment du contrôle et de la portabilité. Toutefois, de nombreuses plates-formes sans serveur exposent la configuration pour aider à ajuster la solution. Les bonnes pratiques en matière de programmation peuvent également entraîner un plus grand nombre de code portable et une réduction du verrouillage des plates-formes sans serveur. Le tableau suivant illustre les approches d’architecture côte à côte. Choisissez sans serveur en fonction de vos besoins de mise à l’échelle, que vous souhaitiez gérer le runtime, et comment vous pouvez diviser vos charges de travail en petits composants. Vous en apprendrez plus sur les défis potentiels avec des points de décision sans serveur et autres dans le chapitre suivant.

|         |IaaS     |PaaS     |Conteneur|Sans serveur|
|---------|---------|---------|---------|----------|
|**Mettre à l’échelle**|Machine virtuelle       |Instance |Application      |Fonction  |
|**Extrait**|Matériel|Plateforme|Hôte de système d’exploitation|Runtime   |
|**Unité** |Machine virtuelle       |Project  |Image    |Code      |
|**Durée de vie**|Mois|Jours à mois|Minutes et jours|Millisecondes en minutes|
|**Responsabilité**|Applications, dépendances, Runtime et système d’exploitation|Applications et dépendances|Applications, dépendances et Runtime|Fonction

- L' **échelle** fait référence à l’unité utilisée pour mettre à l’échelle l’application
- **Abstracts** fait référence à la couche qui est abstraite par l’implémentation
- **Unit** fait référence à l’étendue de ce qui est déployé
- La **durée de vie** fait référence au runtime classique d’une instance spécifique
- La **responsabilité** fait référence à la surcharge liée à la création, au déploiement et à la maintenance de l’application.

Le chapitre suivant se concentre sur l’architecture sans serveur, les cas d’utilisation et les modèles de conception.

## <a name="recommended-resources"></a>Ressources recommandées

- [Guide d’architecture des applications Azure](/azure/architecture/guide/)
- [Azure Cosmos DB](/azure/cosmos-db)
- [Azure SQL](/azure/sql-database)
- [Modèle d’architecture à N niveaux](/azure/architecture/guide/architecture-styles/n-tier)
- [Kubernetes sur Azure](/azure/aks/intro-kubernetes)
- [Microservices](/azure/architecture/guide/architecture-styles/microservices)
- [Architecture de référence multiniveau d’ordinateur virtuel](/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
- [Machines virtuelles](/azure/virtual-machines/)
- [Qu’est-ce que Docker ?](../microservices/container-docker-introduction/docker-defined.md)
- [Application SaaS Wingtip tickets](/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[Précédent](architecture-approaches.md) 
> [Suivant](serverless-architecture.md)
