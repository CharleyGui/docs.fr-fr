---
title: Déployer des applications .NET existantes en tant que conteneurs Windows
description: Moderniser des applications .NET existantes avec des conteneurs de Cloud Azure et Windows | Déployer des applications .NET existantes en tant que conteneurs de Windows
ms.date: 04/29/2018
ms.openlocfilehash: ba9af3fc3a5bf285830bb873fa6a5da8390dc6b4
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758833"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Déployer des applications .NET existantes en tant que conteneurs Windows

Les déploiements qui sont basées sur les conteneurs Windows sont appliquent aux applications optimisé pour le Cloud et applications Cloud natives.

Toutefois, dans ce guide et en particulier dans les sections suivantes, elle principalement se concentre sur l’utilisation de conteneurs Windows pour *optimisé pour le Cloud* applications où vous n’avez pas besoin de remanier votre application.

## <a name="what-are-containers-linux-or-windows"></a>Quelles sont les conteneurs ? (Windows ou Linux)

Les conteneurs sont un moyen d’encapsuler une application dans son propre package isolé. Dans son conteneur, l’application n’est pas affectée par les applications ou les processus qui existent en dehors du conteneur. Tout ce que l’application varie pour exécuter avec succès comme un processus est à l’intérieur du conteneur. Partout où le conteneur peut déplacer, la configuration requise de l’application sera toujours respectée, en termes de dépendances directes, car il est fourni avec tout ce qu’il doit s’exécuter (dépendances de bibliothèque de runtimes et ainsi de suite).

La principale caractéristique d’un conteneur est qu’elle rend l’environnement le même entre les différents déploiements car le conteneur lui-même est fourni avec toutes les dépendances dont il a besoin. Vous pouvez déboguer l’application sur votre ordinateur et puis le déployer sur un autre ordinateur, avec le même environnement garanti.

Un conteneur est une instance d’une image de conteneur. Une image de conteneur est un moyen d’empaqueter une application ou un service (par exemple, un instantané), puis le déployer de manière fiable et reproductible. Vous pouvez dire que Docker n’est pas qu'une technologie uniquement-it l’également une philosophie et un processus.

Comme tous les jours, les conteneurs devenant plus courants, ils deviennent un secteur « unité de déploiement ».

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Avantages des conteneurs (moteur Docker sur Linux ou Windows)

Création d’applications à l’aide de conteneurs qui peut-être également être défini en tant que blocs de construction légers-offers une augmentation significative en agilité pour la création, expédition et l’exécution de n’importe quelle application, sur n’importe quelle infrastructure.

Avec des conteneurs, vous pouvez prendre n’importe quelle application à partir de développement en production avec peu ou aucune modification de code, grâce à l’intégration Docker sur les outils de développement Microsoft, de systèmes d’exploitation et de cloud.

Lorsque vous déployez sur les machines virtuelles ordinaires, vous disposez probablement déjà une méthode en place pour le déploiement d’applications ASP.NET sur vos machines virtuelles. Cependant, il est probable, que votre méthode implique plusieurs étapes manuelles ou automatisées des processus complexes à l’aide d’un outil de déploiement comme Puppet, ou un outil similaire. Vous devrez peut-être effectuer des tâches telles que la modification des éléments de configuration, copie le contenu de l’application entre les serveurs et l’exécution des programmes d’installation interactive basées sur les installations .msi, suivies de test. Toutes ces étapes dans le déploiement ajoutent temps et risques aux déploiements. Vous obtiendrez des erreurs chaque fois qu’une dépendance n’est pas présente dans l’environnement cible.

Dans des conteneurs Windows, le processus d’empaquetage d’applications est entièrement automatisé. Les conteneurs Windows est basée sur la plateforme Docker, qui offre des mises à jour automatiques et les restaurations pour les déploiements de conteneur. La principale amélioration que vous obtenez de l’utilisation du moteur Docker est que vous créez des images, qui sont, comme des instantanés de votre application, avec toutes ses dépendances. Les images sont des images Docker (image de conteneur Windows, dans ce cas). Les images d’exécuter des applications ASP.NET dans des conteneurs, sans avoir à revenir au code source. L’instantané du conteneur devient l’unité de déploiement.

De nombreuses organisations sont CONTENEURISATION des applications monolithiques existantes pour les raisons suivantes :

