---
title: Annexe-gRPC pour les développeurs WCF
description: Présentation des transactions distribuées et de leur implémentation dans les architectures de microservices modernes.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: d181eb07dd50ed338d02edb1908626e6ca3fb56c
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846731"
---
# <a name="appendix-a---transactions"></a>Annexe A-transactions

Les transactions distribuées prises en charge par Windows Communication Foundation (WCF) permettent d’effectuer des opérations atomiques sur plusieurs services. Cette fonctionnalité était basée sur le [Distributed Transaction Coordinator Microsoft](https://docs.microsoft.com/previous-versions/windows/desktop/ms684146(v=vs.85)).

Dans le paysage des microservices moderne, ce type de traitement automatisé des transactions distribuées n’est pas possible. Il existe un trop grand nombre de technologies différentes, notamment les bases de données relationnelles, les magasins de données NoSQL et les systèmes de messagerie, sans oublier la combinaison de systèmes d’exploitation, de langages de programmation et d’infrastructures qui peuvent être utilisés dans un environnement unique.

La transaction distribuée WCF est une implémentation de ce qu’on appelle une [validation en deux phases (2PC)](https://en.wikipedia.org/wiki/Two-phase_commit_protocol). Il est possible d’implémenter des transactions 2PC manuellement en coordonnant les messages entre les services, en créant des transactions ouvertes au sein de chaque service et en envoyant des messages « Commit » ou « Rollback » en fonction de la réussite ou de l’échec. Toutefois, la complexité impliquée dans la gestion de 2PC peut augmenter de façon exponentielle à mesure que les systèmes évoluent, et les transactions ouvertes contiennent des verrous de base de données qui peuvent avoir un impact négatif sur les performances ou, pire, provoquent des blocages interservices.

Si possible, il est préférable d’éviter totalement les transactions distribuées. Si deux éléments de données sont liés comme pour exiger des mises à jour atomiques, envisagez de les gérer à la fois avec le même service et en appliquant ces modifications atomiques à l’aide d’une requête ou d’un message unique à ce service.

Si ce n’est pas possible, une alternative consiste à utiliser le [modèle saga](https://microservices.io/patterns/data/saga.html). Dans un saga, les mises à jour sont traitées de manière séquentielle. à mesure que chaque mise à jour est réussie, le suivant est déclenché. Ces déclencheurs peuvent être propagés du service au service, ou gérés par un coordinateur saga ou « Orchestrator ». Si une mise à jour échoue à tout moment pendant le processus, les services qui ont déjà effectué leurs mises à jour appliquent une logique spécifique pour les inverser.

Une autre option consiste à utiliser la conception pilotée par domaine (DDD) et la séparation des responsabilités de commande/requête (CQRS), comme décrit dans le [livre électronique sur les microservices .net](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/). En particulier, l’utilisation d’événements de domaine ou d’une [source d’événements](https://martinfowler.com/eaaDev/EventSourcing.html) peut aider à garantir que les mises à jour sont toujours&mdash;es si elles ne sont pas immédiatement&mdash;appliquées.

>[!div class="step-by-step"]
>[Précédent](application-performance-management.md)
