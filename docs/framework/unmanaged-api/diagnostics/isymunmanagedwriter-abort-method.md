---
title: ISymUnmanagedWriter::Abort, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
ms.openlocfilehash: 6074ec5248d27b1405d2367349904f6630df951b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445997"
---
# <a name="isymunmanagedwriterabort-method"></a>ISymUnmanagedWriter::Abort, méthode
Ferme le writer de symbole sans valider les symboles dans le magasin de symboles. Après cet appel, l’enregistreur de symboles devient non valide pour les mises à jour ultérieures. Pour valider les symboles et fermer le writer de symbole, utilisez la méthode [ISymUnmanagedWriter :: Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
