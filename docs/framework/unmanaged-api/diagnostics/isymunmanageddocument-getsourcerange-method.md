---
title: ISymUnmanagedDocument::GetSourceRange, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
ms.openlocfilehash: 841379702e24428a8092cfd1d2cbd3c5b4e17ba4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615603"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>ISymUnmanagedDocument::GetSourceRange, méthode
Retourne la plage spécifiée de la source incorporée dans la mémoire tampon donnée. La mémoire tampon doit être suffisamment grande pour contenir la source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `startLine`  
 dans Ligne de début dans le document actif.  
  
 `startColumn`  
 dans Colonne de début dans le document actif.  
  
 `endLine`  
 dans Dernière ligne dans le document actif.  
  
 `endColumn`  
 dans Dernière colonne dans le document actif.  
  
 `cSourceBytes`  
 dans Taille de la source, en octets.  
  
 `pcSourceBytes`  
 à Pointeur vers une variable qui reçoit la taille de la source.  
  
 `source`  
 à Taille et longueur de la plage spécifiée du document source, en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie.  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedDocument, interface](isymunmanageddocument-interface.md)
