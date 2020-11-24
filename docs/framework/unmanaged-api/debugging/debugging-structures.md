---
title: Structures de débogage
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: bf84f8ddb1e86da3b9d0e4326584e61304640558
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676268"
---
# <a name="debugging-structures"></a>Structures de débogage

Cette section décrit les structures non managées utilisées par l'API de débogage.

## <a name="in-this-section"></a>Dans cette section

 [Structure CLRDATA_ADDRESS_RANGE](clrdata-address-range-structure.md) Définit une plage d’adresses.

 [Structure CLRDATA_IL_ADDRESS_MAP](clrdata-il-address-map-structure.md) Définit un mappage IL à adresse

 [Structure CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) Définit la version de produit du common language runtime (CLR) à des fins de débogage.

 [CodeChunkInfo, structure](codechunkinfo-structure.md) Représente un segment de code unique en mémoire.

 [COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contient des informations sur les fonctions qui sont actuellement actives dans les frames d’un thread.

 [Structure COR_ARRAY_LAYOUT](cor-array-layout-structure.md) Fournit des informations sur la disposition d’un objet tableau en mémoire.

 [COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contient les décalages utilisés pour mapper du code MSIL (Microsoft Intermediate Language) au code natif.

 [COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contient les informations de décalage pour une plage de code.

 [Structure COR_FIELD](cor-field-structure.md) Fournit des informations à propos d’un champ dans un objet.

 [Structure COR_GC_REFERENCE](cor-gc-reference-structure.md) Contient des informations sur un objet qui doit être récupéré par le garbage collector.

 [Structure COR_HEAPINFO](cor-heapinfo-structure.md) Fournit des informations générales sur le tas garbage collection, y compris s’il est énumérable.

 [Structure COR_HEAPOBJECT](cor-heapobject-structure.md) Fournit des informations à propos d’un objet sur le tas managé.

 [COR_IL_MAP](cor-il-map-structure.md) Spécifie les modifications dans l’offset relatif d’une fonction.

 [Structure COR_SEGMENT](cor-segment-structure.md) Contient des informations sur une zone de mémoire dans le tas managé.

 [Structure COR_TYPEID](cor-typeid-structure.md) Contient un identificateur de type.

 [Structure COR_TYPE_LAYOUT](cor-type-layout-structure.md) Fournit des informations sur la disposition d’un objet en mémoire.

 [COR_VERSION](cor-version-structure.md) Stocke le numéro de version en quatre parties standard du common language runtime.

 [CorDebugBlockingObject, structure](cordebugblockingobject-structure.md) Définit un objet qui bloque un thread et la raison pour laquelle le thread est bloqué.

 [CorDebugEHClause, structure](cordebugehclause-structure.md) Représente une clause de gestion des exceptions pour une partie donnée du langage intermédiaire (IL).

 [Cordebugexceptionobjectstackframe,, structure](cordebugexceptionobjectstackframe-structure.md) Représente les informations de frame de pile d’un objet exception.

 [Cordebugguidtotypemapping,, structure](cordebugguidtotypemapping-structure.md) Mappe un GUID Windows Runtime à son objet [ICorDebugType](icordebugtype-interface.md) correspondant.

 [DacpGetModuleAddress, structure](dacpgetmoduleaddress-structure.md) Définit le conteneur pour une demande d’adresse de module.

 [DacpMethodDescData, structure](dacpmethoddescdata-structure.md) Définit une mémoire tampon de transport pour les informations d’exécution d’une méthode.

 [DacpModuleData, structure](dacpmoduledata-structure.md) Définit une mémoire tampon de transport pour les informations d’exécution d’un module.

 [DacpReJitData, structure](dacprejitdata-structure.md) Définit les informations de base sur une méthode instrumentée de profileur donnée.

 [Structure StackTrace_SimpleContext](stacktrace-simplecontext-structure.md) Fournit un contexte simple qui peut être utilisé à la place d’une `CONTEXT` structure complète.

## <a name="related-sections"></a>Sections connexes

 [Débogage des coclasses](debugging-coclasses.md)

 [Interfaces de débogage](debugging-interfaces.md)

 [Fonctions statiques globales du débogage](debugging-global-static-functions.md)

 [Énumérations de débogage](debugging-enumerations.md)

 [Débogage](index.md)
