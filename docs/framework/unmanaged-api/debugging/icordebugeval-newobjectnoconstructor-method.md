---
title: ICorDebugEval::NewObjectNoConstructor, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
ms.openlocfilehash: 45efa1939813a319e996a72fef62ada167b877c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788701"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a>ICorDebugEval::NewObjectNoConstructor, méthode
Alloue une nouvelle instance d’objet du type spécifié, sans tenter d’appeler une méthode de constructeur.  
  
 Cette méthode est obsolète dans la version 2,0 de .NET Framework. Utilisez [ICorDebugEval2 :: NewParameterizedObjectNoConstructor,](icordebugeval2-newparameterizedobjectnoconstructor-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pClass`  
 dans Pointeur vers un objet ICorDebugClass qui représente le type d’objet à instancier.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :** 1,1, 1,0  
  
## <a name="see-also"></a>Voir aussi

- [NewParameterizedObjectNoConstructor, méthode](icordebugeval2-newparameterizedobjectnoconstructor-method.md)
