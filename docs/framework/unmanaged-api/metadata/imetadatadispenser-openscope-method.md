---
title: IMetaDataDispenser::OpenScope, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: 5185fb6663910c85ce5dae1225b9b10c5dd8bb28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175939"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope, méthode
Ouvre un fichier existant sur disque et cartographie ses métadonnées en mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szScope`  
 [dans] Le nom du fichier à ouvrir. Le fichier doit contenir des métadonnées courantes (CLR).  
  
 `dwOpenFlags`  
 [dans] Une valeur de l’énumération [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) pour spécifier le mode (lire, écrire, etc.) pour l’ouverture.  
  
 `riid`  
 [dans] L’IID de l’interface de métadonnée souhaitée à retourner; l’appelant utilisera l’interface pour importer (lire) ou émettre des métadonnées (écrire).  
  
 La valeur `riid` de doit spécifier l’une des interfaces "importation" ou "émettre". Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [out] Le pointeur de l’interface retournée.  
  
## <a name="remarks"></a>Notes   
 La copie en mémoire des métadonnées peut être demandée à l’aide de méthodes à partir d’une des interfaces « d’importation », ou ajoutée à l’utilisation de méthodes de l’une des interfaces « émettrices ».  
  
 Si le fichier cible ne contient pas `OpenScope` de métadonnées CLR, la méthode échouera.  
  
 Dans la version cadre .NET 1.0 et la version 1.1, si une portée est ouverte avec `dwOpenFlags` l’ensemble deRead, il est admissible au partage. Autrement dit, si `OpenScope` les appels ultérieurs doivent être transmis au nom d’un fichier qui a été ouvert auparavant, la portée existante est réutilisée et un nouvel ensemble de structures de données n’est pas créé. Cependant, des problèmes peuvent survenir en raison de ce partage.  
  
 Dans la version cadre .NET 2.0, les portées ouvertes avec `dwOpenFlags` set to ofRead ne sont plus partagées. Utilisez la valeur deReadOnly pour permettre de partager la portée. Lorsqu’une portée est partagée, les requêtes qui utilisent des interfaces métadonnées « lire/écrire » échouent.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
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
