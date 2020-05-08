---
title: ICorDebugEval::NewObject, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
ms.openlocfilehash: e9570d3c916123093f69e7f26d3778f1c7184b1f
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976185"
---
# <a name="icordebugevalnewobject-method"></a>ICorDebugEval::NewObject, méthode
Alloue une nouvelle instance d’objet et appelle la méthode de constructeur spécifiée.  
  
 Cette méthode est obsolète dans la version 2,0 de .NET Framework. Utilisez [ICorDebugEval2 :: NewParameterizedObject,](icordebugeval2-newparameterizedobject-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pConstructor`  
 dans Constructeur à appeler.  
  
 `nArgs`  
 [in] Taille du tableau `ppArgs`.  
  
 `ppArgs`  
 dans Tableau d’objets ICorDebugValue, chacun représentant un argument à passer au constructeur.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :** 1,1, 1,0  
  
## <a name="see-also"></a>Voir aussi

- [NewParameterizedObject, méthode](icordebugeval2-newparameterizedobject-method.md)
