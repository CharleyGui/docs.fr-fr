---
title: Structures de débogage
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: 05a321d5025f03d6a0378b462178bf06c0291f48
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123030"
---
# <a name="debugging-structures"></a><span data-ttu-id="681a8-102">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="681a8-102">Debugging Structures</span></span>

<span data-ttu-id="681a8-103">Cette section décrit les structures non managées utilisées par l'API de débogage.</span><span class="sxs-lookup"><span data-stu-id="681a8-103">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="681a8-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="681a8-104">In This Section</span></span>
 <span data-ttu-id="681a8-105">[CLRDATA_ADDRESS_RANGE, structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Définit une plage d’adresses.</span><span class="sxs-lookup"><span data-stu-id="681a8-105">[CLRDATA_ADDRESS_RANGE Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="681a8-106">[CLRDATA_IL_ADDRESS_MAP, structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Définit un mappage IL à adresse</span><span class="sxs-lookup"><span data-stu-id="681a8-106">[CLRDATA_IL_ADDRESS_MAP Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="681a8-107">[CLR_DEBUGGING_VERSION, structure](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Définit la version de produit du common language runtime (CLR) à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="681a8-107">[CLR_DEBUGGING_VERSION Structure](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="681a8-108">[CodeChunkInfo, structure](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Représente un segment de code unique en mémoire.</span><span class="sxs-lookup"><span data-stu-id="681a8-108">[CodeChunkInfo Structure](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="681a8-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contient des informations sur les fonctions qui sont actuellement actives dans les frames d’un thread.</span><span class="sxs-lookup"><span data-stu-id="681a8-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="681a8-110">[COR_ARRAY_LAYOUT, structure](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Fournit des informations sur la disposition d’un objet tableau en mémoire.</span><span class="sxs-lookup"><span data-stu-id="681a8-110">[COR_ARRAY_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="681a8-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contient les décalages utilisés pour mapper du code MSIL (Microsoft Intermediate Language) au code natif.</span><span class="sxs-lookup"><span data-stu-id="681a8-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="681a8-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contient les informations de décalage pour une plage de code.</span><span class="sxs-lookup"><span data-stu-id="681a8-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="681a8-113">[COR_FIELD, structure](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Fournit des informations à propos d’un champ dans un objet.</span><span class="sxs-lookup"><span data-stu-id="681a8-113">[COR_FIELD Structure](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="681a8-114">[COR_GC_REFERENCE, structure](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Contient des informations sur un objet qui doit être récupéré par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="681a8-114">[COR_GC_REFERENCE Structure](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="681a8-115">[COR_HEAPINFO, structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Fournit des informations générales sur le tas garbage collection, y compris s’il est énumérable.</span><span class="sxs-lookup"><span data-stu-id="681a8-115">[COR_HEAPINFO Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="681a8-116">[COR_HEAPOBJECT, structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Fournit des informations à propos d’un objet sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="681a8-116">[COR_HEAPOBJECT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="681a8-117">[COR_IL_MAP](cor-il-map-structure.md) Spécifie les modifications dans l’offset relatif d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="681a8-117">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="681a8-118">[COR_SEGMENT, structure](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Contient des informations sur une zone de mémoire dans le tas managé.</span><span class="sxs-lookup"><span data-stu-id="681a8-118">[COR_SEGMENT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="681a8-119">[COR_TYPEID, structure](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Contient un identificateur de type.</span><span class="sxs-lookup"><span data-stu-id="681a8-119">[COR_TYPEID Structure](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="681a8-120">[COR_TYPE_LAYOUT, structure](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Fournit des informations sur la disposition d’un objet en mémoire.</span><span class="sxs-lookup"><span data-stu-id="681a8-120">[COR_TYPE_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="681a8-121">[COR_VERSION](cor-version-structure.md) Stocke le numéro de version en quatre parties standard du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="681a8-121">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="681a8-122">[CorDebugBlockingObject, structure](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Définit un objet qui bloque un thread et la raison pour laquelle le thread est bloqué.</span><span class="sxs-lookup"><span data-stu-id="681a8-122">[CorDebugBlockingObject Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="681a8-123">[CorDebugEHClause, structure](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Représente une clause de gestion des exceptions pour une partie donnée du langage intermédiaire (IL).</span><span class="sxs-lookup"><span data-stu-id="681a8-123">[CorDebugEHClause Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="681a8-124">[Cordebugexceptionobjectstackframe,, structure](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Représente les informations de frame de pile d’un objet exception.</span><span class="sxs-lookup"><span data-stu-id="681a8-124">[CorDebugExceptionObjectStackFrame Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="681a8-125">[Cordebugguidtotypemapping,, structure](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Mappe un GUID Windows Runtime à son objet [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) correspondant.</span><span class="sxs-lookup"><span data-stu-id="681a8-125">[CorDebugGuidToTypeMapping Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Maps a Windows Runtime GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="681a8-126">[DacpGetModuleAddress, structure](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Définit le conteneur pour une demande d’adresse de module.</span><span class="sxs-lookup"><span data-stu-id="681a8-126">[DacpGetModuleAddress Structure](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="681a8-127">[DacpMethodDescData, structure](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Définit une mémoire tampon de transport pour les informations d’exécution d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="681a8-127">[DacpMethodDescData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="681a8-128">[DacpModuleData, structure](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Définit une mémoire tampon de transport pour les informations d’exécution d’un module.</span><span class="sxs-lookup"><span data-stu-id="681a8-128">[DacpModuleData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="681a8-129">[DacpReJitData, structure](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Définit les informations de base sur une méthode instrumentée de profileur donnée.</span><span class="sxs-lookup"><span data-stu-id="681a8-129">[DacpReJitData Structure](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="681a8-130">[StackTrace_SimpleContext, structure](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Fournit un contexte simple qui peut être utilisé à la place d’une structure `CONTEXT` complète.</span><span class="sxs-lookup"><span data-stu-id="681a8-130">[StackTrace_SimpleContext Structure](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="681a8-131">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="681a8-131">Related Sections</span></span>

 [<span data-ttu-id="681a8-132">Coclasses de débogage</span><span class="sxs-lookup"><span data-stu-id="681a8-132">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [<span data-ttu-id="681a8-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="681a8-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [<span data-ttu-id="681a8-134">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="681a8-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [<span data-ttu-id="681a8-135">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="681a8-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [<span data-ttu-id="681a8-136">Débogage</span><span class="sxs-lookup"><span data-stu-id="681a8-136">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
