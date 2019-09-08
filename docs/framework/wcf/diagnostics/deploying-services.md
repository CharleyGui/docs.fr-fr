---
title: Déploiement de services
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 684b781c568518cfb321d8021e4f7062e855e6aa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798143"
---
# <a name="deploying-services"></a><span data-ttu-id="5dbf1-102">Déploiement de services</span><span class="sxs-lookup"><span data-stu-id="5dbf1-102">Deploying Services</span></span>
<span data-ttu-id="5dbf1-103">Cette rubrique décrit comment vous pouvez déployer une application Windows Communication Foundation (WCF) dans un environnement d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5dbf1-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="5dbf1-104">Choix de l'environnement d'hébergement de votre application</span><span class="sxs-lookup"><span data-stu-id="5dbf1-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="5dbf1-105">Les services WCF sont conçus pour s’exécuter dans n’importe quel processus Windows qui prend en charge le code managé.</span><span class="sxs-lookup"><span data-stu-id="5dbf1-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="5dbf1-106">Pour devenir actif, un service doit être hébergé dans un environnement d'exécution qui le crée et contrôle son contexte et sa durée de vie.</span><span class="sxs-lookup"><span data-stu-id="5dbf1-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="5dbf1-107">Les options d'hébergement vont de l'exécution à l'intérieur de l'application console la plus simple à une exécution dans des environnements serveur comme un service Windows et les services Internet (IIS) ou dans un processus de travail géré par WAS (Windows Activation Services).</span><span class="sxs-lookup"><span data-stu-id="5dbf1-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="5dbf1-108">Pour passer en revue les différentes options d’hébergement pour votre application WCF, consultez [services d’hébergement](../hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="5dbf1-108">To review the different hosting options for your WCF application, see [Hosting Services](../hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dbf1-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5dbf1-109">See also</span></span>

- [<span data-ttu-id="5dbf1-110">Hébergement</span><span class="sxs-lookup"><span data-stu-id="5dbf1-110">Hosting</span></span>](../feature-details/hosting.md)
- [<span data-ttu-id="5dbf1-111">Hébergement de services</span><span class="sxs-lookup"><span data-stu-id="5dbf1-111">Hosting Services</span></span>](../hosting-services.md)
