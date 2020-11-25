---
title: ICorDebugArrayValue::GetElement, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: 0b6b6f46c7fff8f1d4c2ad555c93423f9ca8ac09
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698141"
---
# <a name="icordebugarrayvaluegetelement-method"></a>ICorDebugArrayValue::GetElement, méthode

Obtient la valeur de l’élément de tableau donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `cdim`  
 dans Nombre de dimensions de cet `ICorDebugArrayValue` objet.  
  
 Cette valeur est également la taille du `indices` tableau, car sa taille est égale au nombre de dimensions de l' `ICorDebugArrayValue` objet.  
  
 `indices`  
 dans Tableau de valeurs d’index, chacune spécifiant une position dans une dimension de l' `ICorDebugArrayValue` objet.  
  
 Cette valeur ne doit pas être Null.  
  
 `ppValue`  
 à Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur de l’élément spécifié.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
