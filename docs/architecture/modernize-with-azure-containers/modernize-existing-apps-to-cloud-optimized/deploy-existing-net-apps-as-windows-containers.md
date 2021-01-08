---
title: Déployer des applications .NET existantes en tant que conteneurs Windows
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Déployer des applications .NET existantes en tant que conteneurs Windows
ms.date: 12/21/2020
ms.openlocfilehash: f3f164ca0578d5358f2c5365fd5a1d2e8e22d8c5
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025345"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Déployer des applications .NET existantes en tant que conteneurs Windows

Les déploiements basés sur des conteneurs Windows s’appliquent aux applications Cloud-Optimized et aux applications Cloud-Native.

Toutefois, dans ce guide, et en particulier dans les sections suivantes, il se concentre principalement sur l’utilisation des conteneurs Windows pour les applications *optimisées* pour le Cloud où vous n’avez pas besoin de remanier votre application.

## <a name="what-are-containers-linux-or-windows"></a>Que sont les conteneurs ? (Linux ou Windows)

Les conteneurs sont un moyen d’encapsuler une application dans son propre package isolé. Dans son conteneur, l’application n’est pas affectée par les applications ou les processus qui existent en dehors du conteneur. Tout ce dont dépend l’application pour s’exécuter correctement en tant que processus se trouve à l’intérieur du conteneur. Partout où le conteneur peut se déplacer, les exigences de l’application sont toujours respectées, en termes de dépendances directes, car elles sont regroupées avec tout ce dont elles ont besoin pour s’exécuter (dépendances de bibliothèque, runtimes, etc.).

La caractéristique principale d’un conteneur est qu’il rend l’environnement identique dans différents déploiements, car le conteneur lui-même est associé à toutes les dépendances dont il a besoin. Vous pouvez déboguer l’application sur votre ordinateur, puis la déployer sur un autre ordinateur, avec le même environnement garanti.

Un conteneur est une instance d’une image de conteneur. Une image de conteneur est un moyen d’empaqueter une application ou un service (par exemple, un instantané), puis de la déployer de manière fiable et reproductible. Vous pouvez affirmer que Dockr n’est pas seulement une technologie. il s’agit également d’une philosophie et d’un processus.

À mesure que les conteneurs sont plus courants, ils deviennent une unité de déploiement à l’ensemble du secteur.

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Avantages des conteneurs (moteur de l’amarrage sur Linux ou Windows)

La création d’applications à l’aide de conteneurs, qui peuvent également être définies en tant que blocs de construction légers, offre une augmentation significative de l’agilité pour la création, l’expédition et l’exécution d’applications, dans toute l’infrastructure.

Avec les conteneurs, vous pouvez faire passer n’importe quelle application du développement à la production avec peu ou pas de modifications de code, grâce à l’intégration de l’ancrer sur les outils de développement Microsoft, les systèmes d’exploitation et le Cloud.

Lorsque vous déployez sur des machines virtuelles ordinaires, vous avez probablement déjà une méthode en place pour déployer des applications ASP.NET sur vos machines virtuelles. Toutefois, il est probable que votre méthode implique plusieurs étapes manuelles ou des processus automatisés complexes à l’aide d’un outil de déploiement tel que marionnette ou d’un outil similaire. Vous devrez peut-être effectuer des tâches telles que la modification des éléments de configuration, la copie du contenu de l’application entre les serveurs et l’exécution de programmes d’installation interactifs basés sur des configurations. msi, puis le test. Toutes les étapes du déploiement ajoutent du temps et des risques aux déploiements. Vous obtiendrez des erreurs chaque fois qu’une dépendance n’est pas présente dans l’environnement cible.

Dans les conteneurs Windows, le processus de packaging des applications est entièrement automatisé. Les conteneurs Windows sont basés sur la plateforme de la station d’accueil, qui offre des mises à jour et des restaurations automatiques pour les déploiements de conteneurs. L’amélioration principale que vous pouvez effectuer à l’aide du moteur de l’ancrage est que vous créez des images, comme des instantanés de votre application, avec toutes ses dépendances. Les images sont des images d’ancrage (une image de conteneur Windows, dans le cas présent). Les images exécutent des applications ASP.NET dans des conteneurs, sans revenir au code source. L’instantané de conteneur devient l’unité de déploiement.

De nombreuses organisations déposent des applications monolithiques existantes pour les raisons suivantes :