- **Mise en production de la souplesse via un déploiement amélioré**. Les conteneurs offrent un contrat d’un déploiement cohérent entre le développement et les opérations. Lorsque vous utilisez des conteneurs, vous entendez les développeurs dire, « Ça marche sur ma machine, pourquoi ne pas en production ? » Ils peuvent par exemple « Il s’exécute en tant que conteneur, afin qu’il s’exécute en production. » L’application empaquetée, avec toutes ses dépendances, peut être exécutée dans n’importe quel environnement basé sur des conteneurs pris en charge. Il s’exécutera la façon qu'il a été destiné à exécuter dans toutes les cibles de déploiement (développement, test, intermédiaire et de production). Conteneurs éliminent la plupart des frictions lorsqu’ils passent d’une étape à l’autre, ce qui améliore considérablement le déploiement, et vous pouvez expédier plus rapidement.

- **Réduction des coûts**. Conteneurs contribuer à réduire les coûts, soit par la consolidation et la suppression de matériel existant, ou à partir de l’exécution des applications à une densité plus élevée par unité du matériel.

- **Portabilité**. Les conteneurs sont modulaire et portable. Conteneurs docker sont pris en charge sur n’importe quel système d’exploitation server (Linux et Windows), dans n’importe quel cloud majeure (Microsoft Azure, Amazon AWS, Google, IBM) et en local et privé ou les environnements de cloud hybride.

- **Contrôle**. Les conteneurs offrent un environnement flexible et sécurisé qui est contrôlé au niveau du conteneur. Un conteneur peut être sécurisé, isolé et même limité en définissant des stratégies de contrainte d’exécution sur le conteneur. Comme indiqué dans la section sur les conteneurs Windows, les conteneurs Windows Server 2016 et Hyper-V offrent des options de support d’entreprise.

Des améliorations significatives dans la portabilité, flexibilité et le contrôle entraîner importantes réductions de coûts lorsque vous utilisez des conteneurs pour développer et maintenir des applications.

## <a name="what-is-docker"></a>Qu’est-ce que Docker ?

