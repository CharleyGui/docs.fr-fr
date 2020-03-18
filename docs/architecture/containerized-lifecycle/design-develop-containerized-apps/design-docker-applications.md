---
title: Concevoir des applications Docker
description: Vous trouverez ici une référence à un guide détaillé de l’architecture des microservices, car le présent guide ne traite pas ce sujet en détail.
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68674036"
---
# <a name="design-docker-applications"></a>Concevoir des applications Docker

Les concepts fondamentaux des conteneurs et de Docker vous ont été présentés dans le chapitre 1. Il s’agit du niveau d’information de base dont vous avez besoin pour débuter. Or, les applications d’entreprise peuvent être complexes et comporter non pas un mais plusieurs services ou conteneurs. Pour ces cas d’usage particuliers, vous devez connaître d’autres approches de conception, notamment l’architecture orientée service (SOA, Service-Oriented Architecture) et les concepts plus avancés des microservices et de l’orchestration de conteneurs. Le champ d’application de ce document ne se limite pas aux microservices, mais englobe le cycle de vie de n’importe quelle application Docker. Par conséquent, il n’explore pas l’architecture de microservices, car vous pouvez aussi utiliser des conteneurs et Docker avec une architecture SOA normale, des tâches ou des travaux en arrière-plan, voire des approches de déploiement d’applications monolithiques.

**Plus d’infos** Pour en savoir plus sur les applications d’entreprise et l’architecture des microservices en profondeur, <https://aka.ms/MicroservicesEbook>lisez le guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) que vous pouvez également télécharger à partir de .

Cependant, avant de vous pencher sur la question du cycle de vie d’application et de DevOps, il est important que vous sachiez comment vous allez concevoir et construire votre application et quels sont vos choix de conception.

>[!div class="step-by-step"]
>[Suivant précédent](index.md)
>[Next](common-container-design-principles.md)
