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
# <a name="debugging-structures"></a>Structures de débogage

Cette section décrit les structures non managées utilisées par l'API de débogage.

## <a name="in-this-section"></a>Dans cette section
 [CLRDATA_ADDRESS_RANGE, structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Définit une plage d’adresses.

 [CLRDATA_IL_ADDRESS_MAP, structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Définit un mappage IL à adresse

 [CLR_DEBUGGING_VERSION, structure](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Définit la version de produit du common language runtime (CLR) à des fins de débogage.

 [CodeChunkInfo, structure](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Représente un segment de code unique en mémoire.

 [COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contient des informations sur les fonctions qui sont actuellement actives dans les frames d’un thread.

 [COR_ARRAY_LAYOUT, structure](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Fournit des informations sur la disposition d’un objet tableau en mémoire.

 [COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contient les décalages utilisés pour mapper du code MSIL (Microsoft Intermediate Language) au code natif.

 [COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contient les informations de décalage pour une plage de code.

 [COR_FIELD, structure](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Fournit des informations à propos d’un champ dans un objet.

 [COR_GC_REFERENCE, structure](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Contient des informations sur un objet qui doit être récupéré par le garbage collector.

 [COR_HEAPINFO, structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Fournit des informations générales sur le tas garbage collection, y compris s’il est énumérable.

 [COR_HEAPOBJECT, structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Fournit des informations à propos d’un objet sur le tas managé.

 [COR_IL_MAP](cor-il-map-structure.md) Spécifie les modifications dans l’offset relatif d’une fonction.

 [COR_SEGMENT, structure](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Contient des informations sur une zone de mémoire dans le tas managé.

 [COR_TYPEID, structure](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Contient un identificateur de type.

 [COR_TYPE_LAYOUT, structure](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Fournit des informations sur la disposition d’un objet en mémoire.

 [COR_VERSION](cor-version-structure.md) Stocke le numéro de version en quatre parties standard du common language runtime.

 [CorDebugBlockingObject, structure](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Définit un objet qui bloque un thread et la raison pour laquelle le thread est bloqué.

 [CorDebugEHClause, structure](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Représente une clause de gestion des exceptions pour une partie donnée du langage intermédiaire (IL).

 [Cordebugexceptionobjectstackframe,, structure](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Représente les informations de frame de pile d’un objet exception.

 [Cordebugguidtotypemapping,, structure](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Mappe un GUID Windows Runtime à son objet [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) correspondant.

 [DacpGetModuleAddress, structure](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Définit le conteneur pour une demande d’adresse de module.

 [DacpMethodDescData, structure](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Définit une mémoire tampon de transport pour les informations d’exécution d’une méthode.

 [DacpModuleData, structure](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Définit une mémoire tampon de transport pour les informations d’exécution d’un module.

 [DacpReJitData, structure](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Définit les informations de base sur une méthode instrumentée de profileur donnée.

 [StackTrace_SimpleContext, structure](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Fournit un contexte simple qui peut être utilisé à la place d’une structure `CONTEXT` complète.

## <a name="related-sections"></a>Rubriques connexes

 [Coclasses de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [Fonctions statiques globales de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
