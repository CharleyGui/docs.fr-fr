---
title: Images officielles .NET Docker
description: Architecture de microservices .NET pour les applications .NET en conteneur | Images officielles .NET Docker
ms.date: 01/13/2021
ms.openlocfilehash: 072e565260bf81c123ee837ccca46fbdf7c67361
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065120"
---
# <a name="official-net-docker-images"></a>Images officielles .NET Docker

Les images officielles .NET Docker sont des images Docker créées et optimisées par Microsoft. Ils sont disponibles publiquement dans les référentiels Microsoft sur le hub de l' [arrimeur](https://hub.docker.com/u/microsoft/). Chaque dépôt peut contenir plusieurs images, en fonction des versions de .NET, du système d’exploitation et de ses versions (Linux Debian, Linux Alpine, Windows Nano Server, Windows Server Core, etc.).

Depuis .NET Core 2,1, toutes les images .NET Core ou versions ultérieures, y compris pour ASP.NET Core, sont disponibles dans le hub de l’Ancreur dans le référentiel d’images .NET : <https://hub.docker.com/_/microsoft-dotnet/> .

Depuis le 2018 mai, les images Microsoft sont [syndiquées dans le container Registry Microsoft](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/). Le catalogue officiel est toujours disponible uniquement dans le hub de l’arrimeur, et vous trouverez l’adresse mise à jour pour extraire l’image.

La plupart des référentiels d’images fournissent un balisage complet pour vous aider à sélectionner non seulement une version de Framework spécifique, mais également à choisir un système d’exploitation (distribution Linux ou version de Windows).

## <a name="net-and-docker-image-optimizations-for-development-versus-production"></a>Optimisations des images .NET et de l’arrimeur pour le développement et la production

Au moment de créer des images Docker pour développeurs, Microsoft s’est concentré sur les principaux scénarios suivants :

- Images utilisées pour *développer* et générer des applications .net.

- Images utilisées pour *exécuter* des applications .net.

Pourquoi plusieurs images ? En règle générale, vos propriétés varient selon que vous développez, générez ou exécutez des applications en conteneur. En proposant des images différentes en fonction des tâches, Microsoft permet d’optimiser ces processus distincts que sont le développement, la génération et le déploiement d’applications.

### <a name="during-development-and-build"></a>En phase de développement et de génération

En phase de développement, il importe d’itérer rapidement les modifications et de pouvoir les déboguer. La taille de l’image n’est pas aussi importante que la possibilité d’apporter des modifications à votre code et de voir rapidement les modifications. Certains outils et « conteneurs d’agent de build » utilisent l’image .NET de développement (*MCR.Microsoft.com/dotnet/SDK :5.0*) pendant le processus de développement et de génération. Lors de la génération à l’intérieur d’un conteneur d’ancrage, les aspects importants sont les éléments nécessaires à la compilation de votre application. Il s’agit notamment du compilateur et des autres dépendances .NET.

Pourquoi ce type d’image de build est-il important ? Vous ne déployez pas cette image en production. Au lieu de cela, il s’agit d’une image que vous utilisez pour créer le contenu que vous placez dans une image de production. Cette image est utilisée dans votre environnement d’intégration continue (CI) ou dans votre environnement de génération lors de l’utilisation de builds à plusieurs étages Dockr.

### <a name="in-production"></a>En production

Ce qui est important en production est la rapidité avec laquelle vous pouvez déployer et démarrer vos conteneurs basés sur une image .NET de production. Par conséquent, l’image d’exécution uniquement basée sur *MCR.Microsoft.com/dotnet/ASPNET :5.0* est petite afin de pouvoir circuler rapidement sur le réseau à partir de votre registre de station d’accueil vers vos hôtes d’ancrage. Le contenu est prêt à s’exécuter, ce qui permet d’écourter au maximum la durée entre le démarrage du conteneur et le traitement des résultats. Dans le modèle Docker, il n’est pas nécessaire de compiler à partir de code C\# comme c’est le cas lorsque vous exécutez la commande dotnet build ou dotnet publish en utilisant le conteneur de build.

Dans cette image optimisée, vous placez uniquement les fichiers binaires et tout autre contenu nécessaire à l’exécution de l’application. Par exemple, le contenu créé par `dotnet publish` contient uniquement les fichiers binaires .net, les images, les fichiers. js et. CSS compilés. Au fil du temps, vous verrez des images qui contiennent des packages prétraités avec JIT (la compilation du langage intermédiaire en code natif qui se produit lors de l’exécution).

Bien qu’il existe plusieurs versions des images .NET et ASP.NET Core, elles partagent toutes une ou plusieurs couches, y compris la couche de base. Par conséquent, la quantité d’espace disque nécessaire au stockage d’une image est faible ; elle est uniquement constituée de la différence entre votre image personnalisée et son image de base. De ce fait, l’extraction de l’image de votre registre est très rapide.

En explorant les dépôts d’images .NET dans Docker Hub, vous trouverez plusieurs versions d’images classées ou marquées avec des balises. Ces balises permettent d’identifier la version dont vous avez besoin, comme celles présentées dans le tableau suivant :

| Image | Commentaires |
|-------|----------|
| mcr.microsoft.com/dotnet/aspnet :**5,0** | ASP.NET Core, avec le runtime uniquement et les optimisations ASP.NET Core, Linux et Windows (multi-arch) |
| mcr.microsoft.com/dotnet/sdk :**5,0** | .NET 5, avec les kits de développement logiciel (SDK) inclus, sur Linux et Windows (multi-arch) |

> [!div class="step-by-step"]
> [Précédent](net-container-os-targets.md) 
>  [Suivant](../architect-microservice-container-applications/index.md)
