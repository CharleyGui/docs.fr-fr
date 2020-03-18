---
title: Terminologie Docker
description: Architecture des microservices .NET pour les applications .NET en conteneur | Terminologie Docker
ms.date: 01/30/2020
ms.openlocfilehash: 5ffc7e791df8cbc999c6ababf62670bae46e1d5e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502837"
---
# <a name="docker-terminology"></a>Terminologie Docker

Cette section liste les termes et les définitions que vous devez connaître avant d’explorer Docker de manière plus approfondie. Pour obtenir d’autres définitions, consultez le [glossaire](https://docs.docker.com/glossary/) complet fourni par Docker.

**Image conteneur (container image)** : package de toutes les dépendances et informations nécessaires pour créer un conteneur. Une image inclut toutes les dépendances (notamment les frameworks) ainsi que la configuration de déploiement et d’exécution à utiliser par le runtime du conteneur. En règle générale, une image est dérivée de plusieurs images de base qui sont empilées en couches pour former le système de fichiers du conteneur. Une image est immuable une fois qu’elle a été créée.

**Dockerfile** : fichier texte contenant des instructions pour la création d’une image Docker. C’est comme un script de commandes, la première ligne indique l’image de base avec laquelle commencer, puis suivez les instructions pour installer les programmes requis, copier les fichiers et ainsi de suite, jusqu’à ce que vous obteniez l’environnement de travail dont vous avez besoin.

**Création (build)** : action de créer une image conteneur sur la base des informations et du contexte fournis par le fichier Dockerfile associé, plus des fichiers supplémentaires dans le dossier où l’image est créée. Vous pouvez créer des images à l’aide de la commande **docker build** de Docker.

**Conteneur (container)** : instance d’une image Docker. Un conteneur représente l’exécution d’une application, d’un processus ou d’un service. Il renferme une image Docker, un environnement d’exécution et un ensemble standard d’instructions. Pour mettre un service à l’échelle, vous créez plusieurs instances d’un conteneur à partir de la même image. Cela peut également être fait par un traitement par lots, qui passe des paramètres différents à chaque instance.

**Volumes** : offre un système de fichiers accessible en écriture que le conteneur peut utiliser. Dans la mesure où les images sont en lecture seule, mais que la plupart des programmes ont besoin d’écrire dans le système de fichiers, les volumes ajoutent une couche accessible en écriture, par-dessus l’image de conteneur, afin que les programmes aient accès à un système de fichiers accessible en écriture. Le programme ne sait pas qu’il accède à un système de fichiers en couches, il s’agit simplement du système de fichiers normal. Les volumes résident dans le système hôte et sont gérés par Docker.

**Balise (tag)** : marque ou étiquette que vous pouvez appliquer aux images pour identifier les différentes images ou versions de l’image initiale (selon le numéro de version de l’environnement cible).

**Build en plusieurs étapes** : fonctionnalité, depuis Docker 17.05 ou une version ultérieure, qui permet de réduire la taille des images finales. En quelques phrases, avec un build en plusieurs étapes vous pouvez utiliser, par exemple, une grande image de base, qui contient le SDK pour compiler et publier l’application, puis utilisez le dossier de publication avec une petite image de base runtime uniquement, pour produire une image finale beaucoup plus petite

**Dépôt (repository)** : collection d’images Docker associées, identifiées par une balise qui indique la version de chaque image. Certains repos contiennent plusieurs variantes d’une image spécifique, comme une image contenant des SDK (plus lourd), une image contenant uniquement des runtimes (plus léger), etc. Ces variantes peuvent être marquées avec des étiquettes. Un dépôt peut contenir des variantes de plateforme, comme une image Linux et une image Windows.

**Registre (registry)** : service qui fournit l’accès aux dépôts. Le registre par défaut utilisé pour la plupart des images publiques est [Docker Hub](https://hub.docker.com/) (propriété de l’organisation Docker). Un registre contient généralement des dépôts de plusieurs équipes. Les entreprises utilisent souvent des registres privés pour stocker et gérer les images qu’elles ont créées. Azure Container Registry est un autre exemple de registre.

**Image multi-arc**: Pour la multi-architecture, c’est une fonctionnalité qui simplifie la sélection de l’image appropriée, selon la plate-forme où Docker est en cours d’exécution. Par exemple, lorsqu’un Dockerfile demande une image de base **de mcr.microsoft.com/dotnet/core/sdk:3.1** du registre, il obtient en fait **3,1-sdk-nanoserver-1909**, **3.1-sdk-nanoserver-1809** ou **3.1-sdk-buster-slim**, selon le système d’exploitation et la version où Docker est en cours d’exécution.

**Docker Hub** : registre public dans lequel vous pouvez charger et manipuler des images. Docker Hub fournit un hébergement d’images Docker, des registres publics ou privés, des déclencheurs de build et des webhooks, et l’intégration avec GitHub et Bitbucket.

**Azure Container Registry** : ressource publique permettant d’utiliser des images Docker et leurs composants dans Azure. Vous disposez ainsi d’un registre au plus près de vos déploiements dans Azure, qui vous permet de contrôler l’accès avec vos groupes et autorisations Azure Active Directory existants.

**Docker Trusted Registry (DTR)** : service de registre Docker (fourni par Docker) qui peut être installé en local pour résider au sein même du centre de données et du réseau de l’organisation. Il est pratique pour les images privées devant être gérées en interne dans l’entreprise. Docker Trusted Registry est intégré au produit Docker Datacenter. Pour plus d’informations, consultez [Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE)** : outils de développement pour Windows et macOS permettant de créer, d’exécuter et de tester des conteneurs localement. Docker CE pour Windows fournit des environnements de développement pour les conteneurs Linux et Windows. L’hôte Linux Docker sur Windows est basé sur une machine virtuelle [Hyper-V](https://www.microsoft.com/cloud-platform/server-virtualization). L’hôte pour les conteneurs Windows est directement basé sur Windows. Docker CE pour Mac est basé sur le framework Hypervisor d’Apple et [l’hyperviseur xhyve](https://github.com/mist64/xhyve), qui fournit une machine virtuelle hôte Linux Docker sur Mac OS X. Docker CE pour Windows et pour Mac remplace Docker Toolbox, qui était basé sur Oracle VirtualBox.

**Docker Enterprise Edition (EE)** : version pour l’entreprise qui fournit des outils Docker pour le développement Linux et Windows.

**Compose** : outil en ligne de commande et format de fichier YAML fournissant des métadonnées pour la définition et l’exécution d’applications multiconteneurs. Vous définissez une application basée sur plusieurs images avec un ou plusieurs fichiers .yml qui peuvent remplacer les valeurs en fonction de l’environnement. Après avoir créé les définitions, vous déployez l’application multiconteneurs entière à l’aide d’une seule commande (docker-compose up) qui crée un conteneur par image sur l’hôte Docker.

**Cluster** : collection d’hôtes Docker exposés en tant qu’hôte Docker virtuel unique, ce qui permet la mise à l’échelle de l’application en fonction du nombre d’instances des services répartis entre les différents hôtes au sein du cluster. Vous pouvez créer des clusters Docker avec Kubernetes, Azure Service Fabric, Docker Swarm et Mesosphere DC/OS.

**Orchestrator** : outil qui simplifie la gestion des clusters et des hôtes Docker. Les orchestrateurs vous permettent de gérer leurs images, conteneurs et hôtes à travers un CLI ou une interface utilisateur graphique. Vous pouvez gérer la mise en réseau des conteneurs, les configurations, l’équilibrage de charge, la découverte des services, la haute disponibilité, la configuration des hôtes Docker, et bien plus encore. Un orchestrateur gère l’exécution, la distribution, la mise à l’échelle et la réparation des charges de travail dans une collection de nœuds. En règle générale, les produits Orchestrator sont les mêmes produits qui fournissent l’infrastructure de cluster, comme Kubernetes et Azure Service Fabric, entre autres offres sur le marché.

>[!div class="step-by-step"]
>[Suivant précédent](docker-defined.md)
>[Next](docker-containers-images-registries.md)
