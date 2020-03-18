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
# <a name="design-docker-applications"></a><span data-ttu-id="fca45-103">Concevoir des applications Docker</span><span class="sxs-lookup"><span data-stu-id="fca45-103">Design Docker applications</span></span>

<span data-ttu-id="fca45-104">Les concepts fondamentaux des conteneurs et de Docker vous ont été présentés dans le chapitre 1.</span><span class="sxs-lookup"><span data-stu-id="fca45-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="fca45-105">Il s’agit du niveau d’information de base dont vous avez besoin pour débuter.</span><span class="sxs-lookup"><span data-stu-id="fca45-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="fca45-106">Or, les applications d’entreprise peuvent être complexes et comporter non pas un mais plusieurs services ou conteneurs.</span><span class="sxs-lookup"><span data-stu-id="fca45-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="fca45-107">Pour ces cas d’usage particuliers, vous devez connaître d’autres approches de conception, notamment l’architecture orientée service (SOA, Service-Oriented Architecture) et les concepts plus avancés des microservices et de l’orchestration de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="fca45-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="fca45-108">Le champ d’application de ce document ne se limite pas aux microservices, mais englobe le cycle de vie de n’importe quelle application Docker. Par conséquent, il n’explore pas l’architecture de microservices, car vous pouvez aussi utiliser des conteneurs et Docker avec une architecture SOA normale, des tâches ou des travaux en arrière-plan, voire des approches de déploiement d’applications monolithiques.</span><span class="sxs-lookup"><span data-stu-id="fca45-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="fca45-109">**Plus d’infos** Pour en savoir plus sur les applications d’entreprise et l’architecture des microservices en profondeur, <https://aka.ms/MicroservicesEbook>lisez le guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) que vous pouvez également télécharger à partir de .</span><span class="sxs-lookup"><span data-stu-id="fca45-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="fca45-110">Cependant, avant de vous pencher sur la question du cycle de vie d’application et de DevOps, il est important que vous sachiez comment vous allez concevoir et construire votre application et quels sont vos choix de conception.</span><span class="sxs-lookup"><span data-stu-id="fca45-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fca45-111">[Suivant précédent](index.md)
>[Next](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="fca45-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
