---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
ms.openlocfilehash: 770a9280d27c84b950e00e71328c9b28e61c9e7c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084808"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a>ICorDebugEval2::NewParameterizedObjectNoConstructor, méthode
Instancie un nouvel objet de type paramétrable de la classe spécifiée sans tenter d’appeler une méthode de constructeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pClass`  
 dans Pointeur vers un objet ICorDebugClass qui représente la classe de l’objet à instancier.  
  
 `nTypeArgs`  
 dans Nombre d’arguments de type passés.  
  
 `ppTypeArgs`  
 dans Tableau de pointeurs, chacun pointant vers un objet ICorDebugType qui représente un argument de type pour l’objet en cours d’instanciation.  
  
## <a name="remarks"></a>Notes  
 La méthode `NewParameterizedObjectNoConstructor` échoue si un nombre incorrect d’arguments de type ou les types d’arguments de type incorrects sont passés.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
