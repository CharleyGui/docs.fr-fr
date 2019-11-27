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
ms.openlocfilehash: 5ce1af82631531f8f7105fbf92ba78db3cca437b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442329"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope, méthode
Ouvre un fichier sur disque existant et mappe ses métadonnées en mémoire.  
  
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
 dans Nom du fichier à ouvrir. Le fichier doit contenir des métadonnées common language runtime (CLR).  
  
 `dwOpenFlags`  
 dans Valeur de l’énumération [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) pour spécifier le mode (lecture, écriture, etc.) à ouvrir.  
  
 `riid`  
 dans IID de l’interface de métadonnées souhaitée à retourner ; l’appelant utilisera l’interface pour importer (Lire) ou émettre (écrire) des métadonnées.  
  
 La valeur de `riid` doit spécifier l’une des interfaces « import » ou « Emit ». Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.  
  
 `ppIUnk`  
 à Pointeur vers l’interface retournée.  
  
## <a name="remarks"></a>Notes  
 La copie en mémoire des métadonnées peut être interrogée à l’aide de méthodes de l’une des interfaces d’importation ou ajoutée à l’aide de méthodes à partir de l’une des interfaces d’émission.  
  
 Si le fichier cible ne contient pas de métadonnées CLR, la méthode `OpenScope` échoue.  
  
 Dans .NET Framework les versions 1,0 et 1,1, si une étendue est ouverte avec `dwOpenFlags` définie sur ofRead, elle est éligible au partage. Autrement dit, si des appels suivants à `OpenScope` passer le nom d’un fichier qui a été ouvert précédemment, l’étendue existante est réutilisée et un nouvel ensemble de structures de données n’est pas créé. Toutefois, des problèmes peuvent survenir en raison de ce partage.  
  
 Dans la version .NET Framework 2,0, les étendues ouvertes avec `dwOpenFlags` définies sur ofRead ne sont plus partagées. Utilisez la valeur ofReadOnly pour autoriser le partage de l’étendue. Lorsqu’une étendue est partagée, les requêtes qui utilisent des interfaces de métadonnées en lecture/écriture échouent.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataDispenser, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
