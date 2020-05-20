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
ms.openlocfilehash: 6256d052780b1c610e61267be2517954d722a42d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610598"
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
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedVariable, interface](isymunmanagedvariable-interface.md)
- [GetAddressField1, méthode](isymunmanagedvariable-getaddressfield1-method.md)
- [GetAddressField3, méthode](isymunmanagedvariable-getaddressfield3-method.md)
- [GetAddressKind, méthode](isymunmanagedvariable-getaddresskind-method.md)
