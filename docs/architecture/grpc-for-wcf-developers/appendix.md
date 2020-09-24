---
title: Annexe-gRPC pour les développeurs WCF
description: Présentation des transactions distribuées et de leur implémentation dans les architectures de microservices modernes.
ms.date: 09/02/2019
ms.openlocfilehash: f60899463a13e9f740f6ae63150d18eab3069124
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165856"
---
# <a name="appendix-a---transactions"></a>Annexe A-transactions

Windows Communication Foundation (WCF) prend en charge les transactions distribuées, ce qui vous permet d’effectuer des opérations atomiques sur plusieurs services. Cette fonctionnalité est basée sur le [Distributed Transaction Coordinator Microsoft](/previous-versions/windows/desktop/ms684146(v=vs.85)).

Dans le paysage des microservices plus récents, ce type de traitement automatisé des transactions distribuées n’est pas possible. Le nombre de technologies impliquées est trop important, notamment les bases de données relationnelles, les magasins de données NoSQL et les systèmes de messagerie. Il peut également y avoir une combinaison de systèmes d’exploitation, de langages de programmation et d’infrastructures en cours d’utilisation dans un environnement unique.

La transaction distribuée WCF est une implémentation de ce qu’on appelle une [validation en deux phases (2PC)](https://en.wikipedia.org/wiki/Two-phase_commit_protocol). Vous pouvez implémenter des transactions 2PC manuellement en coordonnant les messages entre les services, en créant des transactions ouvertes au sein de chaque service et en envoyant des messages de validation ou de restauration, en fonction de la réussite ou de l’échec. Toutefois, la complexité impliquée dans la gestion de 2PC peut augmenter de façon exponentielle à mesure que les systèmes évoluent. Les transactions ouvertes contiennent des verrous de base de données qui peuvent avoir un impact négatif sur les performances, ou pire, provoquer des interblocages entre les services.

Si possible, il est préférable d’éviter totalement les transactions distribuées. Si deux éléments de données sont liés comme pour exiger des mises à jour atomiques, envisagez de les gérer à la fois avec le même service. Appliquez ces modifications atomiques à l’aide d’une requête ou d’un message unique à ce service.

Si ce n’est pas possible, une alternative consiste à utiliser le [modèle saga](https://microservices.io/patterns/data/saga.html). Dans un saga, les mises à jour sont traitées de manière séquentielle. à mesure que chaque mise à jour est réussie, le suivant est déclenché. Ces déclencheurs peuvent être propagés du service au service, ou gérés par un coordinateur saga ou Orchestrator. Si une mise à jour échoue à tout moment pendant le processus, les services qui ont déjà effectué leurs mises à jour appliquent une logique spécifique pour les inverser.

Une autre option consiste à utiliser la conception pilotée par domaine (DDD) et la séparation des responsabilités de commande/requête (CQRS), comme décrit dans le [livre électronique sur les microservices .net](../microservices/microservice-ddd-cqrs-patterns/index.md). En particulier, l’utilisation d’événements de domaine ou d’une [source d’événements](https://martinfowler.com/eaaDev/EventSourcing.html) peut aider à garantir que les mises à jour sont cohérentes, si elles ne sont pas appliquées immédiatement.

>[!div class="step-by-step"]
>[Précédent](application-performance-management.md)
