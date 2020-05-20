---
title: ISymUnmanagedWriter::Close, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
ms.openlocfilehash: 0a7ecd475a8031fedb2c8474593b45045fcc6fb9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610130"
---
# <a name="isymunmanagedwriterclose-method"></a>ISymUnmanagedWriter::Close, méthode
Ferme le writer de symbole après avoir validé les symboles dans le magasin de symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Après cet appel, l’enregistreur de symboles devient non valide pour les mises à jour ultérieures. Pour fermer le writer de symbole sans valider les symboles, utilisez la méthode [ISymUnmanagedWriter :: Abort](isymunmanagedwriter-abort-method.md) à la place.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
