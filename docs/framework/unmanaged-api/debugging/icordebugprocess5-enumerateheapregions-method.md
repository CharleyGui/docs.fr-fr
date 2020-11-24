---
title: ICorDebugProcess5::EnumerateHeapRegions, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
ms.openlocfilehash: 5a51670200f8fc8a98ff7b80334253b37c7d89ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671120"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a>ICorDebugProcess5::EnumerateHeapRegions, méthode

Obtient un énumérateur pour les plages de mémoire du tas managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppRegions`  
 à Pointeur vers l’adresse d’un objet d’interface [icordebugheapsegmentenum,](icordebugheapsegmentenum-interface.md) qui est un énumérateur pour les plages de mémoire dans lesquelles les objets résident dans le tas managé.  
  
## <a name="remarks"></a>Remarques  

 Avant d’appeler la `ICorDebugProcess5::EnumerateHeapRegions` méthode, vous devez appeler la méthode [ICorDebugProcess5 :: getgcheapinformation,](icordebugprocess5-getgcheapinformation-method.md) et examiner la valeur du `areGCStructuresValid` champ de l’objet [COR_HEAPINFO](cor-heapinfo-structure.md) retourné pour vous assurer que le segment de mémoire garbage collection dans son état actuel est énumérable. En outre, la `ICorDebugProcess5::EnumerateHeapRegions` méthode retourne `E_FAIL` si vous attachez trop tôt au cours de la durée de vie du processus, avant que les régions de la mémoire ne soient créées.  
  
 Cette méthode permet d’énumérer toutes les régions de mémoire qui peuvent contenir des objets managés, mais elle ne garantit pas que les objets managés résident réellement dans ces régions. L’objet de collection [icordebugheapsegmentenum,](icordebugheapsegmentenum-interface.md) peut inclure des régions de mémoire vides ou réservées.  
  
 L’objet d’interface [icordebugheapsegmentenum,](icordebugheapsegmentenum-interface.md) est un énumérateur standard dérivé de l’interface ICorDebugEnum qui vous permet d’énumérer des objets [COR_SEGMENT](cor-segment-structure.md) . Chaque objet [COR_SEGMENT](cor-segment-structure.md) fournit des informations sur la plage de mémoire d’un segment particulier, ainsi que la génération des objets dans ce segment.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess5, interface](icordebugprocess5-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
