---
title: Introduction aux conteneurs et à Docker
description: Obtenez une vue d’ensemble des principaux avantages de l’utilisation de Docker.
ms.date: 04/15/2020
ms.openlocfilehash: 79b4752ef4d2f0aa6199414aea5cf4ef357c86d3
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915948"
---
# <a name="introduction-to-containers-and-docker"></a>Présentation des conteneurs et de Docker

*La mise en conteneur est une approche du développement logiciel dans laquelle une application ou un service, ses dépendances et sa configuration (abstraite comme fichiers manifeste de déploiement) sont regroupés sous la forme d’une image conteneur. Vous pouvez ensuite tester l’application en conteneur en tant qu’unité et la déployer en tant qu’instance d’image de conteneur dans le système d’exploitation hôte.*

De la même manière que les conteneurs de transport permettent de transporter des marchandises par bateau, par train ou par camion indépendamment de la nature de la cargaison, les conteneurs logiciels agissent comme une unité de déploiement logiciel standard qui peut contenir du code et des dépendances différents. Cette façon de mettre les logiciels en conteneur permet aux développeurs et aux informaticiens de les déployer dans les environnements avec peu ou pas de modifications.

Par ailleurs, les conteneurs isolent les applications les unes des autres sur un SE partagé. Les applications en conteneur s’exécutent sur un hôte de conteneurs qui à son tour s’exécute sur le SE (Linux ou Windows). Par conséquent, les conteneurs ont un encombrement bien moindre que les images de machine virtuelle.

Chaque conteneur peut exécuter une application web ou un service dans son intégralité, comme l’illustre la figure 1-1. Dans cet exemple, l’hôte Docker est un hôte de conteneurs, et App1, App2, Svc1 et Svc2 sont des applications ou des services en conteneur.

![Diagramme montrant quatre conteneurs exécutés sur une machine virtuelle ou un serveur.](./media/introduction-to-containers-and-docker/multiple-containers-single-host.png)

**Figure 1-1**. plusieurs conteneurs s’exécutant sur un hôte de conteneurs

L’autre avantage qui dérive de la mise en conteneur est la scalabilité. Vous pouvez rapidement monter en charge en créant des conteneurs pour des tâches à court terme. Du point de vue de l’application, instancier une image (c.-à-d., créer un conteneur) revient à instancier un processus comme un service ou une application web. Cependant, dans un souci de fiabilité, quand il s’agit d’exécuter plusieurs instances d’une même image sur plusieurs serveurs hôtes, il est en principe préférable que chaque conteneur (instance d’image) s’exécute sur un serveur hôte différent ou sur une machine virtuelle dans différents domaines d’erreur.

Pour résumer, les conteneurs offrent les avantages de l’isolation, de la portabilité, de l’agilité, de l’extensibilité et du contrôle dans l’ensemble du flux de travail du cycle de vie de l’application. L’avantage le plus important est l’isolation de l’environnement fourni entre le développement et les opérations.

>[!div class="step-by-step"]
>[Précédent](index.md) 
> [Suivant](what-is-docker.md)
