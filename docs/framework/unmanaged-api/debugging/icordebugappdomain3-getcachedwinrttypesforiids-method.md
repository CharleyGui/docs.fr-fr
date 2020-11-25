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
ms.openlocfilehash: 2aff86fb63b87869ed13028bd7344afe11363f51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723179"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs, méthode

Obtient un énumérateur pour les types de Windows Runtime mis en cache dans un domaine d’application en fonction de leurs identificateurs d’interface.  
  
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
 dans Nombre de types requis.  
  
 `iidsToResolve`  
 dans Pointeur vers un tableau qui contient les identificateurs d’interface correspondant aux représentations managées des types de Windows Runtime à récupérer.  
  
 `ppTypesEnum`  
 à Pointeur vers l’adresse d’un objet d’interface « ICorDebugTypeEnum » qui permet l’énumération des représentations managées mises en cache des types de Windows Runtime récupérés, en fonction des identificateurs d’interface dans `iidsToResolve` .  
  
## <a name="remarks"></a>Remarques  

 Si la méthode ne parvient pas à récupérer des informations pour un identificateur d’interface spécifique, l’entrée correspondante dans la collection « ICorDebugTypeEnum » aura un type d' `ELEMENT_TYPE_END` erreurs en raison des problèmes de récupération de données ou `ELEMENT_TYPE_VOID` des identificateurs d’interface inconnus.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Windows Runtime  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugAppDomain3, interface](icordebugappdomain3-interface.md)
