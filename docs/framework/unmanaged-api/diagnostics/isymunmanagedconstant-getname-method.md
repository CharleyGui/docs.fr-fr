---
title: ISymUnmanagedConstant::GetName, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
ms.openlocfilehash: 2dd70693528904459a34689dbad944c65c971254
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441641"
---
# <a name="isymunmanagedconstantgetname-method"></a>ISymUnmanagedConstant::GetName, méthode
Obtient le nom de la constante.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cchName`  
 dans Longueur de la mémoire tampon vers laquelle `szName` pointe le paramètre.  
  
 `pcchName`  
 à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le nom, y compris l’arrêt null.  
  
 `szName`  
 à Mémoire tampon qui stocke le nom.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedConstant, interface](isymunmanagedconstant-interface.md)
- [GetSignature, méthode](isymunmanagedconstant-getsignature-method.md)
- [GetValue, méthode](isymunmanagedconstant-getvalue-method.md)
