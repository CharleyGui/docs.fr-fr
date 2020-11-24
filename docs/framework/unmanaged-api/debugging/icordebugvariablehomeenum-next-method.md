---
title: 'ICorDebugVariableHomeEnum :: Next, méthode'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
ms.openlocfilehash: 4ef4ed19033b0857b9970ee8103bbd92f383898c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679531"
---
# <a name="icordebugvariablehomeenumnext-method"></a>ICorDebugVariableHomeEnum :: Next, méthode

Obtient le nombre spécifié d’instances [ICorDebugVariableHome](icordebugvariablehome-interface.md) qui contiennent des informations sur les variables locales et les arguments d’une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `celt`  
 [in] Nombre d'objets à récupérer.  
  
 `homes`  
 Tableau de pointeurs, chacun pointant vers un objet [ICorDebugVariableHome](icordebugvariablehome-interface.md) qui fournit des informations sur une variable locale ou un argument d’une fonction.  
  
 `pceltFetched`  
 à Nombre d’instances réellement retournées dans les objets.  
  
## <a name="return-value"></a>Valeur renvoyée  

 La méthode retourne les valeurs suivantes.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|La commande s'est correctement terminée.|  
|`S_FALSE`|Le nombre réel d’instances récupérées, comme indiqué dans `pceltFetched` , est inférieur au nombre d’instances demandé.|  
  
## <a name="remarks"></a>Remarques  

 La méthode [ICorDebugVariableHomeEnum :: Next](icordebugvariablehomeenum-next-method.md) récupère un nombre maximal d'  `celt` objets commençant à la position actuelle de l’énumérateur. Lorsque la méthode est retournée, `pceltFetched` contient le nombre réel d’objets récupérés.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugVariableHomeEnum, interface](icordebugvariablehomeenum-interface.md)
- [ICorDebugVariableHome, interface](icordebugvariablehome-interface.md)