[Docker](https://www.docker.com/) est un [projet open source](https://github.com/docker/docker) qui automatise le déploiement d’applications en tant que conteneurs portables et autonomes pouvant s’exécuter dans le nuage ou sur site. Docker est également une [société](https://www.docker.com/) qui promeut et fait évoluer cette technologie. La société travaille en collaboration avec le cloud, Linux et les fournisseurs de Windows, y compris Microsoft.

![](./media/image6.png)

> **Figure 4-6.** Docker déploie des conteneurs à toutes les couches du cloud hybride

À une personne familiarisé avec les machines virtuelles, conteneurs peuvent sembler être remarquablement similaires. Un conteneur exécute un système d’exploitation, a un système de fichiers et sont accessibles via un réseau, tout comme un système d’ordinateur physique ou virtuel. Toutefois, la technologie et les concepts derrière les conteneurs sont considérablement différents à partir de machines virtuelles. À partir du point de vue du développeur, un conteneur doit être traité plus comme un processus unique. En fait, un conteneur comporte un point d’entrée unique pour un processus.

Conteneurs docker (par souci de simplicité, *conteneurs*) peuvent s’exécuter en mode natif sur Linux et Windows. Lors de l’exécution régulières conteneurs, les conteneurs Windows peuvent exécuter uniquement sur les hôtes Windows (un serveur hôte ou une machine virtuelle), et des conteneurs Linux peuvent s’exécuter uniquement sur les hôtes Linux. Toutefois, dans les versions récentes des conteneurs Windows Server et Hyper-V, un conteneur Linux également peut s’exécuter en mode natif sur Windows Server à l’aide de la technologie d’isolation Hyper-V qui est actuellement disponible uniquement dans les conteneurs Windows Server.

Dans un avenir proche, les environnements mixtes qui ont des conteneurs Linux et Windows sera possible et même courant.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Avantages de Windows conteneurs pour vos applications .NET existantes

Les avantages de l’utilisation de conteneurs de Windows sont fondamentalement les mêmes avantages que vous obtenez à partir de conteneurs en général. À l’aide de conteneurs de Windows est sur ce qui améliore considérablement la portabilité, flexibilité et le contrôle.

Les applications .NET existantes font référence à ces applications qui ont été créées à l’aide de .NET Framework. Par exemple, elles sont peut-être les applications web ASP.NET traditionnelles-ils n’utilisent pas .NET Core, qui est plus récente et exécuter sur plusieurs plateformes sur Linux, Windows et MacOS.

La dépendance principale dans le .NET Framework est Windows. Il possède également des dépendances secondaire, tels que IIS et System.Web dans ASP.NET traditionnel.

Une application .NET Framework doit exécuter sur Windows, de la période. Si vous souhaitez mettre en conteneur des applications .NET Framework existantes et vous ne pouvez pas ou ne souhaitez pas investir dans une migration vers .NET Core (« si cela fonctionne correctement, ne pas migrer il »), le seul choix que vous avez des conteneurs est d’utiliser les conteneurs Windows.

Ainsi, un des principaux avantages des conteneurs de Windows est qu’ils vous offrent un moyen de moderniser vos applications .NET Framework existantes qui sont exécutent sur Windows via la mise en conteneur. Au final, les conteneurs Windows Obtient les avantages que vous cherchez à l’aide de la souplesse de conteneurs, la portabilité et un meilleur contrôle.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Choisissez un système d’exploitation cibler avec. Conteneurs NET

Étant donné la diversité des systèmes d’exploitation pris en charge par Docker, ainsi que les différences entre .NET Framework et .NET Core, vous devez cibler un système d’exploitation spécifique et basées sur le framework que vous utilisez des versions spécifiques.

Pour Windows, vous pouvez utiliser Windows Server Core ou Windows Nano Server. Ces versions de Windows offrent des caractéristiques différentes (par exemple, IIS par rapport à un serveur web auto-hébergé comme Kestrel) qui peuvent être nécessaires aux applications .NET Framework ou .NET Core.

Pour Linux, plusieurs distributions sont disponibles et prises en charge dans les images .NET Docker officielles (comme Debian).

Figure 4-7 illustre les versions de système d’exploitation que vous pouvez cibler, selon la version du .NET Framework.

![](./media/image7.png)

> **Figure 4-7.** Systèmes d’exploitation à cibler en fonction de la version du .NET Framework

Dans les scénarios de migration des applications héritées ou existantes qui reposent sur des applications .NET Framework, les dépendances principales sont sur Windows et IIS. Votre seule option consiste à utiliser des images Docker basées sur Windows Server Core et .NET Framework.

Lorsque vous ajoutez le nom de l’image à votre fichier Dockerfile, vous pouvez sélectionner le système d’exploitation et la version à l’aide d’une balise, comme dans les exemples suivants pour les images de conteneur Windows basée sur .NET Framework :

> | **Tag** | **Version du système et** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | .NET framework 4.x sur Windows Server Core |
> | **microsoft/aspnet:4.x-windowsservercore** | .NET framework 4.x avec une personnalisation supplémentaire ASP.NET, sur Windows Server Core |

Pour .NET Core (multiplateforme pour Linux et Windows), les balises seraient présente comme suit :

> | **Tag** | **Version du système et**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | .NET core 2.0 runtime uniquement sur Linux |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | .NET core 2.0 runtime uniquement sur Windows Nano Server |

### <a name="multi-arch-images"></a>Images multi-arch

Depuis la mi-année 2017, vous pouvez également utiliser une nouvelle fonctionnalité dans Docker appelé [multi-arch](https://github.com/moby/moby/issues/15866) images. Images Docker .NET core peuvent utiliser des balises multi-arch. Votre fichier Dockerfile les fichiers n’est plus nécessaire de définir le système d’exploitation que vous ciblez. La fonctionnalité multi-ARCHE permet une balise unique à utiliser dans plusieurs configurations d’ordinateur. Par exemple, avec multi-arch, vous pouvez utiliser une balise courantes : **microsoft/dotnet:2.0.0-runtime**. Si vous extrayez cette étiquette à partir d’un environnement de conteneur Linux, vous obtenez l’image basées sur Debian. Si vous extrayez cette étiquette à partir d’un environnement de conteneur Windows, vous obtenez l’image de Nano Server.

Pour les images de .NET Framework, le .NET Framework classique prend en charge uniquement Windows, vous ne pouvez pas utiliser la fonctionnalité multi-ARCHE.

## <a name="windows-container-types"></a>Types de conteneurs Windows

Comme les conteneurs Linux, conteneurs Windows Server sont gérés à l’aide du moteur Docker. Contrairement aux conteneurs Linux, les conteneurs Windows incluent deux différents types de conteneurs, ou exécutent des conteneurs fois-Windows Server et isolation Hyper-V.

**Conteneurs Windows Server**: Fournit l’isolation des applications via une technologie d’isolation des processus et l’espace de noms. Un conteneur Windows Server partage un noyau avec l’hôte de conteneur et tous les conteneurs en cours d’exécution sur l’ordinateur hôte. Ces conteneurs ne fournissent pas d’une limite de sécurité hostile et ne doivent pas servir à isoler le code non fiable. En raison de l’espace de noyau partagé, ces conteneurs nécessitent la même version de noyau et de la configuration.

**Isolation Hyper-V**: Développe l’isolation fournie par les conteneurs Windows Server en exécutant chaque conteneur sur une machine virtuelle hautement optimisée. Dans cette configuration, le noyau de l’hôte de conteneur n’est pas partagé avec d’autres conteneurs sur le même hôte. Ces conteneurs sont conçus pour hostile mutualisées d’hébergement, avec les mêmes garanties de sécurité d’une machine virtuelle. Étant donné que ces conteneurs ne partagent le noyau avec l’hôte ou d’autres conteneurs sur l’ordinateur hôte, ils peuvent exécuter des noyaux avec différentes versions et les configurations (avec les versions prises en charge). Par exemple, tous les conteneurs Windows sur Windows 10 permet d’isolation Hyper-V utilisent la version du noyau de Windows Server et la configuration.

Exécution d’un conteneur sur Windows avec ou sans isolation Hyper-V est une décision d’exécution. Vous pouvez choisir de créer le conteneur avec l’isolation Hyper-V initialement et en cours d’exécution, choisir d’exécuter à la place comme un conteneur Windows Server.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Documentation sur les conteneurs de Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Principes de base de conteneurs de Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **Infographie : Microsoft et les conteneurs**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>L’écosystème de conteneurs dans Azure

Dans les sections précédentes, il a été expliqué quels sont les avantages des conteneurs Docker, ainsi que des détails sur les images de conteneur spécifique pour les applications .NET. Obtenir des informations générales que sont essentielle afin de développer ou conteneuriser une application.
Toutefois, lorsque vous réfléchissez à l’environnement de déploiement de production ou même des environnements de l’assurance qualité et développement/Test, Microsoft Azure fournit une ouverte et large variété de choix, un écosystème de conteneurs complète dans le cloud (indiqué dans le diagramme ci-dessous). En fonction des besoins spécifiques de votre application, vous devez choisir un ou un autre produit Azure.

![](./media/image7.5.png)

> **Figure 4-7.5.** L’écosystème de conteneurs dans Azure

À partir de l’écosystème de conteneurs dans Azure, les produits suivants est prise en charge des conteneurs qui sont considérés comme infrastructure :
- **Azure Container Instances (ACI)**
- **Machines virtuelles** (avec prise en charge du conteneur)
- **Azure Virtual Machine Scale Sets** (avec prise en charge du conteneur)

À partir de ces trois, ACI fournit un énorme avantage, le fait que vous n’avez pas besoin de mettre à jour le système d’exploitation sous-jacent, sans devoir vous/correctif de mise à niveau, etc. mais ACI est toujours placé dans le niveau de l’infrastructure, comme expliqué mieux dans les sections à venir de ce livre.

Les produits dans des conteneurs de prise en charge Azure qui sont à la fois positionnée plus dans le PaaS (plateforme en tant que Service) au niveau sont :

- **Azure App Service**
- **Azure Kubernetes Service (AKS et ACS)**
- **Azure Batch** 

Ensuite, Azure Container Registry est un Registre de conteneur évolutifs haute hébergé dans Azure que vous pouvez utiliser à partir de tous les produits précédents lors de l’inscription et le déploiement de vos images de conteneur personnalisé.

En outre, à partir de vos conteneurs, vous pouvez utiliser les autres services gérés dans Azure comme Azure SQL Database, cache Redis Azure, Azure Cosmos DB, etc. en outre solutions/plateformes tierces sont disponibles dans Azure Marketplace, tels que Cloud Foundry et OpenShift où vous pouvez également utiliser des conteneurs dans Azure. 

Dans les sections suivantes, vous pouvez explorer les recommandations de Microsoft sur comment utiliser chacune de ces produits et solutions Azure en particulier lorsque vous ciblez les conteneurs Windows.

>[!div class="step-by-step"]
>[Précédent](what-about-cloud-native-applications.md)
>[Suivant](when-not-to-deploy-to-windows-containers.md)
