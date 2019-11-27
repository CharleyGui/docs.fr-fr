---
title: IMetaDataAssemblyEmit::SetExportedTypeProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: ae682c354a7a5188611b103008a3e18f8d821260
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431945"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a>IMetaDataAssemblyEmit::SetExportedTypeProps, méthode
Modifie la structure de métadonnées `ExportedType` spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ct`  
 dans Jeton de métadonnées qui spécifie la structure de métadonnées `ExportedType` à modifier.  
  
 `tkImplementation`  
 dans Jeton, de type `File`, `AssemblyRef`ou `ExportedType`, qui spécifie la façon dont ce type est implémenté.  
  
 `tkTypeDef`  
 dans Jeton `TypeDef` référencé dans le fichier de code.  
  
 `dwExportedTypeFlags`  
 dans Combinaison d’opérations de bits de valeurs qui spécifient des attributs du type.  
  
## <a name="remarks"></a>Notes  
 Pour créer une structure de métadonnées `ExportedType`, utilisez la méthode [IMetaDataAssemblyEmit ::D efineexportedtype](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) .  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
