---
title: Approches de déploiement d’architecture - Applications sans serveur
description: Un guide sur les différentes façons dont les architectures d’entreprise sont déployées dans le nuage, en comparaison entre IaaS, PaaS, conteneurs, et sans serveur.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c745a4eb1c6f4a00bf139100b02f31cf3327d01e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522731"
---
# <a name="architecture-deployment-approaches"></a>Approches du déploiement de l’architecture

Indépendamment de l’approche d’architecture utilisée pour concevoir une application d’entreprise, la mise en œuvre ou le déploiement de ces applications peut varier. Les entreprises hébergent des applications sur tout, du matériel physique aux fonctions sans serveur.

## <a name="n-tier-applications"></a>Applications N-Tier

Le [modèle d’architecture N-Tier](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier) est une architecture mature et se réfère simplement à des applications qui séparent diverses couches logiques en niveaux physiques distincts. L’architecture N-Tier est une mise en œuvre physique de l’architecture N-Layer. La mise en œuvre la plus courante de cette architecture comprend :

- Un niveau de présentation, par exemple une application web.
- Un API ou un niveau d’accès aux données, comme une API REST.
- Un niveau de données, comme une base de données SQL.

![Architecture N-tier](./media/n-tier-architecture.png)

Les solutions À niveau N ont les caractéristiques suivantes :

- Les projets sont généralement alignés avec les niveaux.
- Les tests peuvent être abordés différemment par niveau.
- Les niveaux fournissent des couches d’abstraction, par exemple le niveau de présentation est généralement ignorant des détails de mise en œuvre du niveau de données.
- En règle générale, les couches n’interagissent qu’avec les couches adjacentes.
- Les rejets sont souvent gérés au niveau du projet, et donc de niveau. Un simple changement d’API peut nécessiter une nouvelle version d’un niveau intermédiaire entier.

Cette approche offre plusieurs avantages, notamment :

- Isolement de la base de données (souvent l’extrémité avant n’a pas un accès direct à la base de données back end).
- La réutilisation de l’API (par exemple, les clients mobiles, de bureau et d’applications Web peuvent tous réutiliser les mêmes API).
- Capacité d’échelle des niveaux indépendants les uns des autres.
- Refactoring isolation: un niveau peut être refactorisé sans avoir d’impact sur d’autres niveaux.

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>Sur place et infrastructure en tant que service (IaaS)

L’approche traditionnelle de l’hébergement des applications nécessite l’achat de matériel et la gestion de toutes les installations logicielles, y compris le système d’exploitation. À l’origine, cela impliquait des centres de données coûteux et du matériel physique. Les défis qui viennent avec le matériel physique d’exploitation sont nombreux, y compris:

- La nécessité d’acheter des excès pour des scénarios de « juste au cas » ou de pic de demande.
- Assurer l’accès physique au matériel.
- Responsabilité de la défaillance matérielle (comme la défaillance du disque).
- Refroidissement.
- Configuration des routeurs et des équilibristes de charge.
- Redondance de puissance.
- Sécuriser l’accès au logiciel.

![Approche IaaS](./media/iaas-approach.png)

La virtualisation du matériel, via des "machines virtuelles" permet l’infrastructure en tant que service (IaaS). Les machines hôtes sont effectivement partitionnées pour fournir des ressources aux instances avec des allocations pour leur propre mémoire, processeur, et le stockage. L’équipe fournit les magnétoscopes nécessaires et configure les réseaux associés et l’accès au stockage.

Pour plus d’informations, voir [la machine virtuelle N-tier architecture de référence](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier).

