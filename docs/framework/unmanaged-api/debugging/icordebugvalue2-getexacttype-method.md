---
title: ICorDebugValue2::GetExactType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
ms.openlocfilehash: cb5bec66ab02de248109d8aaf444a93e67c2c6d2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720358"
---
# <a name="icordebugvalue2getexacttype-method"></a>ICorDebugValue2::GetExactType, méthode

Obtient un pointeur d’interface vers un objet « ICorDebugType » qui représente le <xref:System.Type> de cette valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppType`  
 à Pointeur vers l’adresse d’un `ICorDebugType` objet qui représente le <xref:System.Type> de la valeur représentée par cet objet « ICorDebugValue2 ».  
  
## <a name="remarks"></a>Remarques  

 La méthode qui prend en charge les génériques `GetExactType` remplace les méthodes [ICorDebugObjectValue :: GetClass](icordebugobjectvalue-getclass-method.md) et [ICorDebugValue :: GetType](icordebugvalue-gettype-method.md) , chacune d’elles retournant des informations sur le type d’une valeur.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
