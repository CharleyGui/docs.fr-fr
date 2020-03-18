---
title: Images officielles .NET Docker
description: Architecture de microservices .NET pour les applications .NET en conteneur | Images officielles .NET Docker
ms.date: 01/30/2020
ms.openlocfilehash: 50a50587b35f811859841c4e049f40cb99479372
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501877"
---
# <a name="official-net-docker-images"></a>Images officielles .NET Docker

Les images officielles .NET Docker sont des images Docker créées et optimisées par Microsoft. Ils sont accessibles au public dans les référentiels Microsoft sur [Docker Hub](https://hub.docker.com/u/microsoft/). Chaque dépôt peut contenir plusieurs images, en fonction des versions de .NET, du système d’exploitation et de ses versions (Linux Debian, Linux Alpine, Windows Nano Server, Windows Server Core, etc.).

Depuis .NET Core 2.1, toutes les images .NET Core, y compris pour ASP.NET Core sont disponibles au Docker Hub au référentiel d’images .NET Core: <https://hub.docker.com/_/microsoft-dotnet-core/>.

Depuis mai 2018, les images Microsoft sont [syndiquées dans le Microsoft Container Registry](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/). Le catalogue officiel n’est toujours disponible que dans Docker Hub, et là vous trouverez l’adresse mise à jour pour tirer l’image.

La plupart des dépôts d’images fournissent un marquage complet pour vous aider à sélectionner non seulement une version cadre spécifique, mais aussi à choisir un système d’exploitation (distribution Linux ou version Windows).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>Optimisations d’images .NET Core et Docker pour le développement et la production

Au moment de créer des images Docker pour développeurs, Microsoft s’est concentré sur les principaux scénarios suivants :

- Images utilisées pour *développer* et générer des applications .NET Core

- Images utilisées pour *exécuter* des applications .NET Core

Pourquoi plusieurs images ? En règle générale, vos propriétés varient selon que vous développez, générez ou exécutez des applications en conteneur. En proposant des images différentes en fonction des tâches, Microsoft permet d’optimiser ces processus distincts que sont le développement, la génération et le déploiement d’applications.

### <a name="during-development-and-build"></a>En phase de développement et de génération

En phase de développement, il importe d’itérer rapidement les modifications et de pouvoir les déboguer. La taille de l’image n’est pas aussi importante que la possibilité d’apporter des modifications à votre code et de voir les modifications rapidement. Certains outils et des « conteneurs à agent de construction », utilisent l’image de développement .NET Core (*mcr.microsoft.com/dotnet/core/sdk:3.1*) pendant le processus de développement et de construction. Lors de la construction à l’intérieur d’un conteneur Docker, les aspects importants sont les éléments qui sont nécessaires pour compiler votre application. Il s’agit notamment du compilateur et des autres dépendances .NET.

Pourquoi ce type d’image de build est-il important ? Vous ne déployez pas cette image en production. Au lieu de cela, c’est une image que vous utilisez pour construire le contenu que vous placez dans une image de production. Cette image serait utilisée dans votre environnement d’intégration continue (CI) ou dans votre environnement de construction lors de l’utilisation de builds en plusieurs étapes Docker.

### <a name="in-production"></a>En production

Ce qui importe en production, c’est la vitesse à laquelle vous pouvez déployer et démarrer vos conteneurs basées sur une image .NET Core de production. Par conséquent, l’image runtime-only basée sur *mcr.microsoft.com/dotnet/core/aspnet:3.1* est petite de sorte qu’il peut voyager rapidement à travers le réseau de votre registre Docker à vos hôtes Docker. Le contenu est prêt à s’exécuter, ce qui permet d’écourter au maximum la durée entre le démarrage du conteneur et le traitement des résultats. Dans le modèle Docker, il n’est pas nécessaire de compiler à partir de code C\# comme c’est le cas lorsque vous exécutez la commande dotnet build ou dotnet publish en utilisant le conteneur de build.

Dans cette image optimisée, vous ne mettez que les binaires et autres contenus nécessaires à l’exécution de l’application. Par exemple, le `dotnet publish` contenu créé par ne contient que les binaires .NET compilés, les images, .js, et .css fichiers. Au fil du temps, vous verrez des images qui contiennent des packages prétraités avec JIT (la compilation du langage intermédiaire en code natif qui se produit lors de l’exécution).

Bien qu’il existe plusieurs versions des images .NET Core et ASP.NET Core, elles partagent toutes une ou plusieurs couches, dont la couche de base. Par conséquent, la quantité d’espace disque nécessaire au stockage d’une image est faible ; elle est uniquement constituée de la différence entre votre image personnalisée et son image de base. De ce fait, l’extraction de l’image de votre registre est très rapide.

En explorant les dépôts d’images .NET dans Docker Hub, vous trouverez plusieurs versions d’images classées ou marquées avec des balises. Ces balises permettent d’identifier la version dont vous avez besoin, comme celles présentées dans le tableau suivant :

| Image | Commentaires |
|-------|----------|
| mcr.microsoft.com/dotnet/core/aspnet:**3.1** | ASP.NET Core, avec le runtime uniquement et les optimisations ASP.NET Core, Linux et Windows (multi-arch) |
| mcr.microsoft.com/dotnet/core/sdk:**3.1** | .NET Core, avec les SDK inclus, sur Linux et Windows (multi-arch) |

> [!div class="step-by-step"]
> [Suivant précédent](net-container-os-targets.md)
> [Next](../architect-microservice-container-applications/index.md)
