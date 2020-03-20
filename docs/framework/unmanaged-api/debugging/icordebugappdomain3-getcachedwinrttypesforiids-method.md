---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: f8e92ec4f813e8810273a1514298d0739a3d2406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179063"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs, méthode
Obtient un enumérateur pour les types Windows Runtime en cache dans un domaine d’application basé sur leurs identifiants d’interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cReqTypes`  
 [dans] Le nombre de types requis.  
  
 `iidsToResolve`  
 [dans] Un pointeur vers un tableau qui contient les identifiants d’interface correspondant aux représentations gérées des types Windows Runtime à récupérer.  
  
 `ppTypesEnum`  
 [out] Un pointeur à l’adresse d’un objet d’interface "ICorDebugTypeEnum" qui permet le recensement des représentations gérées `iidsToResolve`en cache des types Windows Runtime récupérés, en fonction des identifiants d’interface dans .  
  
## <a name="remarks"></a>Notes   
 Si la méthode ne parvient pas à récupérer des informations pour un identifiant d’interface spécifique, l’entrée correspondante dans la collection "ICorDebugTypeEnum" aura un type d’erreurs dues à des problèmes de récupération de `ELEMENT_TYPE_END` données, ou `ELEMENT_TYPE_VOID` pour des identifiants d’interface inconnus.  
  
## <a name="requirements"></a>Spécifications  
 **Plates-formes:** Windows Runtime  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugAppDomain3, interface](icordebugappdomain3-interface.md)
