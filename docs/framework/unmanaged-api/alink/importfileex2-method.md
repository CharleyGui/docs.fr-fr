---
title: ImportFileEx2, méthode
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
ms.openlocfilehash: 59149e79e926a0b9a3e549e013bf178e54ddf6fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705174"
---
# <a name="importfileex2-method"></a>ImportFileEx2, méthode

Importe les assemblys et les modules indépendants. Cette méthode est semblable à la [méthode ImportFile](importfile-method.md), mais fonctionne même si le fichier importé n’existe pas sur le disque.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  

 `pszFilename`  
 Nom du fichier à importer.  
  
 `pszTargetName`  
 Nom facultatif du fichier cible.  
  
 `pAssemblyScopeIn`  
 Option de l’interface de l’interface [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) facultative.  
  
 `fSmartImport`  
 Si la valeur est TRUE, ImportTypes, est utilisé, sinon l’importation doit être effectuée manuellement.  
  
 `dwOpenFlags`  
 Indicateurs à passer à la [méthode OpenScope](../metadata/imetadatadispenser-openscope-method.md).  
  
 `pImportToken`  
 Reçoit l’ID unique de l’assembly ou du fichier.  
  
 `ppAssemblyScope`  
 Reçoit l’interface de l’interface d’importation d’assembly [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) . Peut avoir la valeur NULL si le fichier n’est pas un assembly.  
  
 `pdwCountOfScopes`  
 Reçoit le nombre de fichiers et/ou d’étendues importés.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  

 Requiert ALink. h.  
  
## <a name="see-also"></a>Voir aussi

- [IALink2, interface](ialink2-interface.md)
- [IALink, interface](ialink-interface.md)
- [API ALink](index.md)
