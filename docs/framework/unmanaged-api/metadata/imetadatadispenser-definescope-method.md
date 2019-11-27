---
title: IMetaDataDispenser::DefineScope, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
ms.openlocfilehash: 381c38542dcde242c0a1a4e71e9b99316328159d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436238"
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope, méthode
Crée une zone en mémoire dans laquelle vous pouvez créer des métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `rclsid`  
 dans CLSID de la version des structures de métadonnées à créer. Cette valeur doit être CLSID_CorMetaDataRuntime pour la version .NET Framework 2,0.  
  
 `dwCreateFlags`  
 dans Indicateurs qui spécifient des options. Cette valeur doit être égale à zéro pour le .NET Framework 2,0.  
  
 `riid`  
 dans IID de l’interface de métadonnées souhaitée à retourner ; l’appelant utilisera l’interface pour créer les nouvelles métadonnées.  
  
 La valeur de `riid` doit spécifier l’une des interfaces d’émission. Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit ou IID_IMetaDataEmit2.  
  
 `ppIUnk`  
 à Pointeur vers l’interface retournée.  
  
## <a name="remarks"></a>Notes  
 `DefineScope` crée un ensemble de tables de métadonnées en mémoire, génère un GUID unique (identificateur de version de module, ou MVID) pour les métadonnées, et crée une entrée dans la table de module pour l’unité de compilation en cours d’émission.  
  
 Vous pouvez attacher des attributs à la portée de métadonnées dans son ensemble à l’aide de la méthode [IMetaDataEmit :: SetModuleProps,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) ou [IMetaDataEmit ::D efinecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) , selon le cas.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataDispenser, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
