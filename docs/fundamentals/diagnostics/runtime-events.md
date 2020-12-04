---
title: Événements d’exécution
description: Passez en revue les événements de diagnostic émis par le Runtime .NET (CoreCLR) qui peuvent être utilisés avec ETW, LTTng ou EventPipe.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- runtime events (CoreCLR)
- ETW, EventPipe runtime events (CoreCLR)
ms.openlocfilehash: 33fa7275ce40934ce043b4d0dba5749c37515755
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96588605"
---
# <a name="net-runtime-events"></a><span data-ttu-id="52913-103">Événements du Runtime .NET</span><span class="sxs-lookup"><span data-stu-id="52913-103">.NET runtime events</span></span>

<span data-ttu-id="52913-104">Le Runtime .NET (CoreCLR) émet différents événements qui peuvent être utilisés pour diagnostiquer les problèmes liés à votre application .NET qui peuvent être consommés via différents mécanismes tels que `ETW` , `LTTng` et `EventPipe` .</span><span class="sxs-lookup"><span data-stu-id="52913-104">The .NET runtime (CoreCLR) emits various events that can be used to diagnose issues with your .NET application that can be consumed via various mechanisms such as `ETW`, `LTTng`, and `EventPipe`.</span></span>

<span data-ttu-id="52913-105">Ce document sert de référence sur les événements déclenchés par le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="52913-105">This document serves as a reference on the events that are fired by .NET Core runtime.</span></span>

<span data-ttu-id="52913-106">Pour les événements de Runtime dans .NET Framework, consultez [événements ETW du CLR](../../framework/performance/clr-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="52913-106">For runtime events in .NET Framework, see [CLR ETW Events](../../framework/performance/clr-etw-events.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="52913-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="52913-107">In this section</span></span>

<span data-ttu-id="52913-108">[Événements de conflit](runtime-contention-events.md)</span><span class="sxs-lookup"><span data-stu-id="52913-108">[Contention Events](runtime-contention-events.md)</span></span>\
<span data-ttu-id="52913-109">Ces événements collectent des informations sur les conflits de verrous du moniteur.</span><span class="sxs-lookup"><span data-stu-id="52913-109">These events collect information about monitor lock contentions.</span></span>

<span data-ttu-id="52913-110">[Événements de garbage collection](runtime-garbage-collection-events.md)</span><span class="sxs-lookup"><span data-stu-id="52913-110">[Garbage Collection Events](runtime-garbage-collection-events.md)</span></span>\
<span data-ttu-id="52913-111">Ces événements collectent des informations relatives au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="52913-111">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="52913-112">Ils facilitent le diagnostic et le débogage, notamment la détermination du nombre de fois que garbage collection a été effectué, la quantité de mémoire libérée pendant la garbage collection, etc.</span><span class="sxs-lookup"><span data-stu-id="52913-112">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc.</span></span>

<span data-ttu-id="52913-113">[Événements d’exception](runtime-exception-events.md)</span><span class="sxs-lookup"><span data-stu-id="52913-113">[Exception Events](runtime-exception-events.md)</span></span>\
<span data-ttu-id="52913-114">Ces événements de Runtime capturent des informations sur les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="52913-114">These runtime events capture information about exceptions that are thrown.</span></span>

<span data-ttu-id="52913-115">[Événements d’interopérabilité](runtime-interop-events.md)</span><span class="sxs-lookup"><span data-stu-id="52913-115">[Interop Events](runtime-interop-events.md)</span></span>\
<span data-ttu-id="52913-116">Ces événements de Runtime capturent des informations sur la génération du stub Common Intermediate Language (CIL).</span><span class="sxs-lookup"><span data-stu-id="52913-116">These runtime events capture information about Common Intermediate Language (CIL) stub generation.</span></span>

<span data-ttu-id="52913-117">[Événements de chargeur et de Binder](runtime-loader-binder-events.md)</span><span class="sxs-lookup"><span data-stu-id="52913-117">[Loader and Binder Events](runtime-loader-binder-events.md)</span></span>\
<span data-ttu-id="52913-118">Ces événements recueillent des informations concernant le chargement et le déchargement des assemblys et des modules.</span><span class="sxs-lookup"><span data-stu-id="52913-118">These events collect information relating to loading and unloading assemblies and modules.</span></span>

<span data-ttu-id="52913-119">[Événements de méthode](runtime-method-events.md)</span><span class="sxs-lookup"><span data-stu-id="52913-119">[Method Events](runtime-method-events.md)</span></span>\
<span data-ttu-id="52913-120">Ces événements collectent des informations spécifiques aux méthodes.</span><span class="sxs-lookup"><span data-stu-id="52913-120">These events collect information that is specific to methods.</span></span> <span data-ttu-id="52913-121">La charge utile de ces événements est requise pour la résolution des symboles.</span><span class="sxs-lookup"><span data-stu-id="52913-121">The payload of these events is required for symbol resolution.</span></span> <span data-ttu-id="52913-122">De plus, ces événements fournissent des informations utiles telles que le nombre de fois qu'une méthode a été appelée.</span><span class="sxs-lookup"><span data-stu-id="52913-122">In addition, these events provide helpful information such as the number of times a method was called.</span></span>

<span data-ttu-id="52913-123">[Événements de thread](runtime-thread-events.md)</span><span class="sxs-lookup"><span data-stu-id="52913-123">[Thread Events](runtime-thread-events.md)</span></span>\
<span data-ttu-id="52913-124">Ces événements collectent des informations sur les threads de travail et d'E/S.</span><span class="sxs-lookup"><span data-stu-id="52913-124">These events collect information about worker and I/O threads.</span></span>

<span data-ttu-id="52913-125">[Événements de type](runtime-type-events.md)</span><span class="sxs-lookup"><span data-stu-id="52913-125">[Type Events](runtime-type-events.md)</span></span>\
<span data-ttu-id="52913-126">Ces événements collectent des informations sur le système de type.</span><span class="sxs-lookup"><span data-stu-id="52913-126">These events collect information about the type system.</span></span>
