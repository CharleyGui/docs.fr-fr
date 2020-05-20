---
title: ISymUnmanagedWriter::DefineLocalVariable, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
ms.openlocfilehash: 5730cdd910257d762230f5e54576d5e0a7ac1adb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614823"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable, méthode
Définit une variable unique dans la portée lexicale actuelle. Cette méthode peut être appelée plusieurs fois pour une variable du même nom qui a plusieurs maisons dans une étendue. Dans ce cas, toutefois, les valeurs des `startOffset` paramètres et `endOffset` ne doivent pas se chevaucher.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>Paramètres  
 `name`  
 dans Pointeur vers un `WCHAR` qui définit le nom de la variable locale.  
  
 `attributes`  
 dans Attributs de la variable locale.  
  
 `cSig`  
 dans `ULONG32`Qui indique la taille, en octets, de la `signature` mémoire tampon.  
  
 `signature`  
 dans Signature de la variable locale.  
  
 `addrKind`  
 dans Type d’adresse.  
  
 `addr1`  
 dans Première adresse de la spécification de paramètre.  
  
 `addr2`  
 dans Deuxième adresse de la spécification de paramètre.  
  
 `addr3`  
 dans Troisième adresse de la spécification de paramètre.  
  
 `startOffset`  
 dans Décalage de début de la variable. Ce paramètre est facultatif. Si la valeur est égale à 0, ce paramètre est ignoré et la variable est définie dans l’ensemble de la portée. S’il s’agit d’une valeur différente de zéro, la variable est comprise entre les offsets de la portée actuelle.  
  
 `endOffset`  
 dans Offset de fin de la variable. Ce paramètre est facultatif. Si la valeur est égale à 0, ce paramètre est ignoré et la variable est définie dans l’ensemble de la portée. S’il s’agit d’une valeur différente de zéro, la variable est comprise entre les offsets de la portée actuelle.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
- [DefineGlobalVariable, méthode](isymunmanagedwriter-defineglobalvariable-method.md)
- [DefineLocalVariable2, méthode](isymunmanagedwriter2-definelocalvariable2-method.md)
