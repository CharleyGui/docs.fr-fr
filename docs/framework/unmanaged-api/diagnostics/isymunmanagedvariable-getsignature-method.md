---
title: ISymUnmanagedVariable::GetSignature, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abd4bb00f5c1e703740462f1709407616ac8a8e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778243"
---
# <a name="isymunmanagedvariablegetsignature-method"></a>ISymUnmanagedVariable::GetSignature, méthode
Obtient la signature de cette variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cSig`  
 [in] La longueur de la mémoire tampon vers laquelle pointe le `sig` paramètre.  
  
 `pcSig`  
 [out] Un pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir la signature.  
  
 `sig`  
 [out] La mémoire tampon qui stocke la signature.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedVariable, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
