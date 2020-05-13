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
ms.openlocfilehash: dc6bf4f02c49788e640c6e230f864e3ca8e71b0d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380007"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters, méthode
Obtient un pointeur d’interface vers un ICorDebugTypeEnum qui contient les <xref:System.Type> paramètres de la classe référencée par ce ICorDebugType.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppTyParEnum`  
 à Pointeur vers l’adresse d’un `ICorDebugTypeEnum` qui contient les paramètres du type.  
  
## <a name="remarks"></a>Remarks  
 Vous pouvez utiliser `EnumerateTypeParameters` si la valeur CorElementType retournée par [ICorDebugType :: GetType](icordebugtype-gettype-method.md) est ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR ou ELEMENT_TYPE_FNPTR. Le nombre de paramètres et leur ordre dépendent du type :  
  
- ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE : le nombre de paramètres de type contenus dans le `ICorDebugTypeEnum` retourné par cette méthode dépend du nombre de paramètres de type formels pour la classe correspondante. Par exemple, si le type est `class Dict<String,int32>` , `EnumerateTypeParameters` retourne un `ICorDebugTypeEnum` qui contient des objets représentant `String` et `int32` en séquence.  
  
- ELEMENT_TYPE_FNPTR : le nombre de paramètres de type contenus dans le `ICorDebugTypeEnum` sera supérieur au nombre d’arguments accepté par la fonction. Le premier paramètre de type contenu dans `ICorDebugTypeEnum` est le type de retour pour la fonction, et les paramètres de type suivants sont les paramètres de la fonction.  
  
- ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR : un paramètre de type est retourné. Par exemple, si le type est un type tableau tel que `int32[]` , `EnumerateTypeParameters` retourne un `ICorDebugTypeEnum` qui contient un objet représentant `int32` .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
