---
title: ISymUnmanagedWriter2::DefineGlobalVariable2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineGlobalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a54d3cb1bb9abf740c2c9b5a9a8312a9612ae658
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894455"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a>ISymUnmanagedWriter2::DefineGlobalVariable2, méthode
Définit une variable globale unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>Paramètres  
 `name`  
 dans Nom de la variable globale.  
  
 `attributes`  
 dans Attributs de la variable globale.  
  
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
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter2, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [DefineGlobalVariable, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
