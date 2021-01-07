---
title: Terminologie Docker
description: Découvrez la terminologie de base qui entoure l’utilisation quotidienne de Docker.
ms.date: 01/06/2021
ms.openlocfilehash: 640c3481e271b8fe2b7d7eeb7d5eaeb02af1cc21
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970100"
---
# <a name="docker-terminology"></a>Terminologie Docker

Cette section liste les termes et les définitions que vous devez connaître avant d’explorer Docker de manière plus approfondie. Pour obtenir d’autres définitions, consultez le [glossaire](https://docs.docker.com/glossary/) complet fourni par Docker.

**Image conteneur (container image)** : package de toutes les dépendances et informations nécessaires pour créer un conteneur. Une image inclut toutes les dépendances (notamment les frameworks) ainsi que la configuration de déploiement et d’exécution à utiliser par le runtime du conteneur. En règle générale, une image est dérivée de plusieurs images de base qui sont empilées en couches pour former le système de fichiers du conteneur. Une image est immuable une fois qu’elle a été créée.

**Fichier dockerfile**: fichier texte qui contient des instructions pour la génération d’une image de l’ancrage. C’est comme un script de commandes, la première ligne indique l’image de base avec laquelle commencer, puis suivent les instructions pour installer les programmes requis, copier les fichiers, etc. jusqu’à obtenir l’environnement de travail dont vous avez besoin.

**Création (build)** : action de créer une image conteneur sur la base des informations et du contexte fournis par le fichier Dockerfile associé, plus des fichiers supplémentaires dans le dossier où l’image est créée. Vous pouvez créer des images à l’aide de la commande Dockr suivante :

```bash
docker build
```

**Conteneur (container)** : instance d’une image Docker. Un conteneur représente l’exécution d’une application, d’un processus ou d’un service. Il renferme une image Docker, un environnement d’exécution et un ensemble standard d’instructions. Pour mettre un service à l’échelle, vous créez plusieurs instances d’un conteneur à partir de la même image. Cela peut également être fait par un traitement par lots, qui passe des paramètres différents à chaque instance.

**Volumes** : offre un système de fichiers accessible en écriture que le conteneur peut utiliser. Dans la mesure où les images sont en lecture seule, mais que la plupart des programmes ont besoin d’écrire dans le système de fichiers, les volumes ajoutent une couche accessible en écriture, par-dessus l’image de conteneur, afin que les programmes aient accès à un système de fichiers accessible en écriture. Le programme ne sait pas qu’il accède à un système de fichiers en couches, il s’agit simplement du système de fichiers normal. Les volumes résident dans le système hôte et sont gérés par Docker.

**Balise (tag)** : marque ou étiquette que vous pouvez appliquer aux images pour identifier les différentes images ou versions de l’image initiale (selon le numéro de version de l’environnement cible).

**Build en plusieurs étapes** : fonctionnalité, depuis Docker 17.05 ou une version ultérieure, qui permet de réduire la taille des images finales. Par exemple, une grande image de base contenant le kit de développement logiciel (SDK) peut être utilisée pour la compilation et la publication, puis une petite image de base Runtime only peut être utilisée pour héberger l’application.

**Dépôt (repository)** : collection d’images Docker associées, identifiées par une balise qui indique la version de chaque image. Certains dépôts contiennent plusieurs variantes d’une image spécifique, telles qu’une image contenant des kits de développement logiciel (lourd), une image contenant uniquement des runtimes (plus légère), etc. Ces variantes peuvent être marquées avec des balises. Un dépôt peut contenir des variantes de plateforme, comme une image Linux et une image Windows.

**Registre (registry)** : service qui fournit l’accès aux dépôts. Le registre par défaut utilisé pour la plupart des images publiques est [Docker Hub](https://hub.docker.com/) (propriété de l’organisation Docker). Un registre contient généralement des dépôts de plusieurs équipes. Les entreprises utilisent souvent des registres privés pour stocker et gérer les images qu’elles ont créées. Azure Container Registry est un autre exemple de registre.

**Image multi-** architecture : pour l’architecture mutualisée, il s’agit d’une fonctionnalité qui simplifie la sélection de l’image appropriée, en fonction de la plateforme sur laquelle l’outil de connexion est en cours d’exécution. Par exemple, lorsqu’un fichier dockerfile demande une image **de base à partir de MCR.Microsoft.com/dotnet/SDK :5.0** à partir du Registre, il obtient en fait **5,0-**-20H2, **5,0-** -2004 ou **5,0-Buster-Slim**, en fonction du système d’exploitation et de la version où l’ordinateur est en cours d’exécution.

**Docker Hub** : registre public dans lequel vous pouvez charger et manipuler des images. Docker Hub fournit un hébergement d’images Docker, des registres publics ou privés, des déclencheurs de build et des webhooks, et l’intégration avec GitHub et Bitbucket.

**Azure Container Registry** : ressource publique permettant d’utiliser des images Docker et leurs composants dans Azure. Vous disposez ainsi d’un registre au plus près de vos déploiements dans Azure, qui vous permet de contrôler l’accès avec vos groupes et autorisations Azure Active Directory existants.

**Docker Trusted Registry (DTR)** : service de registre Docker (fourni par Docker) qui peut être installé en local pour résider au sein même du centre de données et du réseau de l’organisation. Il est pratique pour les images privées devant être gérées en interne dans l’entreprise. Docker Trusted Registry est intégré au produit Docker Datacenter. Pour plus d’informations, consultez [Docker Trusted Registry (DTR)](https://www.docker.com/sites/default/files/Docker%20Trusted%20Registry.pdf).

**Docker Community Edition (CE)** : outils de développement pour Windows et macOS permettant de créer, d’exécuter et de tester des conteneurs localement. Docker CE pour Windows fournit des environnements de développement pour les conteneurs Linux et Windows. L’hôte Linux Docker sur Windows est basé sur une machine virtuelle [Hyper-V](https://www.microsoft.com/cloud-platform/server-virtualization). L’hôte pour les conteneurs Windows est directement basé sur Windows. Docker CE pour Mac est basé sur le framework Hypervisor d’Apple et [l’hyperviseur xhyve](https://github.com/mist64/xhyve), qui fournit une machine virtuelle hôte Linux Docker sur Mac OS X. Docker CE pour Windows et pour Mac remplace Docker Toolbox, qui était basé sur Oracle VirtualBox.

**Docker Enterprise Edition (EE)** : version pour l’entreprise qui fournit des outils Docker pour le développement Linux et Windows.

**Compose** : outil en ligne de commande et format de fichier YAML fournissant des métadonnées pour la définition et l’exécution d’applications multiconteneurs. Vous définissez une application basée sur plusieurs images avec un ou plusieurs fichiers .yml qui peuvent remplacer les valeurs en fonction de l’environnement. Après avoir créé les définitions, vous déployez l’application multiconteneur entière à l’aide d’une seule commande (docker-compose up) qui crée un conteneur par image sur l’hôte Docker.

**Cluster** : collection d’hôtes Docker exposés en tant qu’hôte Docker virtuel unique, ce qui permet la mise à l’échelle de l’application en fonction du nombre d’instances des services répartis entre les différents hôtes au sein du cluster. Vous pouvez créer des clusters Docker avec Kubernetes, Azure Service Fabric, Docker Swarm et Mesosphere DC/OS.

**Orchestrator**: outil qui simplifie la gestion des clusters et des hôtes de l’arrimeur. Les orchestrateurs vous permettent de gérer les images, les conteneurs et les hôtes à l’aide d’une interface de ligne de commande (CLI) ou d’une interface graphique utilisateur. Vous pouvez gérer la mise en réseau des conteneurs, les configurations, l’équilibrage de charge, la découverte des services, la haute disponibilité, la configuration des hôtes Docker, et bien plus encore. Un orchestrateur gère l’exécution, la distribution, la mise à l’échelle et la réparation des charges de travail dans une collection de nœuds. En règle générale, les produits Orchestrator sont les mêmes produits qui fournissent l’infrastructure de cluster, comme Kubernetes et Azure Service Fabric, entre autres offres sur le marché.

>[!div class="step-by-step"]
>[Précédent](what-is-docker.md) 
> [Suivant](docker-containers-images-and-registries.md)
