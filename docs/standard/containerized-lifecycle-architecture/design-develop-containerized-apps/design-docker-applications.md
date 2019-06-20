---
title: Concevoir des applications Docker
description: Vous trouverez ici une référence à un guide détaillé de l’architecture des microservices, car le présent guide ne traite pas ce sujet en détail.
ms.date: 02/15/2019
ms.openlocfilehash: 535b6cefb7371014527032972ec27ebfe4b67ebc
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644657"
---
# <a name="design-docker-applications"></a>Concevoir des applications Docker

Les concepts fondamentaux des conteneurs et de Docker vous ont été présentés dans le chapitre 1. Il s’agit du niveau d’information de base dont vous avez besoin pour débuter. Or, les applications d’entreprise peuvent être complexes et comporter non pas un mais plusieurs services ou conteneurs. Pour ces cas d’usage particuliers, vous devez connaître d’autres approches de conception, notamment l’architecture orientée service (SOA, Service-Oriented Architecture) et les concepts plus avancés des microservices et de l’orchestration de conteneurs. Le champ d’application de ce document ne se limite pas aux microservices, mais englobe le cycle de vie de n’importe quelle application Docker. Par conséquent, il n’explore pas l’architecture de microservices, car vous pouvez aussi utiliser des conteneurs et Docker avec une architecture SOA normale, des tâches ou des travaux en arrière-plan, voire des approches de déploiement d’applications monolithiques.

**Plus d’informations** Pour approfondir vos connaissances en matière d’applications d’entreprise et d’architecture de microservices, consultez le guide [NET Microservices : Architecture des applications .NET conteneurisées](../../microservices-architecture/index.md) que vous pouvez également télécharger à l’adresse suivante : <https://aka.ms/MicroservicesEbook>.

Cependant, avant de vous pencher sur la question du cycle de vie d’application et de DevOps, il est important que vous sachiez comment vous allez concevoir et construire votre application et quels sont vos choix de conception.

>[!div class="step-by-step"]
>[Précédent](index.md)
>[Suivant](common-container-design-principles.md)
