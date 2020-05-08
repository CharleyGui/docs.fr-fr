---
title: ICorDebugEval::CreateValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
ms.openlocfilehash: 55888786fdd8ff2b1d5610a74ee729db0d4fcfde
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976250"
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue, méthode
Crée une valeur du type spécifié, avec une valeur initiale de zéro ou null.  
  
 Cette méthode est obsolète dans la version 2,0 de .NET Framework. Utilisez [ICorDebugEval2 :: CreateValueForType,](icordebugeval2-createvaluefortype-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `elementType`  
 dans Valeur de l’énumération [CorElementType](../metadata/corelementtype-enumeration.md) qui spécifie le type de la valeur.  
  
 `pElementClass`  
 dans Pointeur vers un objet [ICorDebugClass](icordebugclass-interface.md) qui spécifie la classe de la valeur, si le type n’est pas un type primitif.  
  
 `ppValue`  
 à Pointeur vers l’adresse d’un objet « ICorDebugValue » qui représente la valeur.  
  
## <a name="remarks"></a>Notes   
 `CreateValue`crée un `ICorDebugValue` objet du type donné dans le seul but de l’utiliser dans une évaluation de fonction. Cet objet de valeur peut être utilisé pour passer des constantes utilisateur en tant que paramètres.  
  
 Si le type de la valeur est un type primitif, sa valeur initiale est zéro ou null. Utilisez [ICorDebugGenericValue :: SetValue](icordebuggenericvalue-setvalue-method.md) pour définir la valeur d’un type primitif.  
  
 Si la valeur de `elementType` est ELEMENT_TYPE_CLASS, vous recevez un « ICorDebugReferenceValue » (retourné dans `ppValue`) représentant la référence d’objet null. Vous pouvez utiliser cet objet pour passer NULL à une évaluation de fonction qui a des paramètres de référence d’objet. Vous ne pouvez pas `ICorDebugValue` définir sur n’importe quoi ; elle conserve toujours la valeur null.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :** 1,1, 1,0  
  
## <a name="see-also"></a>Voir aussi

- [CreateValueForType, méthode](icordebugeval2-createvaluefortype-method.md)
- [ICorDebugEval, interface](icordebugeval-interface.md)
