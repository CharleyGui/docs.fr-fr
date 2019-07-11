---
title: ISymUnmanagedReader::GetNamespaces, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e0c72cd6e7dce784064f7653ba35e488061d9fd7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773581"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a>ISymUnmanagedReader::GetNamespaces, méthode
Obtient les espaces de noms définis dans une portée globale dans ce magasin de symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cNameSpaces`  
 [in] La taille du tableau d’espaces de noms.  
  
 `pcNameSpaces`  
 [out] Pointeur vers une variable qui reçoit la longueur de la liste de l’espace de noms.  
  
 `namespaces`  
 [out] Pointeur vers une variable qui reçoit la liste de l’espace de noms.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedReader, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
