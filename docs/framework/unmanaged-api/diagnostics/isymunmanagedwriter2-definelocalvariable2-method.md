---
title: ISymUnmanagedWriter2::DefineLocalVariable2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fa385805d3e2dca8fef3e1490b2c67dd0583373
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755070"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2, méthode
Définit une variable unique dans la portée lexicale actuelle. Cette méthode peut être appelée plusieurs fois pour une variable du même nom qui a plusieurs maisons tout au long d’une étendue. Dans ce cas, toutefois, les valeurs de la `startOffset` et `endOffset` paramètres ne doivent pas se chevaucher.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>Paramètres  
 `name`  
 [in] Le nom de variable locale.  
  
 `attributes`  
 [in] Attributs de variable locale.  
  
 `sigToken`  
 [in] Le jeton de métadonnées de la signature.  
  
 `addrKind`  
 [in] Le type d’adresse.  
  
 `addr1`  
 [in] La première adresse de la spécification de paramètre.  
  
 `addr2`  
 [in] La deuxième adresse de la spécification de paramètre.  
  
 `addr3`  
 [in] Troisième adresse de la spécification de paramètre.  
  
 `startOffset`  
 [in] Offset de début pour la variable. Ce paramètre est optionnel. Si la valeur est 0, ce paramètre est ignoré et la variable est définie dans l’ensemble de la portée. Dans le cas d’une valeur différente de zéro, la variable est comprise entre les offsets de la portée actuelle.  
  
 `endOffset`  
 [in] Offset de fin pour la variable. Ce paramètre est optionnel. Si la valeur est 0, ce paramètre est ignoré et la variable est définie dans l’ensemble de la portée. Dans le cas d’une valeur différente de zéro, la variable est comprise entre les offsets de la portée actuelle.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter2, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [DefineLocalVariable, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
