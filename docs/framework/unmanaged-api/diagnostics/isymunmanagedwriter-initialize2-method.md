---
title: ISymUnmanagedWriter::Initialize2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
ms.openlocfilehash: 869d7d36ac24bfeee5b2361dd569945ad77eaf7f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610065"
---
# <a name="isymunmanagedwriterinitialize2-method"></a>ISymUnmanagedWriter::Initialize2, méthode
Définit l’interface d’émetteur de métadonnées à laquelle ce writer sera associé et définit le nom du fichier de sortie dans lequel les symboles de débogage seront écrits. Cette méthode vous permet également de définir l’emplacement final du fichier de base de données du programme (PDB).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a>Paramètres  
 `emitter`  
 dans Pointeur vers l’interface d’émetteur de métadonnées.  
  
 `tempfilename`  
 dans Pointeur vers un `WCHAR` qui contient le nom de fichier dans lequel les symboles de débogage sont écrits. Si vous spécifiez un nom de fichier pour un writer qui n'utilise pas les noms de fichiers, ce paramètre est ignoré.  
  
 `pIStream`  
 dans S’il est spécifié, le writer de symbole émet les symboles dans le donné <xref:System.Runtime.InteropServices.ComTypes.IStream> plutôt que dans le fichier spécifié dans le `filename` paramètre. Le paramètre `pIStream` est facultatif.  
  
 `fFullBuild`  
 [in] `true` s’il s’agit d’une régénération complète ; `false`s’il s’agit d’une compilation incrémentielle.  
  
 `finalfilename`  
 dans Pointeur vers `WCHAR` qui est la chaîne de chemin d’accès à l’emplacement final du fichier PDB.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
- [Initialize, méthode](isymunmanagedwriter-initialize-method.md)
