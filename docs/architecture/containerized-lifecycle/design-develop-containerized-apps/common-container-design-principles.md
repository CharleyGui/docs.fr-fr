---
title: Principes de conception communs des conteneurs
description: Découvrez un principe fondamental d’une bonne conception de conteneurs, à savoir qu’un conteneur doit héberger un seul processus.
ms.date: 08/06/2020
ms.openlocfilehash: 7dcf4b4af3385a2a500c5bc16a889b56fa2c25d5
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915998"
---
# <a name="common-container-design-principles"></a>Principes de conception communs des conteneurs

Avant d’aborder le processus de développement, il est bon de mentionner quelques concepts de base liés à la façon dont vous utilisez les conteneurs.

## <a name="container-equals-a-process"></a>Un conteneur est égal à un processus

Dans le modèle à base de conteneurs, un conteneur représente un processus unique. En définissant un conteneur comme limite de processus, vous commencez à créer les primitives utilisées pour la mise à l’échelle des processus. Quand vous exécutez un conteneur Docker, vous voyez une définition [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#entrypoint). Celle-ci définit le processus et la durée de vie du conteneur. Une fois le processus terminé, le cycle de vie du conteneur prend fin. Il existe des processus longs, tels que les serveurs web, et des processus de courte durée, tels que des traitements par lots, qui peuvent avoir été implémentés en tant que [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/) Microsoft Azure. Si le processus échoue, le conteneur prend fin et l’orchestrateur prend le contrôle. Si l’orchestrateur a été configuré pour maintenir cinq instances en exécution et qu’une défaillance touche l’une d’elles, l’orchestrateur crée un autre conteneur pour remplacer le processus défaillant. Dans un programme de traitement par lots, le processus démarre avec des paramètres. Quand le processus prend fin, le travail est terminé.

Le cas peut se présenter où vous voulez que plusieurs processus s’exécutent dans un même conteneur. Dans tout document d’architecture, il n’est jamais question de « jamais » et il n’y a pas toujours un « toujours ». Pour les scénarios qui nécessitent plusieurs processus, un modèle courant consiste à utiliser un [superviseur](http://supervisord.org/).

>[!div class="step-by-step"]
>[Précédent](design-docker-applications.md) 
> [Suivant](monolithic-applications.md)
