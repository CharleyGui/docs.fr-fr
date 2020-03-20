---
title: IMetaDataDispenser::OpenScopeOnMemory, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
ms.openlocfilehash: 492c37540ad68b5b134520218eedc59013c68519
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175926"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a>IMetaDataDispenser::OpenScopeOnMemory, méthode
Ouvre une zone de mémoire qui contient des métadonnées existantes. C’est-à-dire que cette méthode ouvre une zone de mémoire spécifiée dans laquelle les données existantes sont traitées comme des métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pData`  
 [dans] Un pointeur qui spécifie l’adresse de départ de la zone de mémoire.  
  
 `cbData`  
 [dans] La taille de la zone de mémoire, dans les octets.  
  
 `dwOpenFlags`  
 [dans] Une valeur de l’énumération [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) pour spécifier le mode (lire, écrire, etc.) pour l’ouverture.  
  
 `riid`  
 [dans] L’IID de l’interface de métadonnée souhaitée à retourner; l’appelant utilisera l’interface pour importer (lire) ou émettre des métadonnées (écrire).  
  
 La valeur `riid` de doit spécifier l’une des interfaces "importation" ou "émettre". Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [out] Le pointeur de l’interface retournée.  
  
## <a name="remarks"></a>Notes   
 La copie en mémoire des métadonnées peut être demandée à l’aide de méthodes à partir d’une des interfaces « d’importation », ou ajoutée à l’utilisation de méthodes de l’une des interfaces « émettrices ».  
  
 La `OpenScopeOnMemory` méthode est similaire à la méthode [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) méthode, sauf que les métadonnées d’intérêt existe déjà dans la mémoire, plutôt que dans un fichier sur disque.  
  
 Si la zone cible de mémoire ne contient pas de métadonnées courantes (CLR), la `OpenScopeOnMemory` méthode échouera.  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataDispenser, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
