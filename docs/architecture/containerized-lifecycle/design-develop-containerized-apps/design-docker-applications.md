---
title: Concevoir des applications Docker
description: Vous trouverez ici une référence à un guide détaillé de l’architecture des microservices, car le présent guide ne traite pas ce sujet en détail.
ms.date: 08/06/2020
ms.openlocfilehash: b63d4344abb358a393587bdacf91f6091b531af0
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915978"
---
# <a name="design-docker-applications"></a><span data-ttu-id="6d253-103">Concevoir des applications Docker</span><span class="sxs-lookup"><span data-stu-id="6d253-103">Design Docker applications</span></span>

<span data-ttu-id="6d253-104">Les concepts fondamentaux des conteneurs et de Docker vous ont été présentés dans le chapitre 1.</span><span class="sxs-lookup"><span data-stu-id="6d253-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="6d253-105">Il s’agit du niveau d’information de base dont vous avez besoin pour débuter.</span><span class="sxs-lookup"><span data-stu-id="6d253-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="6d253-106">Or, les applications d’entreprise peuvent être complexes et comporter non pas un mais plusieurs services ou conteneurs.</span><span class="sxs-lookup"><span data-stu-id="6d253-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="6d253-107">Pour ces cas d’usage particuliers, vous devez connaître d’autres approches de conception, notamment l’architecture orientée service (SOA, Service-Oriented Architecture) et les concepts plus avancés des microservices et de l’orchestration de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="6d253-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="6d253-108">La portée de ce document n’est pas limitée aux microservices, mais à tout cycle de vie d’application de la station d’accueil. par conséquent, il n’explore pas l’architecture des microservices en profondeur, car vous pouvez également utiliser des conteneurs et un Dockeur avec une SOA, des tâches d’arrière-plan ou des travaux en arrière-plan standard, ou même avec des approches de déploiement</span><span class="sxs-lookup"><span data-stu-id="6d253-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you can also use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="6d253-109">**Plus d’informations** Pour en savoir plus sur les applications d’entreprise et l’architecture de microservices en profondeur, lisez le guide [net microservices : architecture pour les applications .net en conteneur](../../microservices/index.md) que vous pouvez également télécharger à partir de <https://aka.ms/MicroservicesEbook> .</span><span class="sxs-lookup"><span data-stu-id="6d253-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="6d253-110">Toutefois, avant d’aborder le cycle de vie de l’application et DevOps, il est important de savoir comment vous allez concevoir et créer votre application, et quels sont vos choix de conception.</span><span class="sxs-lookup"><span data-stu-id="6d253-110">However, before you get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6d253-111">[Précédent](index.md) 
> [Suivant](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="6d253-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
