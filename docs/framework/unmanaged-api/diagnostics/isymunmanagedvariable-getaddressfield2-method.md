---
title: ISymUnmanagedVariable::GetAddressField2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type:
- apiref
ms.openlocfilehash: 858341d5b8b1b3ecbe9dd5bd39a38f9cfd0d08dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714170"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a>ISymUnmanagedVariable::GetAddressField2, méthode

Obtient le deuxième champ d’adresse pour cette variable. Sa signification dépend du type d’adresse.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pRetVal`  
 à Pointeur vers un `ULONG32` qui reçoit le deuxième champ d’adresse.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedVariable, interface](isymunmanagedvariable-interface.md)
- [GetAddressField1, méthode](isymunmanagedvariable-getaddressfield1-method.md)
- [GetAddressField3, méthode](isymunmanagedvariable-getaddressfield3-method.md)
- [GetAddressKind, méthode](isymunmanagedvariable-getaddresskind-method.md)
