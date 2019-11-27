---
title: ISymUnmanagedWriter::Initialize, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
ms.openlocfilehash: 6e9ab623d5fe9fcfda2305df078e988a561afdc5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427973"
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize, méthode
Définit l’interface d’émetteur de métadonnées à laquelle ce writer sera associé et définit le nom du fichier de sortie dans lequel les symboles de débogage seront écrits.  
  
 Cette méthode ne peut être appelée qu’une seule fois, et elle doit être appelée avant toute autre méthode d’écriture. Certains enregistreurs peuvent nécessiter un nom de fichier. Toutefois, vous pouvez toujours passer un nom de fichier à cette méthode sans effet négatif sur les writers qui n’utilisent pas le nom de fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a>Paramètres  
 `emitter`  
 dans Pointeur vers l’interface d’émetteur de métadonnées.  
  
 `filename`  
 dans Nom du fichier dans lequel les symboles de débogage sont écrits. Si vous spécifiez un nom de fichier pour un writer qui n'utilise pas les noms de fichiers, ce paramètre est ignoré.  
  
 `pIStream`  
 dans S’il est spécifié, le writer de symbole émet les symboles dans le <xref:System.Runtime.InteropServices.ComTypes.IStream> donné plutôt que dans le fichier spécifié dans le paramètre `filename`. Le paramètre `pIStream` est optionnel.  
  
 `fFullBuild`  
 [in] `true` s’il s’agit d’une régénération complète ; `false` s’il s’agit d’une compilation incrémentielle.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [Initialize2, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
