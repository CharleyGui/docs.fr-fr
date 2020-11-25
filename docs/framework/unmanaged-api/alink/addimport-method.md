---
title: AddImport, méthode
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
ms.openlocfilehash: cf73ada36be66edb3fa267d61873ae9acb088a34
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717043"
---
# <a name="addimport-method"></a>AddImport, méthode

Ajoute des importations à l’assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  

 `AssemblyID`  
 ID unique de l’assembly à augmenter.  
  
 `ImportToken`  
 ID unique, récupéré à partir de la [méthode ImportFile](importfile-method.md), du fichier à importer.  
  
 `dwFlags`  
 Indicateurs FileDef COM+ tels que `ffContainsNoMetaData` et `ffWriteable` . `dwFlags` est passé à la [méthode DefineFile](../metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pFileToken`  
 Pointeur vers le jeton qui reçoit l’ID du fichier résultant.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  

 Requiert ALink. h  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
