---
title: ISymUnmanagedReader::UpdateSymbolStore, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
ms.openlocfilehash: ccc787aa1c820a486d9a513055c9c9834b90bd1a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615434"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a>ISymUnmanagedReader::UpdateSymbolStore, méthode
Met à jour le magasin de symboles existant avec un magasin de symboles delta. Cette méthode est utilisée dans les scénarios de modification et de continuation pour mettre à jour le magasin de symboles afin qu’il corresponde aux deltas du fichier exécutable portable (PE) d’origine.  
  
> [!NOTE]
> Vous devez spécifier un seul des `filename` paramètres ou `pIStream` , mais pas les deux. Si `filename` est spécifié, le magasin de symboles est mis à jour avec les symboles dans ce fichier. Si `pIStream` est spécifié, le magasin est mis à jour avec les données de <xref:System.Runtime.InteropServices.ComTypes.IStream> .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a>Paramètres  
 `filename`  
 dans Nom du fichier qui contient le magasin de symboles.  
  
 `pIStream`  
 dans Le flux de fichier, utilisé comme alternative au `filename` paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedReader, interface](isymunmanagedreader-interface.md)
