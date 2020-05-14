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
ms.openlocfilehash: 980f563d3b11fbfcce48b6d7c05275af520e14f1
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396502"
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
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne les valeurs suivantes.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|La commande s'est correctement terminée.|  
|`S_FALSE`|Le nombre réel d’instances récupérées, comme indiqué dans `pceltFetched` , est inférieur au nombre d’instances demandé.|  
  
## <a name="remarks"></a>Notes  
 La méthode [ICorDebugVariableHomeEnum :: Next](icordebugvariablehomeenum-next-method.md) récupère un nombre maximal d' `celt` objets commençant à la position actuelle de l’énumérateur. Lorsque la méthode est retournée, `pceltFetched` contient le nombre réel d’objets récupérés.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugVariableHomeEnum, interface](icordebugvariablehomeenum-interface.md)
- [ICorDebugVariableHome, interface](icordebugvariablehome-interface.md)
