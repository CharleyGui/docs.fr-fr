---
title: Structures de débogage
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45a4b5c2a65ae7e4c01ffc3977875e598d076557
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025926"
---
# <a name="debugging-structures"></a><span data-ttu-id="62aac-102">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="62aac-102">Debugging Structures</span></span>

<span data-ttu-id="62aac-103">Cette section décrit les structures non managées utilisées par l'API de débogage.</span><span class="sxs-lookup"><span data-stu-id="62aac-103">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="62aac-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="62aac-104">In This Section</span></span>
 <span data-ttu-id="62aac-105">[Structure de CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) définit une plage d’adresses.</span><span class="sxs-lookup"><span data-stu-id="62aac-105">[CLRDATA_ADDRESS_RANGE Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="62aac-106">[Structure de CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) définit un langage intermédiaire pour le mappage d’adresses</span><span class="sxs-lookup"><span data-stu-id="62aac-106">[CLRDATA_IL_ADDRESS_MAP Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="62aac-107">[CLR_DEBUGGING_VERSION, Structure](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) définit la version de produit du common language runtime (CLR) pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="62aac-107">[CLR_DEBUGGING_VERSION Structure](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="62aac-108">[CodeChunkInfo (Structure)](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) représente un bloc de code en mémoire unique.</span><span class="sxs-lookup"><span data-stu-id="62aac-108">[CodeChunkInfo Structure](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="62aac-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) contient des informations sur les fonctions qui sont actuellement actives dans les frames d’un thread.</span><span class="sxs-lookup"><span data-stu-id="62aac-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="62aac-110">[Cor_array_layout, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) fournit des informations sur la disposition d’un objet array en mémoire.</span><span class="sxs-lookup"><span data-stu-id="62aac-110">[COR_ARRAY_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="62aac-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) contient les décalages qui sont utilisés pour mapper le langage intermédiaire Microsoft (MSIL) de code en code natif.</span><span class="sxs-lookup"><span data-stu-id="62aac-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="62aac-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) contient les informations de décalage pour une plage de code.</span><span class="sxs-lookup"><span data-stu-id="62aac-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="62aac-113">[Cor_field, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) fournit des informations sur un champ dans un objet.</span><span class="sxs-lookup"><span data-stu-id="62aac-113">[COR_FIELD Structure](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="62aac-114">[Cor_gc_reference, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) contient des informations sur un objet qui doit être le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="62aac-114">[COR_GC_REFERENCE Structure](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="62aac-115">[Cor_heapinfo, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) fournit des informations générales sur le tas de garbage collection, notamment si elle est énumérable.</span><span class="sxs-lookup"><span data-stu-id="62aac-115">[COR_HEAPINFO Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="62aac-116">[Cor_heapobject, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) fournit des informations sur un objet sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="62aac-116">[COR_HEAPOBJECT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="62aac-117">[COR_IL_MAP](cor-il-map-structure.md) indique des modifications dans le décalage relatif d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="62aac-117">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="62aac-118">[Cor_segment, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) contient des informations sur une région de mémoire dans le tas managé.</span><span class="sxs-lookup"><span data-stu-id="62aac-118">[COR_SEGMENT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="62aac-119">[Cor_typeid, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) contient un identificateur de type.</span><span class="sxs-lookup"><span data-stu-id="62aac-119">[COR_TYPEID Structure](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="62aac-120">[Cor_type_layout, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) fournit des informations sur la disposition d’un objet en mémoire.</span><span class="sxs-lookup"><span data-stu-id="62aac-120">[COR_TYPE_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="62aac-121">[COR_VERSION](cor-version-structure.md) stocke le numéro de version en quatre parties standard du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="62aac-121">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="62aac-122">[CorDebugBlockingObject, Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) définit un objet qui bloque un thread et la raison pour laquelle pourquoi le thread est bloqué.</span><span class="sxs-lookup"><span data-stu-id="62aac-122">[CorDebugBlockingObject Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="62aac-123">[Cordebugehclause, Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) représente une clause d’exception (GE) de gestion d’un élément de langage intermédiaire (IL).</span><span class="sxs-lookup"><span data-stu-id="62aac-123">[CorDebugEHClause Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="62aac-124">[Cordebugexceptionobjectstackframe, Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) à partir d’un objet d’exception, les informations de frame de pile représente.</span><span class="sxs-lookup"><span data-stu-id="62aac-124">[CorDebugExceptionObjectStackFrame Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="62aac-125">[Cordebugguidtotypemapping, Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) mappe un GUID de Runtime Windows correspondant [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="62aac-125">[CorDebugGuidToTypeMapping Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Maps a Windows Runtime GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="62aac-126">[Structure de DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) définit le conteneur pour une demande d’adresse de module.</span><span class="sxs-lookup"><span data-stu-id="62aac-126">[DacpGetModuleAddress Structure](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="62aac-127">[Structure de DacpMethodDescData](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) définit une mémoire tampon de transport pour les informations d’exécution d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="62aac-127">[DacpMethodDescData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="62aac-128">[Structure de DacpModuleData](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) définit une mémoire tampon de transport pour les informations d’exécution d’un module.</span><span class="sxs-lookup"><span data-stu-id="62aac-128">[DacpModuleData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="62aac-129">[Structure de DacpReJitData](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) définit les informations de base sur une méthode donnée instrumentée du profileur.</span><span class="sxs-lookup"><span data-stu-id="62aac-129">[DacpReJitData Structure](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="62aac-130">[StackTrace_SimpleContext (Structure)](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) fournit un contexte simple qui peut être utilisé à la place d’un intégral `CONTEXT` structure.</span><span class="sxs-lookup"><span data-stu-id="62aac-130">[StackTrace_SimpleContext Structure](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="62aac-131">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="62aac-131">Related Sections</span></span>

 [<span data-ttu-id="62aac-132">Coclasses de débogage</span><span class="sxs-lookup"><span data-stu-id="62aac-132">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [<span data-ttu-id="62aac-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="62aac-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [<span data-ttu-id="62aac-134">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="62aac-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [<span data-ttu-id="62aac-135">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="62aac-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [<span data-ttu-id="62aac-136">Débogage</span><span class="sxs-lookup"><span data-stu-id="62aac-136">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
