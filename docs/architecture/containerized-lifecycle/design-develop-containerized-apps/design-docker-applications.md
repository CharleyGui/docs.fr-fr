---
title: Concevoir des applications Docker
description: Vous trouverez ici une référence à un guide détaillé de l’architecture des microservices, car le présent guide ne traite pas ce sujet en détail.
ms.date: 02/15/2019
ms.openlocfilehash: b8a08658ec6c3df3e1aed596a0240223768dd647
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738460"
---
# <a name="design-docker-applications"></a>Concevoir des applications Docker

Les concepts fondamentaux des conteneurs et de Docker vous ont été présentés dans le chapitre 1. Il s’agit du niveau d’information de base dont vous avez besoin pour débuter. Or, les applications d’entreprise peuvent être complexes et comporter non pas un mais plusieurs services ou conteneurs. Pour ces cas d’usage particuliers, vous devez connaître d’autres approches de conception, notamment l’architecture orientée service (SOA, Service-Oriented Architecture) et les concepts plus avancés des microservices et de l’orchestration de conteneurs. La portée de ce document ne se limite pas aux microservices, mais à tout cycle de vie d’application Docker, par conséquent, il n’explore pas l’architecture des microservices en profondeur parce que vous pouvez également utiliser des conteneurs et Docker avec SOA régulière, tâches de fond ou des emplois, ou même avec des approches de déploiement d’applications monolithiques.

**Plus d’infos** Pour en savoir plus sur les applications d’entreprise et l’architecture des microservices en profondeur, <https://aka.ms/MicroservicesEbook>lisez le guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) que vous pouvez également télécharger à partir de .

Cependant, avant de vous pencher sur la question du cycle de vie d’application et de DevOps, il est important que vous sachiez comment vous allez concevoir et construire votre application et quels sont vos choix de conception.

>[!div class="step-by-step"]
>[Suivant précédent](index.md)
>[Next](common-container-design-principles.md)
