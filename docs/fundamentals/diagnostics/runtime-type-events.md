---
title: Événements d’exécution du système de type
description: Consultez événements du Runtime .NET qui recueillent des informations de diagnostic spécifiques au système de type .NET, telles que TypeLoadStart et TypeLoadStop.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- type system events (CoreCLR)
- ETW, EventPipe, LTTng type system events (CoreCLR)
ms.openlocfilehash: 8eee89cddb0098da2cb449a4be21945adac725e3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96588593"
---
# <a name="net-runtime-type-events"></a><span data-ttu-id="28261-103">Événements de type .NET Runtime</span><span class="sxs-lookup"><span data-stu-id="28261-103">.NET runtime type events</span></span>

<span data-ttu-id="28261-104">Ces événements collectent des informations relatives au chargement des types.</span><span class="sxs-lookup"><span data-stu-id="28261-104">These events collect information relating to loading types.</span></span> <span data-ttu-id="28261-105">Pour plus d’informations sur l’utilisation de ces événements à des fins de diagnostic, consultez [journalisation et traçage d’applications .net](../../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="28261-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="typeloadstart-event"></a><span data-ttu-id="28261-106">Événement TypeLoadStart</span><span class="sxs-lookup"><span data-stu-id="28261-106">TypeLoadStart Event</span></span>

|<span data-ttu-id="28261-107">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="28261-107">Keyword for raising the event</span></span>|<span data-ttu-id="28261-108">Événement</span><span class="sxs-lookup"><span data-stu-id="28261-108">Event</span></span>|<span data-ttu-id="28261-109">Level</span><span class="sxs-lookup"><span data-stu-id="28261-109">Level</span></span>|  
|-----------------------------------|-----------|-----------|  
|<span data-ttu-id="28261-110">`TypeDiagnosticKeyword` (0x8000000000)</span><span class="sxs-lookup"><span data-stu-id="28261-110">`TypeDiagnosticKeyword` (0x8000000000)</span></span>|<span data-ttu-id="28261-111">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="28261-111">Informational (4)</span></span>|  

|<span data-ttu-id="28261-112">Événement</span><span class="sxs-lookup"><span data-stu-id="28261-112">Event</span></span>|<span data-ttu-id="28261-113">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="28261-113">Event ID</span></span>|<span data-ttu-id="28261-114">Description</span><span class="sxs-lookup"><span data-stu-id="28261-114">Description</span></span>|  
|-----------|--------------|-----------------|  
|`TypeLoadStart`|<span data-ttu-id="28261-115">73</span><span class="sxs-lookup"><span data-stu-id="28261-115">73</span></span>|<span data-ttu-id="28261-116">Un chargement de type a démarré.</span><span class="sxs-lookup"><span data-stu-id="28261-116">A type load has started.</span></span>|

|<span data-ttu-id="28261-117">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="28261-117">Field name</span></span>|<span data-ttu-id="28261-118">Type de données</span><span class="sxs-lookup"><span data-stu-id="28261-118">Data type</span></span>|<span data-ttu-id="28261-119">Description</span><span class="sxs-lookup"><span data-stu-id="28261-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|<span data-ttu-id="28261-120">ID de l’opération de chargement de type.</span><span class="sxs-lookup"><span data-stu-id="28261-120">ID for the type load operation.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="28261-121">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="28261-121">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="typeloadstop-event"></a><span data-ttu-id="28261-122">Événement TypeLoadStop</span><span class="sxs-lookup"><span data-stu-id="28261-122">TypeLoadStop Event</span></span>

|<span data-ttu-id="28261-123">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="28261-123">Keyword for raising the event</span></span>|<span data-ttu-id="28261-124">Level</span><span class="sxs-lookup"><span data-stu-id="28261-124">Level</span></span>|  
|-----------------------------------|-----------|-----------|  
|<span data-ttu-id="28261-125">`TypeDiagnosticKeyword` (0x8000000000)</span><span class="sxs-lookup"><span data-stu-id="28261-125">`TypeDiagnosticKeyword` (0x8000000000)</span></span>|<span data-ttu-id="28261-126">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="28261-126">Informational (4)</span></span>|  

|<span data-ttu-id="28261-127">Événement</span><span class="sxs-lookup"><span data-stu-id="28261-127">Event</span></span>|<span data-ttu-id="28261-128">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="28261-128">Event ID</span></span>|<span data-ttu-id="28261-129">Description</span><span class="sxs-lookup"><span data-stu-id="28261-129">Description</span></span>|  
|-----------|--------------|-----------------|  
|`TypeLoadStop`|<span data-ttu-id="28261-130">74</span><span class="sxs-lookup"><span data-stu-id="28261-130">74</span></span>|<span data-ttu-id="28261-131">Une charge de type est terminée.</span><span class="sxs-lookup"><span data-stu-id="28261-131">A type load is finished.</span></span>|

|<span data-ttu-id="28261-132">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="28261-132">Field name</span></span>|<span data-ttu-id="28261-133">Type de données</span><span class="sxs-lookup"><span data-stu-id="28261-133">Data type</span></span>|<span data-ttu-id="28261-134">Description</span><span class="sxs-lookup"><span data-stu-id="28261-134">Description</span></span>|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|<span data-ttu-id="28261-135">ID de l’opération de chargement de type (correspond au TypeLoadStartID de l’événement TypeLoadStart correspondant).</span><span class="sxs-lookup"><span data-stu-id="28261-135">ID for the type load operation (matches the corresponding TypeLoadStart event's TypeLoadStartID).</span></span>|
|`LoadLevel`|`win:UInt16`|<span data-ttu-id="28261-136">Tapez le niveau de charge.</span><span class="sxs-lookup"><span data-stu-id="28261-136">Type load level.</span></span>|
|`TypeID`|`win:UInt64`|<span data-ttu-id="28261-137">Pointeur vers le handle de type.</span><span class="sxs-lookup"><span data-stu-id="28261-137">Pointer to the type handle.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="28261-138">Nom du type.</span><span class="sxs-lookup"><span data-stu-id="28261-138">Name of the type.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="28261-139">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="28261-139">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
