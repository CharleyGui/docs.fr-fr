---
title: ICorDebugObjectValue::GetFieldValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
ms.openlocfilehash: 660bc13e8109994f59444c0adebbc97f54de0b43
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207595"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue, méthode
Obtient la valeur du champ spécifié de la classe spécifiée pour cette valeur d’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pClass`  
 dans Pointeur vers un objet « ICorDebugClass » qui représente la classe pour laquelle obtenir la valeur de champ.  
  
 `fieldDef`  
 dans `mdFieldDef`Jeton qui fait référence aux métadonnées décrivant le champ.  
  
 `ppValue`  
 à Pointeur vers un objet « ICorDebugValue » qui représente la valeur du champ spécifié.  
  
## <a name="remarks"></a>Remarks  
 La classe, spécifiée dans le `pClass` paramètre, doit se trouver dans la hiérarchie de la classe de la valeur de l’objet, et le champ doit être un champ de cette classe.  
  
 La `GetFieldValue` méthode continuera d’être exécutée pour les objets génériques et les classes génériques. Par exemple, si MyDictionary \< v> hérite de \< la chaîne de dictionnaire, v> et que la valeur de l’objet est de type MyDictionary \< Int32>, passant l' `ICorDebugClass` objet pour le dictionnaire \< K, v> obtiendra avec succès un champ de chaîne de dictionnaire \< , Int32>.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
