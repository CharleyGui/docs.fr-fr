---
title: Déployer des applications .NET existantes en tant que conteneurs Windows
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Déployer les applications .NET existantes sous forme de conteneurs Windows
ms.date: 04/29/2018
ms.openlocfilehash: 28568ca363bfc8100f78b100f8a7f0242c4f04c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089557"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Déployer des applications .NET existantes en tant que conteneurs Windows

Les déploiements basés sur les conteneurs Windows s’appliquent aux applications Cloud-Optimized et aux applications Cloud-Native.

Cependant, dans ce guide et en particulier dans les sections suivantes, il se concentre principalement sur l’utilisation de conteneurs Windows pour les applications *cloud-Optimisées* où vous n’avez pas besoin de rearchitect votre application.

## <a name="what-are-containers-linux-or-windows"></a>Qu’est-ce qu’un conteneur ? (Linux ou Windows)

Les conteneurs sont un moyen de conclure une application dans son propre emballage isolé. Dans son conteneur, l’application n’est pas affectée par les applications ou les processus qui existent à l’extérieur du conteneur. Tout ce dont l’application dépend pour fonctionner avec succès comme un processus est à l’intérieur du conteneur. Partout où le conteneur peut se déplacer, les exigences de l’application seront toujours remplies, en termes de dépendances directes, parce qu’il est regroupé avec tout ce dont il a besoin pour fonctionner (dépendances de bibliothèque, runtimes, et ainsi de suite).

La principale caractéristique d’un conteneur est qu’il rend l’environnement le même à travers différents déploiements parce que le conteneur lui-même est livré avec toutes les dépendances dont il a besoin. Vous pouvez déboiffer l’application sur votre machine, puis la déployer sur une autre machine, avec le même environnement garanti.

Un conteneur est un exemple d’image de conteneur. Une image de conteneur est un moyen de package une application ou un service (comme un instantané), puis de la déployer d’une manière fiable et reproductible. On pourrait dire que Docker n’est pas seulement une technologie, c’est aussi une philosophie et un processus.

À mesure que les conteneurs deviennent plus courants, ils deviennent une « unité de déploiement » à l’échelle de l’industrie.

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Avantages des conteneurs (Moteur Docker sur Linux ou Windows)

Construire des applications en utilisant des conteneurs - qui peuvent également être définis comme des blocs de construction légers - offre une augmentation significative de l’agilité pour la construction, l’expédition et l’exécution de toute application, à travers n’importe quelle infrastructure.

Avec les conteneurs, vous pouvez prendre n’importe quelle application du développement à la production avec peu ou pas de changement de code, grâce à l’intégration Docker à travers les outils de développeur Microsoft, les systèmes d’exploitation et le cloud.

Lorsque vous vous déployez dans des VM simples, vous avez probablement déjà une méthode en place pour déployer ASP.NET applications dans vos VM. Il est probable, cependant, que votre méthode implique plusieurs étapes manuelles ou des processus automatisés complexes en utilisant un outil de déploiement comme Puppet, ou un outil similaire. Vous devrez peut-être effectuer des tâches telles que la modification d’éléments de configuration, la copie du contenu de l’application entre les serveurs et l’exécution de programmes de configuration interactifs basés sur des configurations .msi, suivies de tests. Toutes ces étapes du déploiement ajoutent du temps et des risques aux déploiements. Vous obtiendrez des échecs chaque fois qu’une dépendance n’est pas présente dans l’environnement cible.

Dans Windows Containers, le processus d’applications d’emballage est entièrement automatisé. Windows Containers est basé sur la plate-forme Docker, qui offre des mises à jour automatiques et des réductions pour les déploiements de conteneurs. La principale amélioration que vous obtenez de l’utilisation du moteur Docker est que vous créez des images, qui sont comme des instantanés de votre application, avec toutes ses dépendances. Les images sont des images Docker (une image de conteneur Windows, dans ce cas). Les images s’exécutent ASP.NET applications dans des conteneurs, sans revenir au code source. L’instantané du conteneur devient l’unité de déploiement.

De nombreuses organisations conteneurisent les applications monolithiques existantes pour les raisons suivantes :

