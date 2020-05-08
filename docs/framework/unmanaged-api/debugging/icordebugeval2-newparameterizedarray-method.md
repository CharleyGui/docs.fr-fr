---
title: ICorDebugEval2::NewParameterizedArray, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
ms.openlocfilehash: 9d589bfc3093d03d87acb47ade0fc6c972bcd335
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976107"
---
# <a name="icordebugeval2newparameterizedarray-method"></a>ICorDebugEval2::NewParameterizedArray, méthode
Alloue un nouveau tableau du type d’élément et des dimensions spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pElementType`  
 dans Pointeur vers un objet ICorDebugType qui représente le type d’élément stocké dans le tableau.  
  
 `rank`  
 dans Nombre de dimensions du tableau. Dans le .NET Framework version 2,0, cette valeur doit être 1.  
  
 `dims`  
 dans Taille, en octets, de chaque dimension du tableau.  
  
 `lowBounds`  
 [in] Facultatif. Limite inférieure de chaque dimension du tableau. Si cette valeur est omise, une limite inférieure de zéro est utilisée pour chaque dimension.  
  
## <a name="remarks"></a>Notes   
 Les éléments du tableau peuvent être des instances d’un type générique. Le tableau est toujours créé dans le domaine d’application dans lequel le thread est en cours d’exécution. Dans la .NET Framework 2,0, la valeur de `rank` doit être 1.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
