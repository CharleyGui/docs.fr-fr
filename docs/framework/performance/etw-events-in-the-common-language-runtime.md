---
title: Événements ETW dans le Common Language Runtime
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46ad58813da5b71b884ad55f796db3522b2f1920
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046611"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="28e9a-102">Événements ETW dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="28e9a-102">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="28e9a-103">Le CLR (Common Language Runtime) fournit des informations de diagnostic utiles pour le suivi d’événements pour Windows (ETW) par le biais d’une grande variété d’événements de débogage et de profilage.</span><span class="sxs-lookup"><span data-stu-id="28e9a-103">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="28e9a-104">Les événements ETW du CLR tirent parti du système de suivi Windows (ETW) pour améliorer la prise en charge du profilage et du débogage déjà proposée par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="28e9a-104">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="28e9a-105">Vous trouverez des informations supplémentaires sur ETW dans l’article [Améliorez le débogage et l’optimisation des performances avec ETW](https://go.microsoft.com/fwlink/?LinkID=161142) sur MSDN.</span><span class="sxs-lookup"><span data-stu-id="28e9a-105">More information about ETW is available in the article [Improve Debugging and Performance Tuning with ETW](https://go.microsoft.com/fwlink/?LinkID=161142) on MSDN.</span></span> <span data-ttu-id="28e9a-106">Des informations relatives à Xperf sont disponibles à la page [Windows Performance Toolkit - Xperf](https://go.microsoft.com/fwlink/?LinkID=161144) du blog NTDebugging.</span><span class="sxs-lookup"><span data-stu-id="28e9a-106">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](https://go.microsoft.com/fwlink/?LinkID=161144) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="28e9a-107">Le .NET Framework 4 ou version ultérieure est requis pour tous les événements décrits dans les rubriques relatives aux événements.</span><span class="sxs-lookup"><span data-stu-id="28e9a-107">The .NET Framework 4 or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="28e9a-108">Le système d’exploitation Windows Vista est le client minimal pris en charge, et Windows Server 2008 est le serveur minimal pris en charge.</span><span class="sxs-lookup"><span data-stu-id="28e9a-108">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28e9a-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="28e9a-109">In This Section</span></span>  
 [<span data-ttu-id="28e9a-110">Contrôle de l’enregistrement .NET Framework</span><span class="sxs-lookup"><span data-stu-id="28e9a-110">Controlling .NET Framework Logging</span></span>](controlling-logging.md)  
 <span data-ttu-id="28e9a-111">Décrit les outils et les commandes permettant de capturer et d’afficher des événements ETW.</span><span class="sxs-lookup"><span data-stu-id="28e9a-111">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="28e9a-112">Fournisseurs ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="28e9a-112">CLR ETW Providers</span></span>](clr-etw-providers.md)  
 <span data-ttu-id="28e9a-113">Fournit des informations sur les fournisseurs d’arrêt et de runtime, et sur la façon de les utiliser pour collecter des données ETW.</span><span class="sxs-lookup"><span data-stu-id="28e9a-113">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="28e9a-114">Niveaux et mots clés ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="28e9a-114">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="28e9a-115">Décrit les mots clés pour les fournisseurs d’arrêt et de runtime qui permettent de filtrer des événements par catégorie.</span><span class="sxs-lookup"><span data-stu-id="28e9a-115">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="28e9a-116">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="28e9a-116">CLR ETW Events</span></span>](clr-etw-events.md)  
 <span data-ttu-id="28e9a-117">Fournit des informations détaillées sur les événements ETW du CLR, leurs mots clés, leurs niveaux et leurs données d’événement.</span><span class="sxs-lookup"><span data-stu-id="28e9a-117">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e9a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28e9a-118">See also</span></span>

- [<span data-ttu-id="28e9a-119">Événements ETW dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="28e9a-119">ETW Events in the .NET Framework</span></span>](etw-events.md)
