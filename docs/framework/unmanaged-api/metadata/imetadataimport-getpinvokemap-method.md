---
title: IMetaDataImport::GetPinvokeMap, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
ms.openlocfilehash: 8409e56b5ec4dbe47035a0555b6b7ce175b517ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490976"
---
# <a name="imetadataimportgetpinvokemap-method"></a>IMetaDataImport::GetPinvokeMap, méthode
Obtient un jeton ModuleRef pour représenter l'assembly cible d'un appel PInvoke.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `tk`  
 dans Jeton FieldDef ou MethodDef pour lequel obtenir les métadonnées de mappage PInvoke.  
  
 `pdwMappingFlags`  
 à Pointeur vers les indicateurs utilisés pour le mappage. Cette valeur est un masque de masque de l’énumération [CorPinvokeMap,](corpinvokemap-enumeration.md) .  
  
 `szImportName`  
 à Nom de la DLL cible non managée.  
  
 `cchImportName`  
 dans Taille en caractères larges de `szImportName` .  
  
 `pchImportName`  
 à Nombre de caractères larges retournés dans `szImportName` .  
  
 `pmrImportDLL`  
 à Pointeur vers un jeton ModuleRef qui représente la bibliothèque d’objets cibles non managée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
