---
title: ICorDebugProcess5::EnumerateHeap, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
ms.openlocfilehash: 9386c77cc98df17d797d5886e1603ffc4824b6dc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205235"
---
# <a name="icordebugprocess5enumerateheap-method"></a>ICorDebugProcess5::EnumerateHeap, méthode
Obtient un énumérateur pour les objets sur le tas managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppObject`  
 à Pointeur vers l’adresse d’un objet d’interface [icordebugheapenum,](icordebugheapenum-interface.md) qui est un énumérateur pour les objets qui résident sur le tas managé.  
  
## <a name="remarks"></a>Remarks  
 Avant d’appeler la `ICorDebugProcess5::EnumerateHeap` méthode, vous devez appeler la méthode [ICorDebugProcess5 :: getgcheapinformation,](icordebugprocess5-getgcheapinformation-method.md) et examiner la valeur du `areGCStructuresValid` champ de l’objet [COR_HEAPINFO](cor-heapinfo-structure.md) retourné pour vous assurer que le segment de mémoire garbage collection dans son état actuel est énumérable. De plus, `ICorDebugProcess5::EnumerateHeap` retourne `E_FAIL` si vous attachez trop tôt au cours de la durée de vie du processus, avant d’allouer de la mémoire pour le tas managé.  
  
 L’objet d’interface [icordebugheapenum,](icordebugheapenum-interface.md) est un énumérateur standard dérivé de l’interface ICorDebugEnum qui vous permet d’énumérer des objets [COR_HEAPOBJECT](cor-heapobject-structure.md) . Cette méthode remplit l’objet de collection [icordebugheapenum,](icordebugheapenum-interface.md) avec [COR_HEAPOBJECT](cor-heapobject-structure.md) instances qui fournissent des informations sur tous les objets. La collection peut également inclure des instances [COR_HEAPOBJECT](cor-heapobject-structure.md) qui fournissent des informations sur les objets qui ne sont enracinés par aucun objet, mais qui n’ont pas encore été collectés par le garbage collector.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess5, interface](icordebugprocess5-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
