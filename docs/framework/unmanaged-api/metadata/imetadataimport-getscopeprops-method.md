---
title: IMetaDataImport::GetScopeProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
ms.openlocfilehash: af1c3d599c5280e584ffb842c96c70a7c3d4ed08
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436879"
---
# <a name="imetadataimportgetscopeprops-method"></a>IMetaDataImport::GetScopeProps, méthode
Obtient le nom et éventuellement l'identificateur de version de l'assembly ou du module dans la portée de métadonnées actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szName`  
 à Mémoire tampon pour le nom de l’assembly ou du module.  
  
 `cchName`  
 dans Taille en caractères larges de `szName`.  
  
 `pchName`  
 à Nombre de caractères larges retournés dans `szName`.  
  
 `pmvid`  
 [out, optional] Pointeur vers un GUID qui identifie de façon unique la version de l’assembly ou du module.  
  
## <a name="remarks"></a>Notes  
 La méthode [IMetaDataEmit :: SetModuleProps,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) est utilisée pour définir ces propriétés.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
