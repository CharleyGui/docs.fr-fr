---
title: ICorDebugArrayValue::GetDimensions, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c0f4836a3dc848b52ee7fe6947f350e6fab787f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737563"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a>ICorDebugArrayValue::GetDimensions, méthode
Obtient le nombre d’éléments dans chaque dimension de ce tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cdim`  
 [in] Le nombre de dimensions de cet objet ICorDebugArrayValue.  
  
 Cette valeur est également la taille de la `dims` tableau car sa taille est égale au nombre de dimensions de la `ICorDebugArrayValue` objet.  
  
 `dims`  
 [out] Tableau d’entiers, chacun d’eux spécifie le nombre d’éléments dans une dimension dans ce `ICorDebugArrayValue` objet.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
