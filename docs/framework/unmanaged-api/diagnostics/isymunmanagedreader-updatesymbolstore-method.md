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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d84d4fccb2cb4e500f07f6bfbfb93b8c7b81f5d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939004"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a>ISymUnmanagedReader::UpdateSymbolStore, méthode
Met à jour le magasin de symboles existant avec un magasin de symboles delta. Cette méthode est utilisée dans les scénarios de modification et de continuation pour mettre à jour le magasin de symboles afin qu’il corresponde aux deltas du fichier exécutable portable (PE) d’origine.  
  
> [!NOTE]
> Vous devez spécifier un seul des `filename` paramètres ou `pIStream` , mais pas les deux. Si `filename` est spécifié, le magasin de symboles est mis à jour avec les symboles dans ce fichier. Si `pIStream` est spécifié, le magasin est mis à jour avec les données <xref:System.Runtime.InteropServices.ComTypes.IStream>de.  
  
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
 S_OK si la méthode est réussie; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedReader, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
