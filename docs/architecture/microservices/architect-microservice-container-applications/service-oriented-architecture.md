---
title: Architecture orientée services
description: Découvrez les différences fondamentales entre les microservices et une SOA (architecture orientée services).
ms.date: 09/20/2018
ms.openlocfilehash: 84786539fbac0e8b38a81a2580232474774cd355
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68674926"
---
# <a name="service-oriented-architecture"></a>Architecture orientée services

SOA, ou Architecture orientée services, est un terme qui a été trop utilisé et qui a signifié des choses différentes pour différentes personnes. Un dénominateur commun est néanmoins que SOA signifie que vous structurez votre application en la décomposant en plusieurs services (la plupart du temps en services HTTP) qui peuvent être classés selon différents types, comme des sous-systèmes ou des niveaux.

Ces services peuvent désormais être déployés en tant que conteneurs Docker, ce qui résout les problèmes de déploiement, car toutes les dépendances sont incluses dans l’image du conteneur. Toutefois, quand vous devez effectuer un scale-up d’applications SOA, vous pouvez rencontrer des problèmes de scalabilité et de disponibilité si vous effectuez le déploiement sur des hôtes Docker uniques. C’est là que les logiciels de clustering Docker ou un orchestrateur peuvent vous aider, comme le montrent les prochaines sections, où sont décrites les approches de déploiement des microservices.

Les conteneurs Docker sont pratiques (mais pas obligatoires) pour les architectures orientées services traditionnelles et pour les architectures de microservices plus avancées.

Les microservices dérivent de SOA, mais SOA est différent de l’architecture de microservices. Des fonctionnalités telles que les grands répartiteurs centralisés, les orchestrateurs centralisés au niveau de l’organisation et [ESB (Enterprise Service Bus)](https://en.wikipedia.org/wiki/Enterprise_service_bus) sont classiques dans SOA. Dans la plupart des cas cependant, celles-ci sont des antimodèles dans la communauté des microservices. En fait, certaines personnes affirment que « l’architecture des microservices est une architecture SOA bien conçue ».

Ce guide se concentre sur les microservices, car une approche SOA est moins stricte que la configuration requise et les techniques utilisées dans une architecture de microservices. Si vous savez créer une application basée sur des microservices, vous savez également créer une application orientée services plus simple.

>[!div class="step-by-step"]
>[Suivant précédent](docker-application-state-data.md)
>[Next](microservices-architecture.md)
