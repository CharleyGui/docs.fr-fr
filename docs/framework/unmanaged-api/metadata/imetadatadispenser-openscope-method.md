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
ms.openlocfilehash: f2a85bafc3e2f25b2ed6116a46a9938d869dbaae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726078"
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
 dans Valeur de l’énumération [CorOpenFlags](coropenflags-enumeration.md) pour spécifier le mode (lecture, écriture, etc.) à ouvrir.  
  
 `riid`  
 dans IID de l’interface de métadonnées souhaitée à retourner ; l’appelant utilisera l’interface pour importer (Lire) ou émettre (écrire) des métadonnées.  
  
 La valeur de `riid` doit spécifier l’une des interfaces « import » ou « Emit ». Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.  
  
 `ppIUnk`  
 à Pointeur vers l’interface retournée.  
  
## <a name="remarks"></a>Remarques  

 La copie en mémoire des métadonnées peut être interrogée à l’aide de méthodes de l’une des interfaces d’importation ou ajoutée à l’aide de méthodes à partir de l’une des interfaces d’émission.  
  
 Si le fichier cible ne contient pas de métadonnées CLR, la `OpenScope` méthode échoue.  
  
 Dans le .NET Framework version 1,0 et la version 1,1, si une étendue est ouverte avec la `dwOpenFlags` valeur ofRead, elle est éligible au partage. Autrement dit, si des appels suivants sont `OpenScope` passés au nom d’un fichier qui a été ouvert précédemment, l’étendue existante est réutilisée et un nouvel ensemble de structures de données n’est pas créé. Toutefois, des problèmes peuvent survenir en raison de ce partage.  
  
 Dans la version de .NET Framework 2,0, les étendues ouvertes avec `dwOpenFlags` définies sur ofRead ne sont plus partagées. Utilisez la valeur ofReadOnly pour autoriser le partage de l’étendue. Lorsqu’une étendue est partagée, les requêtes qui utilisent des interfaces de métadonnées en lecture/écriture échouent.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataDispenser, interface](imetadatadispenser-interface.md)
- [IMetaDataDispenserEx, interface](imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit, interface](imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport, interface](imetadataassemblyimport-interface.md)
- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