- **Flexibilité des versions grâce à un déploiement amélioré**. Les conteneurs offrent un contrat de déploiement cohérent entre le développement et les opérations. Lorsque vous utilisez des conteneurs, vous n’entendez pas les développeurs dire « ça marche sur mon ordinateur, pourquoi ne pas en production ? » Par exemple, « il s’exécute en tant que conteneur, il s’exécutera donc en production ». L’application empaquetée, avec toutes ses dépendances, peut être exécutée dans n’importe quel environnement de conteneur pris en charge. Il s’exécutera comme prévu pour s’exécuter dans toutes les cibles de déploiement (dev, QA, staging, production). Les conteneurs éliminent la plupart des frottements lorsqu’ils passent d’une étape à l’autre, ce qui améliore considérablement le déploiement, et vous pouvez les expédier plus rapidement.

- **Réduction des coûts**. Les conteneurs entraînent des coûts réduits, que ce soit par la consolidation et la suppression du matériel existant ou par l’exécution d’applications à une densité plus élevée par unité de matériel.

- **Portabilité** : Les conteneurs sont modulaires et portables. Les conteneurs d’ancrage sont pris en charge sur n’importe quel système d’exploitation serveur (Linux et Windows), dans n’importe quel cloud public principal (Microsoft Azure, Amazon AWS, Google, IBM) et dans des environnements Cloud locaux et privés ou hybrides.

- **Contrôle**. Les conteneurs offrent un environnement flexible et sécurisé, contrôlé au niveau du conteneur. Un conteneur peut être sécurisé, isolé et même limité en définissant des stratégies de contrainte d’exécution sur le conteneur. Comme indiqué dans la section sur les conteneurs Windows, les conteneurs Windows Server 2016 et Hyper-V offrent des options de support technique d’entreprise supplémentaires.

Des améliorations significatives de l’agilité, de la portabilité et du contrôle conduisent à des réductions de coûts significatives lorsque vous utilisez des conteneurs pour développer et gérer des applications.

## <a name="what-is-docker"></a>Qu’est-ce que Docker ?

