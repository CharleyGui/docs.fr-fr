---
title: ISymUnmanagedWriter::DefineField, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
ms.openlocfilehash: 5683c10938873821cbe998dbf13937a6a7d24d7c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675085"
---
# <a name="isymunmanagedwriterdefinefield-method"></a>ISymUnmanagedWriter::DefineField, méthode

Définit une variable unique qui ne se trouve pas dans une méthode. Cette méthode est utilisée pour certains champs dans les classes, les champs de bits, etc.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
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

 `parent`  
 dans Le type de métadonnées ou le jeton de méthode.  
  
 `name`  
 dans Nom du champ.  
  
 `attributes`  
 dans Attributs du champ.  
  
 `cSig`  
 dans `ULONG32` Qui est la taille, en caractères, de la mémoire tampon requise pour contenir la signature de champ.  
  
 `signature`  
 dans Tableau de signatures de champs.  
  
 `addrKind`  
 dans Type d’adresse.  
  
 `addr1`  
 dans Première adresse de la spécification de champ.  
  
 `addr2`  
 dans Deuxième adresse de la spécification de champ.  
  
 `addr3`  
 dans Troisième adresse de la spécification de champ.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
