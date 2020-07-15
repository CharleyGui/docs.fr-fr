---
title: Événements ETW du CLR
description: 'Consultez les articles sur les événements de suivi d’événements common language runtime (CLR) pour Windows (ETW). Il existe deux fournisseurs d’événements : le fournisseur de Runtime et le fournisseur d’arrêt.'
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
ms.openlocfilehash: 22a2f027462d67d5a933972a7420c5f0e38353e5
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309831"
---
# <a name="clr-etw-events"></a><span data-ttu-id="40dcb-104">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="40dcb-104">CLR ETW Events</span></span>
<span data-ttu-id="40dcb-105">Les rubriques de cette section décrivent le suivi d’événements pour les événements Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="40dcb-105">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="40dcb-106">Chaque événement est associé à un mot clé et à un niveau, qui sont décrits dans la rubrique [Niveaux et mots clés ETW du CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="40dcb-106">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="40dcb-107">Le CLR a deux fournisseurs pour les événements :</span><span class="sxs-lookup"><span data-stu-id="40dcb-107">The CLR has two providers for the events:</span></span>  
  
- <span data-ttu-id="40dcb-108">Le fournisseur de runtime, qui déclenche des événements en fonction des mots clés (catégories d’événements) activés.</span><span class="sxs-lookup"><span data-stu-id="40dcb-108">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="40dcb-109">Le GUID du fournisseur de runtime du CLR est e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="40dcb-109">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
- <span data-ttu-id="40dcb-110">Le fournisseur d’arrêt, qui est réservé à des usages spécifiques.</span><span class="sxs-lookup"><span data-stu-id="40dcb-110">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="40dcb-111">Le GUID du fournisseur d’arrêt du CLR est a669021c-c450-4609-a035-5af59af4df18.</span><span class="sxs-lookup"><span data-stu-id="40dcb-111">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="40dcb-112">Pour plus d’informations sur les fournisseurs, consultez [Fournisseurs ETW du CLR](clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="40dcb-112">For more information about the providers, see [CLR ETW Providers](clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40dcb-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="40dcb-113">In This Section</span></span>  
 [<span data-ttu-id="40dcb-114">Événements d'information du runtime</span><span class="sxs-lookup"><span data-stu-id="40dcb-114">Runtime Information Events</span></span>](runtime-information-etw-events.md)  
 <span data-ttu-id="40dcb-115">Capture des informations sur l’exécution, notamment la référence, le numéro de version, le mode d’activation du runtime, les paramètres de ligne de commande avec lesquels il a été démarré, le GUID (le cas échéant) et d’autres informations pertinentes.</span><span class="sxs-lookup"><span data-stu-id="40dcb-115">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="40dcb-116">Événement d'exception Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="40dcb-116">Exception Thrown_V1 Event</span></span>](exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="40dcb-117">Capture des informations sur les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="40dcb-117">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="40dcb-118">Événements de conflit</span><span class="sxs-lookup"><span data-stu-id="40dcb-118">Contention Events</span></span>](contention-etw-events.md)  
 <span data-ttu-id="40dcb-119">Capture des informations sur les conflits de verrous du moniteur ou de verrous natifs utilisés par le runtime.</span><span class="sxs-lookup"><span data-stu-id="40dcb-119">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="40dcb-120">Événements de pool de threads</span><span class="sxs-lookup"><span data-stu-id="40dcb-120">Thread Pool Events</span></span>](thread-pool-etw-events.md)  
 <span data-ttu-id="40dcb-121">Capture des informations sur les pools de threads de travail et les pools de threads d’E/S.</span><span class="sxs-lookup"><span data-stu-id="40dcb-121">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="40dcb-122">Événements de chargeur</span><span class="sxs-lookup"><span data-stu-id="40dcb-122">Loader Events</span></span>](loader-etw-events.md)  
 <span data-ttu-id="40dcb-123">Capture des informations sur le chargement et le déchargement des domaines d’application, des assemblys et des modules.</span><span class="sxs-lookup"><span data-stu-id="40dcb-123">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="40dcb-124">Événements de méthode</span><span class="sxs-lookup"><span data-stu-id="40dcb-124">Method Events</span></span>](method-etw-events.md)  
 <span data-ttu-id="40dcb-125">Capture des informations sur les méthodes CLR pour la résolution des symboles.</span><span class="sxs-lookup"><span data-stu-id="40dcb-125">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="40dcb-126">Événements de garbage collection</span><span class="sxs-lookup"><span data-stu-id="40dcb-126">Garbage Collection Events</span></span>](garbage-collection-etw-events.md)  
 <span data-ttu-id="40dcb-127">Capture des informations relatives au garbage collection, pour vous aider lors du diagnostic et du débogage.</span><span class="sxs-lookup"><span data-stu-id="40dcb-127">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="40dcb-128">Événements de traçage JIT</span><span class="sxs-lookup"><span data-stu-id="40dcb-128">JIT Tracing Events</span></span>](jit-tracing-etw-events.md)  
 <span data-ttu-id="40dcb-129">Capture des informations sur l’incorporation (inlining) juste à temps (JIT) et les appels tail JIT.</span><span class="sxs-lookup"><span data-stu-id="40dcb-129">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="40dcb-130">Événements d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="40dcb-130">Interop Events</span></span>](interop-etw-events.md)  
 <span data-ttu-id="40dcb-131">Capture des informations sur la mise en cache et la génération du stub MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="40dcb-131">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="40dcb-132">Événements ARM</span><span class="sxs-lookup"><span data-stu-id="40dcb-132">ARM Events</span></span>](application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="40dcb-133">Capture des informations de diagnostic détaillées sur l’état d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="40dcb-133">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="40dcb-134">Événements de sécurité</span><span class="sxs-lookup"><span data-stu-id="40dcb-134">Security Events</span></span>](security-etw-events.md)  
 <span data-ttu-id="40dcb-135">Capture des informations sur la vérification de nom fort et la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="40dcb-135">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="40dcb-136">Événement de pile</span><span class="sxs-lookup"><span data-stu-id="40dcb-136">Stack Event</span></span>](stack-etw-event.md)  
 <span data-ttu-id="40dcb-137">Capture des informations utilisées avec d’autres événements pour générer des traces de pile après le déclenchement d’un événement.</span><span class="sxs-lookup"><span data-stu-id="40dcb-137">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40dcb-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40dcb-138">See also</span></span>

- [<span data-ttu-id="40dcb-139">Améliorer le débogage et le réglage des performances à l'aide du suivi ETW</span><span class="sxs-lookup"><span data-stu-id="40dcb-139">Improve Debugging And Performance Tuning With ETW</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)
- [<span data-ttu-id="40dcb-140">Contrôle de l'enregistrement .NET Framework</span><span class="sxs-lookup"><span data-stu-id="40dcb-140">Controlling .NET Framework Logging</span></span>](controlling-logging.md)
- [<span data-ttu-id="40dcb-141">Fournisseurs ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="40dcb-141">CLR ETW Providers</span></span>](clr-etw-providers.md)
- [<span data-ttu-id="40dcb-142">Niveaux et mots clés ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="40dcb-142">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)
- [<span data-ttu-id="40dcb-143">Événements ETW dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="40dcb-143">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
