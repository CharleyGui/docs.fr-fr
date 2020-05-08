---
title: ICorDebugEval2::CreateValueForType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: fd7acaa8bcb4d53893855bcd25ff68cf26e30354
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976159"
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType, méthode
Obtient un pointeur vers un nouveau ICorDebugValue du type spécifié, avec une valeur initiale de zéro ou null.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pType`  
 dans Pointeur vers un objet ICorDebugType qui représente le type.  
  
 `ppValue`  
 à Pointeur vers l’adresse d’un `ICorDebugValue` objet qui représente la valeur.  
  
## <a name="remarks"></a>Notes   
 `CreateValueForType`généralise [ICorDebugEval :: CreateValue](icordebugeval-createvalue-method.md) en vous permettant de spécifier un type d’objet arbitraire, y compris des types `List<int>`construits tels que. Le seul objectif de cette méthode est de générer une valeur qui peut être passée à une évaluation de fonction.  
  
 Le type doit être une classe ou un type valeur. Vous ne pouvez pas utiliser cette méthode pour créer des valeurs de tableau ou des valeurs de chaîne.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
