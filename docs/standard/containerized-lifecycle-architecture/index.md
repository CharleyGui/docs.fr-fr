---
title: Introduction aux conteneurs et à Docker
description: Obtenez une vue d’ensemble des principaux avantages de l’utilisation de Docker.
ms.date: 02/15/2019
ms.openlocfilehash: a03c67ed4fbc55c84e69fba5b7978863c8305e00
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644953"
---
# <a name="introduction-to-containers-and-docker"></a>Présentation des conteneurs et de Docker

*La mise en conteneur est une approche de développement de logiciels qui consiste à empaqueter une application ou un service, ses dépendances et sa configuration (extraits sous forme de fichiers manifeste de déploiement) sous forme d’image de conteneur. Vous pouvez ensuite tester l’application en conteneur en tant qu’unité et la déployer sous forme d’instance d’image de conteneur sur le système d’exploitation hôte.*

De la même manière que les conteneurs de transport permettent de transporter des marchandises par bateau, par train ou par camion indépendamment de la nature de la cargaison, les conteneurs logiciels agissent comme une unité de déploiement logiciel standard qui peut contenir du code et des dépendances différents. Cette façon de mettre les logiciels en conteneur permet aux développeurs et aux informaticiens de les déployer dans les environnements avec peu ou pas de modifications.

Par ailleurs, les conteneurs isolent les applications les unes des autres sur un SE partagé. Les applications en conteneur s’exécutent sur un hôte de conteneurs qui à son tour s’exécute sur le SE (Linux ou Windows). Par conséquent, les conteneurs ont un encombrement bien moindre que les images de machine virtuelle.

Chaque conteneur peut exécuter une application web ou un service dans son intégralité, comme l’illustre la figure 1-1. Dans cet exemple, l’hôte Docker est un hôte de conteneurs, et App1, App2, Svc1 et Svc2 sont des applications ou des services en conteneur.

![Deux applications et deux services s’exécutant sur le système d’exploitation dans une machine virtuelle ou un serveur physique](./media/image1.png)

**Figure 1-1**. plusieurs conteneurs s’exécutant sur un hôte de conteneurs

L’autre avantage qui dérive de la mise en conteneur est la scalabilité. Vous pouvez rapidement monter en charge en créant des conteneurs pour des tâches à court terme. Du point de vue de l’application, instancier une image (c.-à-d., créer un conteneur) revient à instancier un processus comme un service ou une application web. Cependant, dans un souci de fiabilité, quand il s’agit d’exécuter plusieurs instances d’une même image sur plusieurs serveurs hôtes, il est en principe préférable que chaque conteneur (instance d’image) s’exécute sur un serveur hôte différent ou sur une machine virtuelle dans différents domaines d’erreur.

Pour résumer, les conteneurs offrent les avantages de l’isolation, de la portabilité, de l’agilité, de l’extensibilité et du contrôle dans l’ensemble du flux de travail du cycle de vie de l’application. L’avantage le plus important est l’isolation de l’environnement fourni entre le développement et les opérations.

>[!div class="step-by-step"]
>[Next](what-is-docker.md)
