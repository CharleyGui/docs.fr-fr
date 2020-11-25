---
title: ISymUnmanagedScope::GetStartOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type:
- apiref
ms.openlocfilehash: 69b72ce66a203f403fcfe0fd4b4e728ece7397e4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725870"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a>ISymUnmanagedScope::GetStartOffset, méthode

Obtient le décalage de début pour cette portée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pRetVal`  
 à Pointeur vers un `ULONG32` qui contient l’offset de départ.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedScope, interface](isymunmanagedscope-interface.md)
- [GetEndOffset, méthode](isymunmanagedscope-getendoffset-method.md)
