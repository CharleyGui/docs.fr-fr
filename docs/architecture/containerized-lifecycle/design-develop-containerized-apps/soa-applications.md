---
title: Applications SOA
description: N’oubliez pas que les conteneurs peuvent également s’avérer une option de déploiement utile pour les applications SOA.
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68672356"
---
# <a name="service-oriented-applications"></a>Applications orientées services

SOA, ou architecture orientée services, est un terme qui a été trop utilisé et qui a désigné de nombreuses choses différentes pour différentes personnes. Un dénominateur commun est néanmoins que SOA signifie que vous structurez l’architecture de votre application en la décomposant en plusieurs services (la plupart du temps en services HTTP) qui peuvent être classés dans différents types, comme des sous-systèmes ou, dans d’autres cas, des niveaux.

Aujourd’hui, vous pouvez déployer ces services en tant que conteneurs Docker, ce qui résout les problèmes de déploiement, car toutes les dépendances sont incluses dans l’image conteneur. Toutefois, lorsque vous avez besoin d’effectuer un scale-out de SOA, vous pouvez rencontrer des difficultés si vous effectuez un déploiement basé sur des instances uniques. Ces difficultés peuvent être gérées à l’aide de logiciels de clustering Docker ou d’un orchestrateur. Nous allons examiner les orchestrateurs de plus près dans la section suivante, quand nous nous intéresserons aux approches des microservices.

Les conteneurs Docker sont pratiques (mais pas obligatoires) pour les architectures orientées services traditionnelles et pour les architectures de microservices plus avancées.

En fin de compte, les solutions de clustering de conteneur s’avèrent utiles à la fois pour une architecture SOA traditionnelle et une architecture de microservices plus avancée dans laquelle chaque microservice a son modèle de données. Et avec plusieurs bases de données, vous pouvez également effectuer un scale-out de la couche Données au lieu d’utiliser des bases de données monolithiques partagées par les services SOA. Toutefois, le débat quant au fractionnement des données porte purement sur l’architecture et la conception.

>[!div class="step-by-step"]
>[Suivant précédent](state-and-data-in-docker-applications.md)
>[Next](orchestrate-high-scalability-availability.md)
