---
title: Conception et développement d’applications .NET à plusieurs conteneurs et basées sur des microservices
description: Architecture des Microservices .NET pour les applications .NET en conteneur | Comprendre l’architecture externe pour la conception et le développement d’applications .NET à plusieurs conteneurs et basées sur des microservices.
ms.date: 10/02/2018
ms.openlocfilehash: 8c2f828e9913a0efcdf580371124b0f624daeffe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70296625"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Conception et développement d’applications .NET à plusieurs conteneurs et basées sur des microservices

*Le développement d’applications microservices conteneurisées signifie que vous construisez des applications multi-conteneurs. Cependant, une application multi-conteneurs pourrait également être plus simple, par exemple, une application à trois niveaux, et ne peut pas être construite à l’aide d’une architecture de microservice.*

Précédemment, nous avons posé la question : « Docker est-il nécessaire pour générer une architecture de microservice ? » La réponse est clairement non. Docker est un activateur qui peut fournir des avantages significatifs, mais les conteneurs et Docker ne sont pas obligatoires pour les microservices. Par exemple, vous pouvez créer une application basée sur des microservices avec ou sans Docker en utilisant Azure Service Fabric, qui prend en charge des microservices exécutés en tant que processus simples ou en tant que conteneurs Docker.

Toutefois, si vous savez comment concevoir et développer une application basée sur des microservices qui est également basée sur des conteneurs Docker, vous serez en mesure de concevoir et développer n’importe quel modèle d’application plus simple. Par exemple, vous pouvez concevoir une application à trois niveaux qui requiert également une approche de plusieurs conteneurs. Par conséquent, et parce que les architectures de microservice sont une tendance majeure dans le milieu des conteneurs, cette section se concentre sur une implémentation d’architecture de microservice qui utilise des conteneurs Docker.

>[!div class="step-by-step"]
>[Suivant précédent](../docker-application-development-process/docker-app-development-workflow.md)
>[Next](microservice-application-design.md)
