---
title: ICorDebugProcess5, interface
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
ms.openlocfilehash: 1953a3e0492e4cfcdaea761b68ea22cf5a4a8ed7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205516"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5, interface
Étend l’interface ICorDebugProcess pour prendre en charge l’accès au tas managé, pour fournir des informations sur garbage collection d’objets managés et pour déterminer si un débogueur charge des images à partir du cache des images natives locales de l’application.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnableNGenPolicy, méthode](icordebugprocess5-enablengenpolicy-method.md)|Définit une valeur qui détermine la façon dont une application charge les images natives lors de l’exécution sous un débogueur managé.|  
|[EnumerateGCReferences, méthode](icordebugprocess5-enumerategcreferences-method.md)|Obtient un énumérateur pour tous les objets qui doivent être récupérés par le garbage collector dans un processus.|  
|[EnumerateHandles, méthode](icordebugprocess5-enumeratehandles-method.md)|Obtient un énumérateur pour les handles d’objet dans un processus.|  
|[EnumerateHeap, méthode](icordebugprocess5-enumerateheap-method.md)|Obtient un énumérateur pour les objets sur le tas managé.|  
|[EnumerateHeapRegions, méthode](icordebugprocess5-enumerateheapregions-method.md)|Obtient un énumérateur pour les régions du tas managé.|  
|[GetArrayLayout, méthode](icordebugprocess5-getarraylayout-method.md)|Obtient des informations sur la disposition d’un tableau en mémoire.|  
|[GetGCHeapInformation, méthode](icordebugprocess5-getgcheapinformation-method.md)|Obtient un pointeur vers une structure [COR_HEAPINFO](cor-heapinfo-structure.md) qui contient des informations sur les objets qui doivent être récupérés par le garbage collector sur le tas managé.|  
|[GetObject, méthode](icordebugprocess5-getobject-method.md)|Obtient un pointeur vers un objet sur le tas managé.|  
|[GetTypeFields, méthode](icordebugprocess5-gettypefields-method.md)|Obtient un pointeur vers un tableau qui contient des informations de champ pour un type en fonction de son identificateur de type.|  
|[GetTypeForTypeID, méthode](icordebugprocess5-gettypefortypeid-method.md)|Obtient un objet de type qui fournit des informations à propos d’un objet en fonction de ses identificateurs de type.|  
|[GetTypeID, méthode](icordebugprocess5-gettypeid-method.md)|Obtient l’identificateur de type pour l’objet à une adresse spécifiée.|  
|[GetTypeLayout, méthode](icordebugprocess5-gettypelayout-method.md)|Obtient des informations sur la disposition d’un objet en mémoire en fonction de son identificateur de type.|  
  
## <a name="remarks"></a>Remarks  
 Cette interface étend logiquement les interfaces ICorDebugProcess, ICorDebugProcess2 et [ICorDebugProcess3](icordebugprocess3-interface.md) .  
  
> [!NOTE]
> Cette interface ne prend pas en charge l’appel à distance, à partir d’un autre ordinateur ou d’un autre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
