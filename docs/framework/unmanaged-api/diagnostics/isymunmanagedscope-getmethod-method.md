---
title: ISymUnmanagedScope::GetMethod, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
ms.openlocfilehash: 75d5638a6f01ba9569a03e5255a7217371c9d177
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725935"
---
# <a name="isymunmanagedscopegetmethod-method"></a>ISymUnmanagedScope::GetMethod, méthode

Obtient la méthode qui contient cette portée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pRetVal`  
 à Pointeur vers l’interface [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) retournée.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedScope, interface](isymunmanagedscope-interface.md)