Bien que la virtualisation et l’infrastructure en tant que service (IaaS) répondent à de nombreuses préoccupations, elle laisse encore beaucoup de responsabilités entre les mains de l’équipe d’infrastructure. L’équipe maintient les versions du système d’exploitation, applique des correctifs de sécurité et installe des dépendances tierces sur les machines cibles. Les applications se comportent souvent différemment sur les machines de production par rapport à l’environnement de test. Des problèmes surviennent en raison de différentes versions de dépendance et/ou des niveaux OS SKU. Bien que de nombreuses organisations déploient des applications N-Tier à ces cibles, de nombreuses entreprises bénéficient de déploiement à un modèle natif plus cloud tels que [Platform as a Service](#platform-as-a-service-paas). Les architectures avec microservices sont plus difficiles en raison des exigences d’échelle pour l’élasticité et la résilience.

Pour plus d’informations, voir [machines virtuelles](https://docs.microsoft.com/azure/virtual-machines/).

## <a name="platform-as-a-service-paas"></a>PaaS (Platform as a Service)

Platform as a Service (PaaS) offre des solutions configurées que les développeurs peuvent brancher directement. PaaS est un autre terme pour l’hébergement géré. Il élimine la nécessité de gérer le système d’exploitation de base, les correctifs de sécurité et, dans de nombreux cas, toute dépendance de tiers. Des exemples de plates-formes incluent des applications Web, des bases de données et des back ends mobiles.

PaaS aborde les défis communs à IaaS. PaaS permet au développeur de se concentrer sur le schéma de code ou de base de données plutôt que sur la façon dont il est déployé. Les avantages de PaaS comprennent :

- Payez pour les modèles d’utilisation qui éliminent les frais généraux d’investir dans les machines au ralenti.
- Déploiement direct et Amélioration de DevOps, intégration continue (CI) et livraison continue (CD).
- Mises à niveau automatiques, mises à jour et correctifs de sécurité.
- Échelle de bouton et échelle vers le haut (échelle élastique).

Le principal inconvénient de PaaS a traditionnellement été le verrouillage des fournisseurs. Par exemple, certains fournisseurs de PaaS ne prennent en charge que ASP.NET, Node.js ou d’autres langues et plates-formes spécifiques. Des produits comme Azure App Service ont évolué pour répondre à plusieurs plates-formes et prendre en charge une variété de langues et de cadres pour héberger des applications Web.

![Plateforme en tant qu’architecture de service](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>SaaS (Software as a Service)

Le logiciel en tant que service ou SaaS est hébergé de façon central et disponible sans installation ou provisionnement local. SaaS est souvent hébergé au-dessus de PaaS comme une plate-forme pour le déploiement de logiciels. SaaS fournit des services pour exécuter et se connecter avec les logiciels existants. SaaS est souvent spécifique à l’industrie et verticale. SaaS est souvent sous licence et fournit généralement un modèle client/serveur. La plupart des offres SaaS modernes utilisent des applications Web pour le client. Les entreprises considèrent généralement SaaS comme une solution d’affaires aux offres de licences. Il n’est pas souvent mis en œuvre comme considération d’architecture pour l’évolutivité et la maintenance d’une application. En effet, la plupart des solutions SaaS sont construites sur IaaS, PaaS, et / ou sans serveur back ends.

En savoir plus sur SaaS grâce à une [application d’échantillon](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app).

## <a name="containers-and-functions-as-a-service-faas"></a>Conteneurs et fonctions en tant que service (FaaS)

Les conteneurs sont une solution intéressante qui permet des avantages de paaS sans les frais généraux IaaS. Un conteneur est essentiellement un runtime qui contient l’essentiel simple nécessaire pour exécuter une application unique. Le noyau ou la partie centrale du système d’exploitation hôte et les services tels que le stockage sont partagés entre un hôte. Le noyau partagé permet aux conteneurs d’être légers (certains ne sont que des mégaoctets de taille, par rapport à la taille gigaoctet des machines virtuelles typiques). Avec les hôtes déjà en cours d’exécution, les conteneurs peuvent être lancés rapidement, facilitant une grande disponibilité. La possibilité de faire tourner les conteneurs rapidement fournit également des couches supplémentaires de résilience. Docker est l’une des implémentations les plus populaires des conteneurs.

Les avantages des conteneurs comprennent :

- Léger et portable
- Autonome donc pas besoin d’installer des dépendances
- Fournir un environnement cohérent quel que soit l’hôte (fonctionne exactement de la même façon sur un ordinateur portable que sur un serveur cloud)
- Peut être fourni rapidement pour l’échelle
- Peut être redémarré rapidement pour se remettre d’une défaillance

Un conteneur fonctionne sur un hôte de conteneur (qui à son tour peut fonctionner sur une machine en métal nu ou une machine virtuelle). Plusieurs conteneurs ou instances des mêmes conteneurs peuvent fonctionner sur un seul hôte. Pour une véritable défaillance et une résilience, les conteneurs doivent être mis à l’échelle entre les hôtes.

Pour plus d’informations sur les conteneurs Docker, voir [What is Docker](../microservices/container-docker-introduction/docker-defined.md).

La gestion des conteneurs entre les hôtes nécessite généralement un outil d’orchestration tel que Kubernetes. La configuration et la gestion des solutions d’orchestration peuvent ajouter des frais généraux et de la complexité supplémentaires aux projets. Heureusement, de nombreux fournisseurs de cloud fournissent des services d’orchestration grâce à des solutions PaaS pour simplifier la gestion des conteneurs.

L’image suivante illustre un exemple d’installation de Kubernetes. Les nœuds dans l’échelle d’adresse d’installation et l’échec. Ils exécutent des instances de conteneurs Docker qui sont gérées par le serveur principal. Le *kubelet* est le client qui transmet les commandes de Kubernetes à Docker.

![Kubernetes](./media/kubernetes-example.png)

Pour plus d’informations sur l’orchestration, voir [Kubernetes sur Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes).

Fonctions en tant que service (FaaS) est un service de conteneurs spécialisé qui est similaire à sans serveur. Une mise en œuvre spécifique de FaaS, appelée [OpenFaaS](https://github.com/openfaas/faas), se trouve au-dessus des conteneurs pour fournir des capacités sans serveur. OpenFaaS fournit des modèles qui emballent toutes les dépendances du conteneur nécessaires pour exécuter un morceau de code. L’utilisation de modèles simplifie le processus de déploiement du code en tant qu’unité fonctionnelle. OpenFaaS cible les architectures qui comprennent déjà des conteneurs et des orchestrateurs parce qu’il peut utiliser l’infrastructure existante. Bien qu’il fournisse des fonctionnalités sans serveur, il vous oblige spécifiquement à utiliser Docker et un orchestrateur.

## <a name="serverless"></a>Sans serveur

Une architecture sans serveur offre une séparation claire entre le code et son environnement d’hébergement. Vous implémentez le code dans une *fonction* qui est invoquée par un *déclencheur*. Après la sortie de cette fonction, toutes les ressources nécessaires peuvent être libérées. Le déclencheur peut être manuel, un processus chronométré, une demande HTTP ou un téléchargement de fichier. Le résultat de la gâchette est l’exécution du code. Bien que les plates-formes sans serveur varient, la plupart donnent accès à des API et des liaisons prédéfinises pour rationaliser des tâches telles que l’écriture dans une base de données ou des résultats de file d’attente.

Serverless est une architecture qui repose fortement sur l’abstraction de l’environnement hôte pour se concentrer sur le code. Il peut être considéré comme *moins serveur*.

Les solutions de conteneurs fournissent aux développeurs des scripts de construction existants pour publier du code sur des images prêtes pour serveur. D’autres implémentations utilisent les solutions PaaS existantes pour fournir une architecture évolutive.

L’abstraction signifie que l’équipe DevOps n’a pas à fournir ou gérer des serveurs, ni des conteneurs spécifiques. La plate-forme sans serveur héberge le code, que ce soit sous forme de script ou d’exécutables emballés construits avec un SDK connexe, et alloue les ressources nécessaires pour que le code s’métrique.

L’illustration suivante diagramme quatre composants sans serveur. Une demande HTTP fait fonctionner le code API Checkout. L’API Checkout insère le code dans une base de données, et l’insert déclenche plusieurs autres fonctions à exécuter pour effectuer des tâches telles que l’informatique des tâches et l’exécution de l’ordre.

![Implémentation sans serveur](./media/serverless-implementation.png)

Les avantages de serverless incluent :

- **Haute densité.** De nombreux cas du même code sans serveur peuvent s’exécuter sur le même hôte par rapport aux conteneurs ou aux machines virtuelles. Les instances s’étendent sur plusieurs hôtes et la résilience.
- **Micro-facturation.** La plupart des fournisseurs sans serveur facturent en fonction des exécutions sans serveur, permettant des économies massives dans certains scénarios.
- **Échelle instantanée.** Serverless peut évoluer pour faire correspondre les charges de travail automatiquement et rapidement.
- **Plus rapidement temps de mise sur le marché.** Les développeurs se concentrent sur le code et se déploient directement sur la plate-forme sans serveur. Les composants peuvent être libérés indépendamment les uns des autres.

Serverless est le plus souvent discuté dans le contexte du calcul, mais peut également s’appliquer aux données. Par exemple, [Azure SQL](https://docs.microsoft.com/azure/sql-database) et [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) fournissent toutes deux des bases de données cloud qui ne vous obligent pas à configurer des machines ou des clusters hôtes. Ce livre se concentre sur le calcul sans serveur.

## <a name="summary"></a>Résumé

Il ya un large éventail de choix disponibles pour l’architecture, y compris une approche hybride. Serverless simplifie l’approche, la gestion et le coût des fonctionnalités d’application au détriment du contrôle et de la portabilité. Cependant, de nombreuses plates-formes sans serveur exposent la configuration pour aider à affiner la solution. Les bonnes pratiques de programmation peuvent également conduire à plus de code portable et moins de verrouillage de plate-forme sans serveur. Le tableau suivant illustre les approches d’architecture côte à côte. Choisissez sans serveur en fonction de vos besoins d’échelle, si oui ou non vous voulez gérer le temps d’exécution, et comment vous pouvez briser vos charges de travail en petits composants. Vous en apprendrez davantage sur les défis potentiels avec les points de décision sans serveur et d’autres dans le prochain chapitre.

|         |IaaS     |PaaS     |Conteneur|Sans serveur|
|---------|---------|---------|---------|----------|
|**Échelle**|Machine virtuelle       |Instance |Application      |Fonction  |
|**Résumés**|Matériel|Plateforme|Hôte OS|Runtime   |
|**Unité** |Machine virtuelle       |Projet  |Image    |Code      |
|**Vie**|Mois|Jours à mois|Minutes à jours|Millisecondes à Minutes|
|**Responsabilité**|Applications, dépendances, temps d’exécution et système d’exploitation|Applications et dépendances|Applications, dépendances et temps d’exécution|Fonction

- **L’échelle** se réfère à l’unité qui est utilisée pour mettre à l’échelle l’application
- **Les résumés** se réfèrent à la couche qui est abstraite par la mise en œuvre
- **L’unité** se réfère à la portée de ce qui est déployé
- **La durée** de vie se réfère au temps d’exécution typique d’une instance spécifique
- **La responsabilité** se réfère aux frais généraux pour construire, déployer et maintenir l’application

Le chapitre suivant portera sur l’architecture sans serveur, les cas d’utilisation et les modèles de conception.

## <a name="recommended-resources"></a>Ressources recommandées

- [Guide d’architecture d’application Azure](https://docs.microsoft.com/azure/architecture/guide/)
- [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)
- [Azure SQL](https://docs.microsoft.com/azure/sql-database)
- [Modèle d’architecture N-Tier](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
- [Kubernetes sur Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes)
- [Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
- [Architecture de référence de N-tier machine virtuelle](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
- [Machines virtuelles](https://docs.microsoft.com/azure/virtual-machines/)
- [Qu’est-ce que Docker ?](../microservices/container-docker-introduction/docker-defined.md)
- [Application Wingtip Tickets SaaS](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[Suivant précédent](architecture-approaches.md)
>[Next](serverless-architecture.md)