[Dockr](https://www.docker.com/) est un [projet open source](https://github.com/docker/docker) qui automatise le déploiement d’applications en tant que conteneurs portables et autonomes qui peuvent s’exécuter dans le Cloud ou localement. Docker est également le nom de la [société](https://www.docker.com/) qui développe et diffuse cette technologie. L’entreprise travaille en collaboration avec des fournisseurs Cloud, Linux et Windows, y compris Microsoft.

![Diagramme montrant comment l’arrimeur déploie les conteneurs dans le Cloud hybride.](./media/deploy-existing-net-apps-as-windows-containers/docker-deploys-containers-all-layers.png)

**Figure 4-6.** Docker déploie des conteneurs dans toutes les couches du cloud hybride

Pour une personne connaissant les machines virtuelles, les conteneurs peuvent paraître remarquablement similaires. Un conteneur exécute un système d’exploitation, a un système de fichiers et est accessible sur un réseau, tout comme un système informatique physique ou virtuel. Ceci dit, la technologie et les concepts derrière les conteneurs sont très différents de ceux des machines virtuelles. Du point de vue du développeur, un conteneur doit être traité plus comme un processus unique. En fait, un conteneur a un seul point d’entrée pour un processus.

Les conteneurs d’ancrage (par souci de simplicité, *conteneurs*) peuvent s’exécuter en mode natif sur Linux et Windows. Lors de l’exécution de conteneurs standard, les conteneurs Windows ne peuvent s’exécuter que sur des hôtes Windows (un serveur hôte ou une machine virtuelle), et les conteneurs Linux ne peuvent s’exécuter que sur des hôtes Linux. Toutefois, dans les versions récentes de Windows Server et des conteneurs Hyper-V, un conteneur Linux peut également s’exécuter en mode natif sur Windows Server en utilisant la technologie d’isolation Hyper-V qui est actuellement disponible uniquement dans les conteneurs Windows Server.

Dans un avenir proche, les environnements mixtes qui ont des conteneurs Linux et Windows seront possibles et même communs.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Avantages des conteneurs Windows pour vos applications .NET existantes

Les avantages de l’utilisation des conteneurs Windows sont fondamentalement les mêmes avantages que ceux que vous pouvez obtenir des conteneurs en général. L’utilisation de conteneurs Windows est une amélioration considérable de l’agilité, de la portabilité et du contrôle.

Les applications .NET existantes font référence aux applications qui ont été créées à l’aide de l' .NET Framework. Par exemple, il peut s’agir d’applications Web ASP.NET traditionnelles : elles n’utilisent pas .NET Core ou .NET 5,0, qui est plus récent et exécute des plateformes multiplateforme sur Linux, Windows et MacOS.

La dépendance principale dans le .NET Framework est Windows. Il a également des dépendances secondaires, comme IIS et System. Web dans des ASP.NET traditionnels.

Une application .NET Framework doit s’exécuter sur Windows, point. Si vous souhaitez créer un conteneur pour les applications de .NET Framework existantes et que vous ne souhaitez pas investir dans une migration vers .NET Core ou version ultérieure (« si elle fonctionne correctement, ne la migrez pas »), le seul choix que vous avez pour les conteneurs est d’utiliser des conteneurs Windows.

L’un des principaux avantages des conteneurs Windows est qu’ils vous offrent un moyen de moderniser vos applications .NET Framework existantes qui s’exécutent sur le conteneur Windows. Enfin, les conteneurs Windows vous présentent les avantages que vous recherchez à l’aide de conteneurs-agilité, portabilité et meilleur contrôle.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Choisissez un système d’exploitation avec lequel cibler. Conteneurs basés sur le réseau

Compte tenu de la diversité des systèmes d’exploitation pris en charge par l’arrimeur, ainsi que des différences entre .NET Framework et .NET Core, vous devez cibler un système d’exploitation spécifique et des versions spécifiques en fonction de l’infrastructure que vous utilisez.

Pour Windows, vous pouvez utiliser Windows Server Core ou Windows Nano Server. Ces versions de Windows fournissent différentes caractéristiques (comme IIS ou un serveur Web auto-hébergé comme Kestrel) qui peuvent être nécessaires à .NET Framework ou à des applications .NET.

Pour Linux, plusieurs distributions sont disponibles et prises en charge dans les images .NET Docker officielles (comme Debian).

La figure 4-7 montre les versions de système d’exploitation que vous pouvez cibler, en fonction de la version de l’application du .NET Framework.

![Diagramme montrant le système d’exploitation à cibler en fonction de la version de .NET Framework.](./media/deploy-existing-net-apps-as-windows-containers/dotnet-framework-operating-systems.png)

**Figure 4-7.** Systèmes d’exploitation à cibler en fonction de la version de .NET Framework

Dans les scénarios de migration des applications existantes ou héritées basées sur des applications .NET Framework, les dépendances principales sont sur Windows et IIS. La seule option consiste à utiliser des images de l’arrimeur basées sur Windows Server Core et le .NET Framework.

Lorsque vous ajoutez le nom de l’image à votre fichier fichier dockerfile, vous pouvez sélectionner le système d’exploitation et la version à l’aide d’une balise, comme dans les exemples suivants pour les images de conteneur Windows basées sur .NET Framework :

> | **Tag** | **Système et version** |
> |---|---|
> | **mcr.microsoft.com/dotnet/framework/runtime:4.x-windowsservercore-20H2** | .NET Framework 4. x sur Windows Server Core |
> | **mcr.microsoft.com/dotnet/framework/aspnet:4.x-windowsservercore-20H2** | .NET Framework 4. x avec personnalisation supplémentaire des ASP.NET, sur Windows Server Core |

Pour .NET (multiplateforme pour Linux et Windows), les balises se présentent comme suit :

> | **Tag** | **Système et version**
> |---|---|
> | **mcr.microsoft.com/dotnet/runtime:5.0** | .NET Runtime uniquement sur Linux |
> | **mcr.microsoft.com/dotnet/runtime:5.0-nanoserver-20H2** | Runtime .NET uniquement sur Windows nano Server |

### <a name="multi-arch-images"></a>Images multi-arch

À partir de la mi-2017, vous pouvez également utiliser une nouvelle fonctionnalité de l’Ancreur appelée images [multiarch](https://github.com/moby/moby/issues/15866) . Les images de la station d’accueil .NET peuvent utiliser des balises multi-arch. Vos fichiers fichier dockerfile n’ont plus besoin de définir le système d’exploitation que vous ciblez. La fonctionnalité multi-arch permet l’utilisation d’une balise unique sur plusieurs configurations d’ordinateur. Par exemple, avec plusieurs archets, vous pouvez utiliser une balise commune : **MCR.Microsoft.com/dotnet/Runtime :5.0**. Si vous extrayez cette balise d’un environnement de conteneur Linux, vous bénéficiez de l’image Debian. Si vous extrayez cette balise d’un environnement de conteneur Windows, vous récupérez l’image nano Server.

Pour les images .NET Framework, étant donné que le .NET Framework traditionnel ne prend en charge que Windows, vous ne pouvez pas utiliser la fonctionnalité multi-arch.

## <a name="windows-container-types"></a>Types de conteneurs Windows

Comme les conteneurs Linux, les conteneurs Windows Server sont gérés à l’aide du moteur de l’ancrage. À la différence des conteneurs Linux, les conteneurs Windows incluent deux types de conteneurs différents, ou des durées d’exécution : les conteneurs Windows Server et l’isolation Hyper-V.

**Conteneurs Windows Server**: permet d’isoler les applications grâce à la technologie d’isolation des processus et des espaces de noms. Un conteneur Windows Server partage un noyau avec l’hôte de conteneur et tous les conteneurs en cours d’exécution sur l’ordinateur hôte. Ces conteneurs ne créent pas de frontière de sécurité contre le code hostile et ne doivent pas être utilisés pour isoler du code non fiable. En raison de l’espace de noyau partagé, ces conteneurs requièrent la même version et configuration de noyau.

**Isolation Hyper-V**: développe l’isolation fournie par les conteneurs Windows Server en exécutant chaque conteneur sur une machine virtuelle hautement optimisée. Dans cette configuration, le noyau de l’hôte de conteneur n’est pas partagé avec d’autres conteneurs exécutés sur l’hôte. Ces conteneurs sont conçus pour l’hébergement multi-locataire hostile, avec les mêmes garanties de sécurité qu’une machine virtuelle. Étant donné que ces conteneurs ne partagent pas le noyau avec l’hôte ou d’autres conteneurs sur l’hôte, ils peuvent exécuter des noyaux avec différentes versions et configurations (avec les versions prises en charge). Par exemple, tous les conteneurs Windows sur Windows 10 utilisent l’isolation Hyper-V pour utiliser la version et la configuration du noyau de Windows Server.

L’exécution d’un conteneur sur Windows avec ou sans l’isolation Hyper-V est une décision au moment de l’exécution. Vous pouvez choisir de créer le conteneur avec l’isolation Hyper-V initialement et, au moment de l’exécution, choisir de l’exécuter en tant que conteneur Windows Server à la place.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Documentation sur les conteneurs Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Notions de base des conteneurs Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **Infographie : Microsoft et conteneurs**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>L’écosystème de conteneurs dans Azure

Dans les sections précédentes, nous avons expliqué les avantages des conteneurs de l’ancrage, ainsi que les détails sur les images de conteneur spécifiques pour les applications .NET. Toutes ces informations génériques sont fondamentales pour développer ou déconteneurr une application.
Toutefois, quand vous réfléchissez à l’environnement de déploiement de production ou même aux environnements AQ et de développement/test, Microsoft Azure offre une vaste gamme de choix, un écosystème de conteneurs complet dans le Cloud (illustré dans le diagramme ci-dessous). En fonction des besoins spécifiques de votre application, vous devez choisir un ou un autre produit Azure.

![Diagramme de l’écosystème de conteneurs dans Azure.](./media/deploy-existing-net-apps-as-windows-containers/azure-container-ecosystem.png)

**Figure 4-7.5.** L’écosystème de conteneurs dans Azure

À partir de l’écosystème de conteneurs dans Azure, les produits suivants prennent en charge les conteneurs qui sont considérés comme des infrastructures :

- **Azure Container Instances (ACI)**
- **Machines virtuelles Azure** (avec prise en charge du conteneur)
- **Azure Virtual Machine Scale sets** (avec prise en charge du conteneur)

À partir de ces trois, ACI offre un excellent avantage, ce qui est que vous n’avez pas besoin de gérer le système d’exploitation sous-jacent, vous n’avez pas besoin de mettre à niveau/correctif, etc. mais ACI est toujours positionné au niveau de l’infrastructure, comme expliqué dans les prochaines sections de ce document.

Les produits dans Azure prenant en charge les conteneurs qui sont en même temps positionnés plus dans le niveau PaaS (Platform as a service) sont les suivants :

- **Azure App Service**
- **Service Azure Kubernetes (AKS et ACS)**
- **Azure Batch**

Azure Container Registry est ensuite un registre de conteneurs hautement évolutif, hébergé dans Azure, que vous pouvez utiliser à partir de tous les produits précédents lors de l’inscription et du déploiement de vos images de conteneur personnalisées.

En outre, à partir de vos conteneurs, vous pouvez utiliser d’autres services gérés dans Azure comme Azure SQL Database, le cache Redims Azure, les Azure Cosmos DB, etc. de plus, il existe des solutions/plateformes tierces disponibles dans la place de marché Azure, comme Cloud Foundry et OpenShift, où vous pouvez également utiliser des conteneurs dans Azure.

Dans les sections suivantes, vous pouvez explorer les recommandations de Microsoft concernant l’utilisation de chacun de ces produits et solutions Azure, spécifiquement lors du ciblage de conteneurs Windows.

>[!div class="step-by-step"]
>[Précédent](what-about-cloud-native-applications.md) 
> [Suivant](when-not-to-deploy-to-windows-containers.md)
