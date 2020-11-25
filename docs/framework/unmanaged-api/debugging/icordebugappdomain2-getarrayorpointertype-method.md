---
title: ICorDebugAppDomain2::GetArrayOrPointerType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
ms.openlocfilehash: 8b3f6ae92e39f5385bf29f8b29abbb1726136088
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724765"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType, méthode

Obtient un tableau du type spécifié, ou un pointeur ou une référence au type spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `elementType`  
 dans Valeur de l’énumération CorElementType qui spécifie le type natif sous-jacent (un tableau, un pointeur ou une référence) à créer.  
  
 `nRank`  
 dans Classement (autrement dit, le nombre de dimensions) du tableau. Cette valeur doit être égale à 0 si `elementType` spécifie un type pointeur ou référence.  
  
 `pTypeArg`  
 dans Pointeur vers un objet ICorDebugType qui représente le type de tableau, pointeur ou référence à créer.  
  
 `ppType`  
 à Pointeur vers l’adresse d’un `ICorDebugType` objet qui représente le tableau construit, le type pointeur ou le type référence.  
  
## <a name="remarks"></a>Remarques  

 La valeur de *ElementType* doit être l’une des suivantes :  
  
- ELEMENT_TYPE_PTR  
  
- ELEMENT_TYPE_BYREF  
  
- ELEMENT_TYPE_ARRAY ou ELEMENT_TYPE_SZARRAY  
  
 Si la valeur de *ElementType* est ELEMENT_TYPE_PTR ou ELEMENT_TYPE_BYREF, *nRank* doit être égal à zéro.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
