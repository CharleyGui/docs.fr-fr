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
ms.openlocfilehash: cdbb09d25f51e479a8a8ddfc23348305ba7c0a71
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683418"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2, méthode

Définit une variable unique dans la portée lexicale actuelle. Cette méthode peut être appelée plusieurs fois pour une variable du même nom qui a plusieurs maisons dans une étendue. Dans ce cas, toutefois, les valeurs des `startOffset` paramètres et `endOffset` ne doivent pas se chevaucher.  
  
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
 dans Nom de la variable locale.  
  
 `attributes`  
 dans Attributs de la variable locale.  
  
 `sigToken`  
 dans Jeton de métadonnées de la signature.  
  
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
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter2, interface](isymunmanagedwriter2-interface.md)
- [DefineLocalVariable, méthode](isymunmanagedwriter-definelocalvariable-method.md)
