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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9597d05e46c2d41ab1f24a073c028561e944fb59
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753031"
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray, méthode
Alloue un nouveau tableau du type d’élément spécifié et des dimensions.  
  
 Cette méthode est obsolète dans le .NET Framework version 2.0. Utilisez [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) à la place.  
  
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
  
## <a name="parameters"></a>Paramètres  
 `elementType`  
 [in] Une valeur de l’énumération CorElementType qui spécifie le type d’élément du tableau.  
  
 `pElementClass`  
 [in] Pointeur vers un objet ICorDebugClass qui spécifie la classe de l’élément. Cette valeur peut être null si le type d’élément est un type primitif.  
  
 `rank`  
 [in] Le nombre de dimensions du tableau. Dans le .NET Framework 2.0, cette valeur doit être 1.  
  
 `dims`  
 [in] La taille, en octets, de chaque dimension du tableau.  
  
 `lowBounds`  
 [in] Facultatif. La limite inférieure de chaque dimension du tableau. Si cette valeur est omise, une limite inférieure de zéro est prise en compte pour chaque dimension.  
  
## <a name="remarks"></a>Notes  
 Le tableau est toujours créé dans le domaine d’application dans lequel le thread est en cours d’exécution.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** 1.1, 1.0
