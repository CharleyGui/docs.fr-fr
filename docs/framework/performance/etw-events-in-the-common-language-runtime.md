---
title: Événements ETW dans le Common Language Runtime
description: Lisez un résumé et des liens d’affichage concernant les événements de suivi d’événements pour Windows (ETW) dans le common language runtime (CLR).
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
ms.openlocfilehash: aa422dcb7efbc0f6f7f09e09a6c9e44b40ada86b
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309480"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="c34eb-103">Événements ETW dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="c34eb-103">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="c34eb-104">Le CLR (Common Language Runtime) fournit des informations de diagnostic utiles pour le suivi d’événements pour Windows (ETW) par le biais d’une grande variété d’événements de débogage et de profilage.</span><span class="sxs-lookup"><span data-stu-id="c34eb-104">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="c34eb-105">Les événements ETW du CLR tirent parti du système de suivi Windows (ETW) pour améliorer la prise en charge du profilage et du débogage déjà proposée par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="c34eb-105">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="c34eb-106">Des informations supplémentaires sur ETW sont disponibles dans l’article [améliorer le débogage et le réglage des performances avec ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) .</span><span class="sxs-lookup"><span data-stu-id="c34eb-106">More information about ETW is available in the [Improve Debugging and Performance Tuning with ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) article.</span></span> <span data-ttu-id="c34eb-107">Des informations relatives à Xperf sont disponibles à la page [Windows Performance Toolkit - Xperf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) du blog NTDebugging.</span><span class="sxs-lookup"><span data-stu-id="c34eb-107">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="c34eb-108">Le .NET Framework 4 ou version ultérieure est requis pour tous les événements décrits dans les rubriques relatives aux événements.</span><span class="sxs-lookup"><span data-stu-id="c34eb-108">The .NET Framework 4 or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="c34eb-109">Le système d’exploitation Windows Vista est le client minimal pris en charge, et Windows Server 2008 est le serveur minimal pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c34eb-109">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c34eb-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c34eb-110">In This Section</span></span>  
 [<span data-ttu-id="c34eb-111">Contrôle de l'enregistrement .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c34eb-111">Controlling .NET Framework Logging</span></span>](controlling-logging.md)  
 <span data-ttu-id="c34eb-112">Décrit les outils et les commandes permettant de capturer et d’afficher des événements ETW.</span><span class="sxs-lookup"><span data-stu-id="c34eb-112">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="c34eb-113">Fournisseurs ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="c34eb-113">CLR ETW Providers</span></span>](clr-etw-providers.md)  
 <span data-ttu-id="c34eb-114">Fournit des informations sur les fournisseurs d’arrêt et de runtime, et sur la façon de les utiliser pour collecter des données ETW.</span><span class="sxs-lookup"><span data-stu-id="c34eb-114">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="c34eb-115">Niveaux et mots clés ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="c34eb-115">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="c34eb-116">Décrit les mots clés pour les fournisseurs d’arrêt et de runtime qui permettent de filtrer des événements par catégorie.</span><span class="sxs-lookup"><span data-stu-id="c34eb-116">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="c34eb-117">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="c34eb-117">CLR ETW Events</span></span>](clr-etw-events.md)  
 <span data-ttu-id="c34eb-118">Fournit des informations détaillées sur les événements ETW du CLR, leurs mots clés, leurs niveaux et leurs données d’événement.</span><span class="sxs-lookup"><span data-stu-id="c34eb-118">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c34eb-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c34eb-119">See also</span></span>

- [<span data-ttu-id="c34eb-120">ETW Events in the .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c34eb-120">ETW Events in the .NET Framework</span></span>](etw-events.md)