- **Libérer l’agilité grâce à un déploiement amélioré**. Les conteneurs offrent un contrat de déploiement cohérent entre le développement et les opérations. Lorsque vous utilisez des conteneurs, vous n’entendrez pas les développeurs dire: «Cela fonctionne sur ma machine, pourquoi pas en production?" Ils peuvent dire : « Il fonctionne comme un conteneur, donc il fonctionnera en production. » L’application emballée, avec toutes ses dépendances, peut être exécutée dans n’importe quel environnement supporté à base de conteneurs. Il fonctionnera comme il était destiné à fonctionner dans toutes les cibles de déploiement (dev, QA, mise en scène, production). Les conteneurs éliminent la plupart des frictions lorsqu’ils se déplacent d’une étape à l’autre, ce qui améliore considérablement le déploiement, et vous pouvez expédier plus rapidement.

- **Réductions de coûts**. Les conteneurs entraînent des coûts plus bas, soit par la consolidation et la suppression du matériel existant, soit par l’exécution d’applications à une densité plus élevée par unité de matériel.

- **Portabilité**. Les conteneurs sont modulaires et portables. Les conteneurs Docker sont pris en charge sur n’importe quel système d’exploitation serveur (Linux et Windows), dans n’importe quel grand cloud public (Microsoft Azure, Amazon AWS, Google, IBM), et dans des environnements cloud privés ou hybrides.

- **Contrôle**. Les conteneurs offrent un environnement flexible et sécurisé qui est contrôlé au niveau du conteneur. Un conteneur peut être sécurisé, isolé et même limité en fixant des politiques de contrainte d’exécution sur le conteneur. Comme indiqué dans la section sur les conteneurs Windows, Windows Server 2016 et Hyper-V offrent des options de support d’entreprise supplémentaires.

Des améliorations significatives de l’agilité, de la portabilité et du contrôle entraînent en fin de compte des réductions de coûts importantes lorsque vous utilisez des conteneurs pour développer et entretenir des applications.

## <a name="what-is-docker"></a>Présentation de Docker

