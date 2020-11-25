---
title: ImportFileEx, méthode
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
ms.openlocfilehash: 9e373f133830a5bc1f3cf7bdc8034cb67725d797
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705200"
---
# <a name="importfileex-method"></a>ImportFileEx, méthode

Importe l’assembly ou le module indépendant indiqué.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  

 `pszFilename`  
 Nom complet du fichier à partir duquel effectuer l’importation.  
  
 `pszTargetName`  
 Nom facultatif du fichier cible.  
  
 `fSmartImport`  
 Si la valeur est TRUE, ImportTypes, est utilisé, sinon l’importation doit être effectuée manuellement.  
  
 `dwOpenFlags`  
 Indicateurs à passer à la [méthode OpenScope](../metadata/imetadatadispenser-openscope-method.md).  
  
 `pImportToken`  
 Reçoit l’ID du fichier en cours d’importation.  
  
 `ppAssemblyScope`  
 Reçoit l’interface de l’interface d’importation d’assembly [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) . A la valeur NULL si le fichier n’est pas un assembly.  
  
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
