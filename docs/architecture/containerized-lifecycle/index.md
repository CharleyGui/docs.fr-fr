---
title: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
description: Bénéficiez d’une vue d’ensemble du processus de développement et de déploiement pour le développement et le déploiement d’applications en conteneur avec l’arrimeur et la plateforme et les outils Microsoft.
ms.date: 01/06/2021
ms.openlocfilehash: 94c277e349bacee9b9fc7b160043005dd4135958
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970113"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a>Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft

![Couverture de livre](./media/devops-book-cover-large-we.png)

**Édition v 5.0** -mise à jour vers ASP.net Core 5,0

Reportez-vous à [Journal des modifications](https://aka.ms/DockerLifecycleEbookChangelog) pour les mises à jour de livres et les contributions de la communauté.

Ce guide est une vue d’ensemble générale du développement et du déploiement d’applications ASP.NET Core en conteneur avec l’outil d’amarrage, à l’aide de la plateforme et des outils Microsoft. Ce guide comprend une présentation générale d’Azure DevOps, pour l’implémentation de pipelines CI/CD, ainsi que Azure Container Registry (ACR) et les services Azure Kubernetes AKS pour le déploiement.

Pour obtenir des informations de bas niveau sur le développement, vous pouvez consulter le guide [.net microservices : architecture pour les applications .net en conteneur](../microservices/index.md) et l’application de référence [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).

## <a name="send-us-your-feedback"></a>Envoyez-nous vos commentaires !

Nous avons rédigé ce guide pour vous aider à comprendre l’architecture des applications en conteneur et des microservices dans .NET. Le guide et l’application de référence associée étant voués à évoluer, nous faisons bon accueil à vos commentaires ! Si vous avez des commentaires sur la façon dont ce guide peut être amélioré, envoyez vos commentaires à l’adresse <https://aka.ms/ebookfeedback> .

## <a name="credits"></a>Crédits

Auteur :

> **Cesar de la Torre**, chef de produit, équipe produit .NET, Microsoft Corp.

Éditeur des acquisitions :

> **Janine Patrick**

Éditeur de développement :

> **Bob Olivier**, solutions Professional chez Microsoft
>
> [**Octal publication, Inc.**](http://www.octalpub.com/)

Production éditoriale :

> [Dianne Olivier](http://www.octalpub.com/)
>
> **Octal publication, Inc.**

Copyeditor:

> **Bob Olivier**, solutions Professional chez Microsoft

Participants et réviseurs :

> **Nish Anil**, responsable de programme senior, équipe .NET, Microsoft
>
> **Miguel Veloso**, ingénieur de développement logiciel chez des concepts simples
>
> **Sumit Ghosh**, consultant principal chez Neudesic

## <a name="copyright"></a>copyright

PUBLIÉ PAR

Division Développeurs Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright &copy; 2021 par Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

 Certains exemples sont fournis à titre indicatif uniquement et sont fictifs. Toute association ou lien est purement involontaire ou fortuit.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.

Mac et macOS sont des marques commerciales d’Apple Inc.

Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

>[!div class="step-by-step"]
>[Next](introduction-to-containers-and-docker.md)
