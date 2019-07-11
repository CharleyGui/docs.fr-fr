---
title: ICorDebugType::EnumerateTypeParameters, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16cf17d43fcad3c4f7a710678bbdc056f840eaca
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736806"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters, méthode
Obtient un pointeur d’interface ICorDebugTypeEnum qui contient le <xref:System.Type> paramètres de la classe référencée par ICorDebugType.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppTyParEnum`  
 [out] Un pointeur vers l’adresse d’un `ICorDebugTypeEnum` qui contient les paramètres du type.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser `EnumerateTypeParameters` si la valeur CorElementType retournée par [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) est ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_ PTR, ou ELEMENT_TYPE_FNPTR. Le nombre de paramètres et leur ordre varie selon le type :  
  
- ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE : Le nombre de paramètres de type contenues dans le `ICorDebugTypeEnum` que cette méthode est retournée, varient selon le nombre de paramètres de type formel pour la classe correspondante. Par exemple, si le type est `class Dict<String,int32>`, puis `EnumerateTypeParameters` retournera un `ICorDebugTypeEnum` qui contient des objets représentant `String` et `int32` dans la séquence.  
  
- ELEMENT_TYPE_FNPTR : Le nombre de paramètres de type contenues dans le `ICorDebugTypeEnum` sera supérieur au nombre d’arguments acceptés par la fonction. Le premier paramètre de type contenu dans le `ICorDebugTypeEnum` est le type de retour pour la fonction, et les paramètres de type suivants sont les paramètres de la fonction.  
  
- ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR : Un paramètre de type est retourné. Par exemple, si le type est un type tableau tel que `int32[]`,`EnumerateTypeParameters` retournera un `ICorDebugTypeEnum` qui contient un objet représentant `int32`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
