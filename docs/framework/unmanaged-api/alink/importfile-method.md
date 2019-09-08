---
title: ImportFile, méthode
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7fee7a91de99e2db69609cbc7c73e22d85d045f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777060"
---
# <a name="importfile-method"></a>ImportFile, méthode
Importe les assemblys et les modules indépendants.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  
 `pszFilename`  
 Nom complet du fichier à importer.  
  
 `pszTargetName`  
 Nom de fichier de sortie facultatif qui peut être utilisé pour renommer le fichier, car il est lié à l’assembly.  
  
 `fSmartImport`  
 Si la valeur est TRUE, ImportTypes, est utilisé, sinon l’importation doit être effectuée manuellement.  
  
 `pImportToken`  
 Pointeur vers le jeton dans lequel un ID de fichier unique sera stocké. Le fichier peut être un assembly ou un fichier.  
  
 `ppAssemblyScope`  
 Reçoit un pointeur vers l' [interface IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md). Peut avoir la valeur NULL si le fichier n’est pas un assembly.  
  
 `pdwCountOfScopes`  
 Pointeur vers le nombre de fichiers et/ou de portées qui ont été importés.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert ALink. h  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
