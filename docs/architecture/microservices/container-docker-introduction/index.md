---
title: Introduction aux conteneurs et à Docker
description: Architecture des microservices .NET pour les applications .NET en conteneur | Introduction aux conteneurs et à Docker
ms.date: 01/13/2021
ms.openlocfilehash: 5e114ae893176954cae6eb4425459527b248c0ad
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189328"
---
# <a name="introduction-to-containers-and-docker"></a>Introduction aux conteneurs et à Docker

La mise en conteneur est une approche de développement de logiciels qui consiste à empaqueter une application ou un service, ses dépendances et sa configuration (extraits sous forme de fichiers manifeste de déploiement) sous forme d’image de conteneur. L’application en conteneur peut être testée en tant qu’unité et déployée sous forme d’instance d’image de conteneur sur le système d’exploitation (SE) hôte.

De la même manière que les conteneurs de transport permettent de transporter des marchandises par bateau, par train ou par camion indépendamment de la nature de la cargaison, les conteneurs logiciels agissent comme une unité de déploiement logiciel standard qui peut contenir du code et des dépendances différents. Cette façon de mettre les logiciels en conteneur permet aux développeurs et aux informaticiens de les déployer dans les environnements avec peu ou pas de modifications.

Par ailleurs, les conteneurs isolent les applications les unes des autres sur un SE partagé. Les applications en conteneur s’exécutent sur un hôte de conteneurs qui à son tour s’exécute sur le SE (Linux ou Windows). Par conséquent, les conteneurs ont un encombrement bien moindre que les images de machine virtuelle.

Chaque conteneur peut exécuter une application web ou un service dans son intégralité, comme l’illustre la figure 2-1. Dans cet exemple, l’hôte Docker est un hôte de conteneurs, et App1, App2, Svc 1 et Svc 2 sont des applications ou des services en conteneur.

![Diagramme montrant quatre conteneurs exécutés sur une machine virtuelle ou un serveur.](./media/index/multiple-containers-single-host.png)

**Figure 2-1**. plusieurs conteneurs s’exécutant sur un hôte de conteneurs

L’autre avantage de la mise en conteneur est l’extensibilité. Vous pouvez rapidement monter en charge en créant des conteneurs pour des tâches à court terme. Du point de vue de l’application, l’instanciation d’une image (création d’un conteneur) revient à instancier un processus comme un service ou une application Web. Cependant, dans un souci de fiabilité, quand il s’agit d’exécuter plusieurs instances d’une même image sur plusieurs serveurs hôtes, il est en principe préférable que chaque conteneur (instance d’image) s’exécute sur un serveur hôte différent ou sur une machine virtuelle dans différents domaines d’erreur.

Pour résumer, les conteneurs offrent les avantages de l’isolation, de la portabilité, de l’agilité, de l’extensibilité et du contrôle dans l’ensemble du flux de travail du cycle de vie de l’application. L’avantage le plus important est l’isolation de l’environnement fourni entre le développement et les opérations.

>[!div class="step-by-step"]
>[Précédent](../index.md) 
> [Suivant](docker-defined.md)