[Docker](https://www.docker.com/) est un [projet open-source](https://github.com/docker/docker) qui automatise le déploiement d’applications comme des conteneurs portables autosuffisants qui peuvent fonctionner dans le cloud ou sur place. Docker est également le nom de la [société](https://www.docker.com/) qui développe et diffuse cette technologie. La société travaille en collaboration avec les fournisseurs de cloud, Linux et Windows, y compris Microsoft.

![Diagramme montrant comment Docker déploie des conteneurs dans le nuage hybride.](./media/deploy-existing-net-apps-as-windows-containers/docker-deploys-containers-all-layers.png)

**Figure 4-6.** Docker déploie des conteneurs dans toutes les couches du cloud hybride

Pour quelqu’un familier avec les machines virtuelles, les conteneurs peuvent sembler être remarquablement similaires. Un conteneur fonctionne un système d’exploitation, dispose d’un système de fichiers et peut être consulté sur un réseau, tout comme un système informatique physique ou virtuel. Ceci dit, la technologie et les concepts derrière les conteneurs sont très différents de ceux des machines virtuelles. Du point de vue du développeur, un conteneur doit être traité davantage comme un seul processus. En fait, un conteneur a un seul point d’entrée pour un processus.

Les conteneurs Docker (pour la simplicité, *les conteneurs)* peuvent fonctionner localement sur Linux et Windows. Lors de l’exécution de conteneurs réguliers, les conteneurs Windows ne peuvent s’exécuter que sur les hôtes Windows (un serveur hôte ou un VM), et les conteneurs Linux ne peuvent s’exécuter que sur les hôtes Linux. Cependant, dans les versions récentes de Windows Server et des conteneurs Hyper-V, un conteneur Linux peut également fonctionner nativement sur Windows Server en utilisant la technologie d’isolement Hyper-V qui n’est actuellement disponible que dans Windows Server Containers.

Dans un proche avenir, les environnements mixtes qui ont à la fois des conteneurs Linux et Windows seront possibles et même communs.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Avantages des conteneurs Windows pour vos applications .NET existantes

Les avantages de l’utilisation de Windows Containers sont fondamentalement les mêmes avantages que vous obtenez des conteneurs en général. L’utilisation de Windows Containers consiste à améliorer considérablement l’agilité, la portabilité et le contrôle.

Les applications .NET existantes se réfèrent aux applications créées à l’aide du cadre .NET. Par exemple, ils peuvent être traditionnels ASP.NET applications Web- ils n’utilisent pas .NET Core, qui est plus récent et fonctionne en multi-plateforme sur Linux, Windows et MacOS.

La principale dépendance dans le cadre .NET est Windows. Il a également des dépendances secondaires, comme l’IIS, et System.Web dans les ASP.NET traditionnelles.

Une application cadre .NET doit s’exécuter sur Windows, point final. Si vous souhaitez conteneuriser les applications cadres .NET existantes et que vous ne pouvez pas ou ne voulez pas investir dans une migration vers .NET Core ("Si cela fonctionne correctement, ne le migrez pas"), le seul choix que vous avez pour les conteneurs est d’utiliser windows Containers.

Ainsi, l’un des principaux avantages de Windows Containers est qu’ils vous offrent un moyen de moderniser vos applications cadre .NET existantes qui sont en cours d’exécution sur la conteneurisation Windows-through. En fin de compte, Windows Containers vous tire les avantages que vous recherchez en utilisant des conteneurs d’agilité, de portabilité et d’un meilleur contrôle.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Choisissez un système d’exploitation à cibler avec . Conteneurs à base de NET

Compte tenu de la diversité des systèmes d’exploitation qui sont pris en charge par Docker, ainsi que les différences entre .NET Framework et .NET Core, vous devez cibler un système d’exploitation spécifique et des versions spécifiques basées sur le cadre que vous utilisez.

Pour Windows, vous pouvez utiliser Windows Server Core ou Windows Nano Server. Ces versions Windows fournissent différentes caractéristiques (comme IIS par rapport à un serveur Web auto-hébergé comme Kestrel) qui pourraient être nécessaires par .NET Framework ou .NET Core applications.

Pour Linux, plusieurs distributions sont disponibles et prises en charge dans les images .NET Docker officielles (comme Debian).

La figure 4-7 affiche les versions OS que vous pouvez cibler, selon la version de l’application du cadre .NET.

![Diagramme montrant ce que le système d’exploitation cibler basé sur la version cadre .NET.](./media/deploy-existing-net-apps-as-windows-containers/dotnet-framework-operating-systems.png)

**Figure 4-7.** Systèmes d’exploitation à cibler basés sur la version cadre .NET

Dans les scénarios de migration pour les applications existantes ou héritées qui sont basées sur des applications cadre .NET, les principales dépendances sont sur Windows et IIS. Votre seule option est d’utiliser des images Docker basées sur Windows Server Core et le cadre .NET.

Lorsque vous ajoutez le nom d’image à votre fichier Dockerfile, vous pouvez sélectionner le système d’exploitation et la version en utilisant une balise, comme dans les exemples suivants pour les images de conteneurs Windows basées sur le Cadre .NET :

> | **étiquette** | **Système et version** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | .NET Framework 4.x sur Windows Server Core |
> | **microsoft/aspnet:4.x-windowsservercore** | .NET Framework 4.x avec une personnalisation ASP.NET supplémentaire, sur Windows Server Core |

Pour .NET Core (plateforme croisée pour Linux et Windows), les balises ressembleraient à ce qui suit :

> | **étiquette** | **Système et version**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | .NET Core 2.0 runtime-seulement sur Linux |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | .NET Core 2.0 runtime-seulement sur Windows Nano Server |

### <a name="multi-arch-images"></a>Images multi-arcs

À partir de la mi-2017, vous pouvez également utiliser une nouvelle fonctionnalité dans Docker appelée images [multi-arc.](https://github.com/moby/moby/issues/15866) .NET Core Docker images peuvent utiliser des balises multi-arc. Vos fichiers Dockerfile n’ont plus besoin de définir le système d’exploitation que vous ciblez. La fonction multi-arc permet d’utiliser une seule balise sur plusieurs configurations de machines. Par exemple, avec multi-arch, vous pouvez utiliser une balise commune: **microsoft/dotnet:2.0.0-runtime**. Si vous tirez cette étiquette à partir d’un environnement de conteneur Linux, vous obtenez l’image basée sur Debian. Si vous tirez cette étiquette à partir d’un environnement de conteneur Windows, vous obtenez l’image basée sur Nano Server.

Pour les images cadre .NET, parce que le cadre traditionnel .NET ne prend en charge que Windows, vous ne pouvez pas utiliser la fonction multi-arc.

## <a name="windows-container-types"></a>Types de conteneurs Windows

Comme les conteneurs Linux, les conteneurs Windows Server sont gérés en utilisant Docker Engine. Contrairement aux conteneurs Linux, les conteneurs Windows comprennent deux types de conteneurs différents, ou exécuter des conteneurs De serveur Windows et l’isolement Hyper-V.

**Conteneurs Windows Server**: Fournit l’isolement des applications grâce à la technologie d’isolation du processus et de l’espace de nom. Un conteneur Windows Server partage un noyau avec l’hôte du conteneur et tous les conteneurs qui sont en cours d’exécution sur l’hôte. Ces conteneurs ne créent pas de frontière de sécurité contre le code hostile et ne doivent pas être utilisés pour isoler du code non fiable. En raison de l’espace de noyau partagé, ces conteneurs requièrent la même version et configuration de noyau.

**Isolation Hyper-V**: Élargit l’isolement fourni par Windows Server Containers en exécutant chaque conteneur sur un VM hautement optimisé. Dans cette configuration, le noyau de l’hôte de conteneur n’est pas partagé avec d’autres conteneurs exécutés sur l’hôte. Ces conteneurs sont conçus pour l’hébergement multitensif hostile, avec les mêmes garanties de sécurité d’un VM. Étant donné que ces conteneurs ne partagent pas le noyau avec l’hôte ou d’autres conteneurs sur l’hôte, ils peuvent exécuter des grains avec différentes versions et configurations (avec des versions prises en charge). Par exemple, tous les conteneurs Windows sur Windows 10 utilisent l’isolement Hyper-V pour utiliser la version et la configuration du noyau Windows Server.

L’exécution d’un conteneur sur Windows avec ou sans l’isolement Hyper-V est une décision de durée. Vous pouvez choisir de créer le conteneur avec l’isolement Hyper-V initialement, et au moment de l’exécution, choisissez de l’exécuter comme un conteneur Windows Server à la place.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Documentation Windows Containers**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Principes fondamentaux des conteneurs Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **Infographie: Microsoft et les conteneurs**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>L’écosystème des conteneurs en Azure

Dans les sections précédentes, il a été expliqué quels sont les avantages des conteneurs Docker ainsi que des détails sur les images de conteneurs spécifiques pour les applications .NET. Toute cette information générique est fondamentale afin de développer ou de conteneuriser une application.
Cependant, lorsqu’il s’agit de l’environnement de déploiement de la production ou même des environnements QA et Dev/Test, Microsoft Azure offre une variété ouverte et large de choix, un écosystème de conteneurs complet dans le nuage (indiqué dans le diagramme ci-dessous). En fonction des besoins de votre application spécifique, vous devez choisir l’un ou l’autre produit Azure.

![Diagramme de l’écosystème des conteneurs à Azure.](./media/deploy-existing-net-apps-as-windows-containers/azure-container-ecosystem.png)

**Figure 4-7.5.** L’écosystème des conteneurs en Azure

De l’écosystème des conteneurs d’Azure, les produits suivants supportent les conteneurs considérés comme des infrastructures :

- **Exemples de conteneurs Azure (ACI)**
- **Machines virtuelles Azure** (avec le soutien du conteneur)
- **Azure Virtual Machine Scale Sets** (Avec le support du conteneur)

De ces trois, ACI offre un grand avantage, qui est le fait que vous n’avez pas besoin de maintenir le système d’exploitation sous-jacent, pas besoin pour vous de mettre à niveau / patch, etc, mais ACI est toujours positionné dans le niveau de l’infrastructure, comme mieux expliqué dans les sections à venir de ce livre.

Les produits azuréens supportant les conteneurs qui sont en même temps positionnés davantage au niveau PaaS (Plateforme en tant que Service) sont les :

- **Service d’application Azure**
- **Azure Kubernetes Service (AKS et ACS)**
- **Azure Batch**

Ensuite, Azure Container Registry est un registre de conteneurs évolutif élevé hébergé en Azure que vous pouvez utiliser à partir de tous les produits précédents lors de l’enregistrement et le déploiement de vos images de conteneurs personnalisées.

De plus, à partir de vos conteneurs, vous pouvez consommer d’autres services gérés en Azure comme Azure SQL Database, Azure Redis cache, Azure Cosmos DB, etc. plus il existe des solutions/plates-formes tierces disponibles dans Azure Marketplace comme Cloud Foundry et OpenShift où vous pouvez également utiliser des conteneurs au sein d’Azure.

Dans les sections suivantes, vous pouvez explorer les recommandations de Microsoft sur le moment d’utiliser chacun de ces produits et solutions Azure spécifiquement lors du ciblage des conteneurs Windows.

>[!div class="step-by-step"]
>[Suivant précédent](what-about-cloud-native-applications.md)
>[Next](when-not-to-deploy-to-windows-containers.md)
