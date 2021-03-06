---
title: ICorDebugReferenceValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
ms.openlocfilehash: 343e504e086e740236d7b5977452cc0d789883fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728405"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue, interface

Fournit des méthodes qui gèrent une valeur qui est une référence à un objet. (Autrement dit, cette interface fournit des méthodes qui gèrent un pointeur.) Cette interface implémente « ICorDebugValue ».  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Dereference, méthode](icordebugreferencevalue-dereference-method.md)|Obtient l’objet référencé.|  
|[DereferenceStrong, méthode](icordebugreferencevalue-dereferencestrong-method.md)|Non implémenté. N'appelez pas cette méthode.|  
|[GetValue, méthode](icordebugreferencevalue-getvalue-method.md)|Obtient l’adresse mémoire actuelle de l’objet référencé.|  
|[IsNull, méthode](icordebugreferencevalue-isnull-method.md)|Obtient une valeur qui indique s’il `ICorDebugReferenceValue` s’agit d’une valeur null, auquel cas le `ICorDebugReferenceValue` ne pointe pas vers un objet.|  
|[Méthode SetValue](icordebugreferencevalue-setvalue-method.md)|Définit l’adresse mémoire actuelle. Autrement dit, cette méthode définit cela `ICorDebugReferenceValue` pour pointer vers un objet.|  
  
## <a name="remarks"></a>Remarques  

 Le common language runtime (CLR) peut effectuer une garbage collection sur les objets lorsque le processus débogué est poursuivi. La garbage collection peut déplacer des objets dans la mémoire. Un `ICorDebugReferenceValue` est en collaboration avec le garbage collection afin que ses informations soient mises à jour après l’garbage collection, ou qu’elles soient invalidées implicitement avant le garbage collection.  
  
 L' `ICorDebugReferenceValue` objet peut être invalidé implicitement une fois que le processus débogué a été poursuivi. Le « ICorDebugHandleValue » dérivé n’est pas invalidé tant qu’il n’a pas été explicitement libéré ou exposé.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
