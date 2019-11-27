---
title: ISymUnmanagedWriter::RemapToken, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
ms.openlocfilehash: 9e441d4ff39632d9381e445ee99249d04539ad87
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427886"
---
# <a name="isymunmanagedwriterremaptoken-method"></a>ISymUnmanagedWriter::RemapToken, méthode
Notifie le writer de symbole qu’un jeton de métadonnées a été remappé à la sortie des métadonnées. Si le writer de symbole a stocké l’ancien jeton dans le magasin de symboles, il doit mettre à jour le jeton stocké avec la nouvelle valeur, ou il doit enregistrer la carte pour que le lecteur de symboles correspondant soit remappé au cours de la phase de lecture.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a>Paramètres  
 `oldToken`  
 dans Jeton de métadonnées qui a été remappé.  
  
 `newToken`  
 dans Nouveau jeton de métadonnées auquel `oldToken` a été remappé.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
