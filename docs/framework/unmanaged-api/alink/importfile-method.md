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
ms.openlocfilehash: f30307884a268008fd4d1a8de31ec5a49b6ab92d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705239"
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
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  

 Requiert ALink. h  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
