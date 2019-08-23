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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8721f7c30061fbfd4a761bed090b761762c3c13c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939020"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a>ISymUnmanagedReader::ReplaceSymbolStore, méthode
Remplace le magasin de symboles existant par un magasin de symboles delta. Cette méthode est similaire à la méthode [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) , à ceci près que le delta donné agit comme un remplacement complet plutôt qu’une mise à jour.  
  
> [!NOTE]
> Vous devez spécifier un seul des `filename` paramètres ou `pIStream` , mais pas les deux. Si `filename` est spécifié, le magasin de symboles est mis à jour avec les symboles dans ce fichier. Si `pIStream` est spécifié, le magasin est mis à jour avec les données <xref:System.Runtime.InteropServices.ComTypes.IStream>de.  
  
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
 S_OK si la méthode est réussie; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedReader, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
