---
title: ISymUnmanagedReader::ReplaceSymbolStore, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
ms.openlocfilehash: db2137146ded5200e05bbf88e23ae599f3eb7dec
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615447"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a>ISymUnmanagedReader::ReplaceSymbolStore, méthode
Remplace le magasin de symboles existant par un magasin de symboles delta. Cette méthode est similaire à la méthode [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) , à ceci près que le delta donné agit comme un remplacement complet plutôt qu’une mise à jour.  
  
> [!NOTE]
> Vous devez spécifier un seul des `filename` paramètres ou `pIStream` , mais pas les deux. Si `filename` est spécifié, le magasin de symboles est mis à jour avec les symboles dans ce fichier. Si `pIStream` est spécifié, le magasin est mis à jour avec les données de <xref:System.Runtime.InteropServices.ComTypes.IStream> .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a>Paramètres  
 `filename`  
 dans Nom du fichier contenant le magasin de symboles.  
  
 `pIStream`  
 dans Le flux de fichier, utilisé comme alternative au `filename` paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedReader, interface](isymunmanagedreader-interface.md)
