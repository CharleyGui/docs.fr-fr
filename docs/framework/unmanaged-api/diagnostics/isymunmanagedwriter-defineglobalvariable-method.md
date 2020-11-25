---
title: ISymUnmanagedWriter::DefineGlobalVariable, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
ms.openlocfilehash: bc389b7247a6b1d6ce16cb3cf350f1672213b2e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716419"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a>ISymUnmanagedWriter::DefineGlobalVariable, méthode

Définit une variable globale unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>Paramètres  

 `name`  
 dans Pointeur vers un `WCHAR` qui définit le nom de la variable globale.  
  
 `attributes`  
 dans Attributs de la variable globale.  
  
 `cSig`  
 dans `ULONG32` Qui indique la taille, en caractères, de la `signature` mémoire tampon.  
  
 `signature`  
 dans Signature de la variable globale.  
  
 `addrKind`  
 dans Type d’adresse.  
  
 `addr1`  
 dans Première adresse de la spécification de paramètre.  
  
 `addr2`  
 dans Deuxième adresse de la spécification de paramètre.  
  
 `addr3`  
 dans Troisième adresse de la spécification de paramètre.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
- [DefineLocalVariable, méthode](isymunmanagedwriter-definelocalvariable-method.md)
- [DefineGlobalVariable2, méthode](isymunmanagedwriter2-defineglobalvariable2-method.md)
