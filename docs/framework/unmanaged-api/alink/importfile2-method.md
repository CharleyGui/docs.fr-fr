---
title: ImportFile2, méthode
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
ms.openlocfilehash: 17f158167d4075783d1aa594fb61cc9e28d30dd7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446986"
---
# <a name="importfile2-method"></a>ImportFile2, méthode
Importe les assemblys et les modules indépendants. Cette méthode est semblable à la [méthode ImportFile](importfile-method.md), mais fonctionne même si le fichier importé n’existe pas sur le disque.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  
 `pszFilename`  
 Nom du fichier à importer.  
  
 `pszTargetName`  
 Nom de fichier de sortie facultatif qui peut être utilisé pour renommer le fichier, car il est lié à l’assembly.  
  
 `pAssemblyScopeIn`  
 Portée facultative, interface d' [interface IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .  
  
 `fSmartImport`  
 Si la valeur est TRUE, ImportTypes, est utilisé, sinon l’importation doit être effectuée manuellement.  
  
 `pImportToken`  
 Reçoit l’ID du fichier ou de l’assembly.  
  
 `ppAssemblyScope`  
 Reçoit l’interface d' [interface IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) . NULL si le fichier n’est pas un assembly.  
  
 `pdwCountOfScopes`  
 Reçoit le trouvé des fichiers et/ou des étendues importés.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert ALink. h.  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
