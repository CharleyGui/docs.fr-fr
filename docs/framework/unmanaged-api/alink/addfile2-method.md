---
title: AddFile2, méthode
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
ms.openlocfilehash: cff6707496c7d9657796deb8bf6fa9165ff295a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717082"
---
# <a name="addfile2-method"></a>AddFile2, méthode

Ajoute des fichiers à l’assembly. Peut également être utilisé pour créer des modules indépendants.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  

 `AssemblyID`  
 ID de l’assembly auquel le fichier est ajouté.  
  
 `pszFilename`  
 Nom du fichier à ajouter.  
  
 `dwFlags`  
 `FileDef`Indicateurs com+ tels que `ffContainsNoMetaData` et `ffWriteable` . `dwFlags` est passé à la [méthode DefineFile](../metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pEmitter`  
 Interface de l’interface de l' [interface IMetaDataEmit2](../metadata/imetadataemit2-interface.md) .  
  
 `pFileToken`  
 Reçoit l’ID du fichier en cours d’ajout.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  

 Requiert ALink. h.  
  
## <a name="see-also"></a>Voir aussi

- [IALink2, interface](ialink2-interface.md)
- [IALink, interface](ialink-interface.md)
- [API ALink](index.md)
