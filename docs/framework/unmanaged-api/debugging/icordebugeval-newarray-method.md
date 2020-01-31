---
title: ICorDebugEval::NewArray, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
ms.openlocfilehash: 13ac5379992f4e768b09a03d31591143ba9bf627
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788722"
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray, méthode
Alloue un nouveau tableau du type d’élément et des dimensions spécifiés.  
  
 Cette méthode est obsolète dans la version 2,0 de .NET Framework. Utilisez [ICorDebugEval2 :: NewParameterizedArray,](icordebugeval2-newparameterizedarray-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `elementType`  
 dans Valeur de l’énumération CorElementType qui spécifie le type d’élément du tableau.  
  
 `pElementClass`  
 dans Pointeur vers un objet ICorDebugClass qui spécifie la classe de l’élément. Cette valeur peut être null si le type d’élément est un type primitif.  
  
 `rank`  
 dans Nombre de dimensions du tableau. Dans le .NET Framework 2,0, cette valeur doit être 1.  
  
 `dims`  
 dans Taille, en octets, de chaque dimension du tableau.  
  
 `lowBounds`  
 [in] Facultatif. Limite inférieure de chaque dimension du tableau. Si cette valeur est omise, une limite inférieure de zéro est utilisée pour chaque dimension.  
  
## <a name="remarks"></a>Notes  
 Le tableau est toujours créé dans le domaine d’application dans lequel le thread est en cours d’exécution.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :** 1,1, 1,0
