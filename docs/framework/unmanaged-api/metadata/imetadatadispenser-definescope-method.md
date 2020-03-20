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
ms.openlocfilehash: 2f9325f3795262a0c33af02f87fc5d3a020658cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177640"
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope, méthode
Crée une nouvelle zone dans la mémoire dans laquelle vous pouvez créer de nouvelles métadonnées.  
  
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
 [dans] Le CLSID de la version des structures de métadonnées à créer. Cette valeur doit être CLSID_CorMetaDataRuntime pour la version cadre .NET 2.0.  
  
 `dwCreateFlags`  
 [dans] Drapeaux qui spécifient les options. Cette valeur doit être nulle pour le cadre .NET 2.0.  
  
 `riid`  
 [dans] L’IID de l’interface de métadonnée souhaitée à retourner; l’appelant utilisera l’interface pour créer les nouvelles métadonnées.  
  
 La valeur `riid` de doit spécifier l’une des interfaces "emit". Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit ou IID_IMetaDataEmit2.  
  
 `ppIUnk`  
 [out] Le pointeur de l’interface retournée.  
  
## <a name="remarks"></a>Notes   
 `DefineScope`crée un ensemble de tables de métadonnées en mémoire, génère un GUID unique (identificateur de version module, ou MVID) pour les métadonnées, et crée une entrée dans la table du module pour l’unité de compilation émise.  
  
 Vous pouvez attacher des attributs à la portée des métadonnées dans son ensemble en utilisant [l’IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) ou [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) méthode, le cas échéant.  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataDispenser, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
