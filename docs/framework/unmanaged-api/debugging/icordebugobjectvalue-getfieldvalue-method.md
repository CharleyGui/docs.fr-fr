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
ms.openlocfilehash: 745be25183f6b94e7a807c4230961d72e2836fe5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695333"
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
 dans `mdFieldDef` Jeton qui fait référence aux métadonnées décrivant le champ.  
  
 `ppValue`  
 à Pointeur vers un objet « ICorDebugValue » qui représente la valeur du champ spécifié.  
  
## <a name="remarks"></a>Remarques  

 La classe, spécifiée dans le `pClass` paramètre, doit se trouver dans la hiérarchie de la classe de la valeur de l’objet, et le champ doit être un champ de cette classe.  
  
 La `GetFieldValue` méthode continuera d’être exécutée pour les objets génériques et les classes génériques. Par exemple, si MyDictionary \<V> hérite du dictionnaire \<string,V> et que la valeur de l’objet est de type MyDictionary \<int32> , la transmission de l' `ICorDebugClass` objet pour le dictionnaire \<K,V> obtiendra avec succès un champ de dictionnaire \<string,int32> .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
