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
# <a name="debugging-structures"></a>Structures de débogage

Cette section décrit les structures non managées utilisées par l'API de débogage.

## <a name="in-this-section"></a>Dans cette section
 [Structure de CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) définit une plage d’adresses.

 [Structure de CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) définit un langage intermédiaire pour le mappage d’adresses

 [CLR_DEBUGGING_VERSION, Structure](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) définit la version de produit du common language runtime (CLR) pour le débogage.

 [CodeChunkInfo (Structure)](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) représente un bloc de code en mémoire unique.

 [COR_ACTIVE_FUNCTION](cor-active-function-structure.md) contient des informations sur les fonctions qui sont actuellement actives dans les frames d’un thread.

 [Cor_array_layout, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) fournit des informations sur la disposition d’un objet array en mémoire.

 [COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) contient les décalages qui sont utilisés pour mapper le langage intermédiaire Microsoft (MSIL) de code en code natif.

 [COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) contient les informations de décalage pour une plage de code.

 [Cor_field, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) fournit des informations sur un champ dans un objet.

 [Cor_gc_reference, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) contient des informations sur un objet qui doit être le garbage collector.

 [Cor_heapinfo, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) fournit des informations générales sur le tas de garbage collection, notamment si elle est énumérable.

 [Cor_heapobject, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) fournit des informations sur un objet sur le tas managé.

 [COR_IL_MAP](cor-il-map-structure.md) indique des modifications dans le décalage relatif d’une fonction.

 [Cor_segment, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) contient des informations sur une région de mémoire dans le tas managé.

 [Cor_typeid, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) contient un identificateur de type.

 [Cor_type_layout, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) fournit des informations sur la disposition d’un objet en mémoire.

 [COR_VERSION](cor-version-structure.md) stocke le numéro de version en quatre parties standard du common language runtime.

 [CorDebugBlockingObject, Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) définit un objet qui bloque un thread et la raison pour laquelle pourquoi le thread est bloqué.

 [Cordebugehclause, Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) représente une clause d’exception (GE) de gestion d’un élément de langage intermédiaire (IL).

 [Cordebugexceptionobjectstackframe, Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) à partir d’un objet d’exception, les informations de frame de pile représente.

 [Cordebugguidtotypemapping, Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) mappe un GUID de Runtime Windows correspondant [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objet.

 [Structure de DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) définit le conteneur pour une demande d’adresse de module.

 [Structure de DacpMethodDescData](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) définit une mémoire tampon de transport pour les informations d’exécution d’une méthode.

 [Structure de DacpModuleData](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) définit une mémoire tampon de transport pour les informations d’exécution d’un module.

 [Structure de DacpReJitData](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) définit les informations de base sur une méthode donnée instrumentée du profileur.

 [StackTrace_SimpleContext (Structure)](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) fournit un contexte simple qui peut être utilisé à la place d’un intégral `CONTEXT` structure.

## <a name="related-sections"></a>Rubriques connexes

 [Coclasses de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [Fonctions statiques globales de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
