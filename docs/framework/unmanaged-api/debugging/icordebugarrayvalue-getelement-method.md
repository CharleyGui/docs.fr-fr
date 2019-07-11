---
title: ICorDebugArrayValue::GetElement, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 356f7ec9c50ce511883cbf0f5fbcb729493c92af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737573"
---
# <a name="icordebugarrayvaluegetelement-method"></a>ICorDebugArrayValue::GetElement, méthode
Obtient la valeur de l’élément de tableau donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cdim`  
 [in] Le nombre de dimensions de ce `ICorDebugArrayValue` objet.  
  
 Cette valeur est également la taille de la `indices` tableau car sa taille est égale au nombre de dimensions de la `ICorDebugArrayValue` objet.  
  
 `indices`  
 [in] Un tableau de valeurs d’index, dont chacun spécifie une position dans une dimension de la `ICorDebugArrayValue` objet.  
  
 Cette valeur ne doit pas être null.  
  
 `ppValue`  
 [out] Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur de l’élément spécifié.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
