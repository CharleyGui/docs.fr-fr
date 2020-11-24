---
title: ISymUnmanagedWriter::SetMethodSourceRange, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
ms.openlocfilehash: a918b5c2334683348adc6a7382527faedb52d7b6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683535"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a>ISymUnmanagedWriter::SetMethodSourceRange, méthode

Spécifie les véritables début et fin d'une méthode dans un fichier source. Utilisez cette méthode pour spécifier l’étendue d’une méthode indépendamment des points de séquence qui existent dans la méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a>Paramètres  

 `startDoc`  
 dans Pointeur vers le document contenant la position de départ.  
  
 `startLine`  
 dans Numéro de la ligne de départ.  
  
 `startColumn`  
 dans Colonne de départ.  
  
 `endDoc`  
 dans Pointeur vers le document contenant la position de fin.  
  
 `endLine`  
 dans Numéro de la ligne de fin.  
  
 `endColumn`  
 dans Numéro de la colonne de fin.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
