---
title: EmbedResource, méthode
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
ms.openlocfilehash: 24279870e7406de649df56e8aad31252513e95c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446536"
---
# <a name="embedresource-method"></a>EmbedResource, méthode
Déclare une ressource incorporée. Cette méthode n’incorpore pas réellement la ressource.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID de l’assembly.  
  
 `FileToken`  
 Jeton de fichier ou ID d’assembly du fichier qui contient la ressource.  
  
 `pszResourceName`  
 Nom de la ressource.  
  
 `dwOffset`  
 Décalage de la ressource à partir de RVA.  
  
 `dwFlags`  
 Indicateurs d’accessibilité tels que `mrPublic` et `mrPrivate`. Ces indicateurs peuvent être passés à la [méthode DefineExportedType,](../metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert ALink. h.  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
