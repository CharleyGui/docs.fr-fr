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
ms.openlocfilehash: 69e5e05012d2b44a76a986591ec990f66bf8ae20
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007323"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a>IMetaDataDispenser::OpenScopeOnMemory, méthode
Ouvre une zone de mémoire qui contient des métadonnées existantes. Autrement dit, cette méthode ouvre une zone de mémoire spécifiée dans laquelle les données existantes sont traitées en tant que métadonnées.  
  
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
 dans Pointeur qui spécifie l’adresse de début de la zone mémoire.  
  
 `cbData`  
 dans Taille de la zone de mémoire, en octets.  
  
 `dwOpenFlags`  
 dans Valeur de l’énumération [CorOpenFlags](coropenflags-enumeration.md) pour spécifier le mode (lecture, écriture, etc.) à ouvrir.  
  
 `riid`  
 dans IID de l’interface de métadonnées souhaitée à retourner ; l’appelant utilisera l’interface pour importer (Lire) ou émettre (écrire) des métadonnées.  
  
 La valeur de `riid` doit spécifier l’une des interfaces « import » ou « Emit ». Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.  
  
 `ppIUnk`  
 à Pointeur vers l’interface retournée.  
  
## <a name="remarks"></a>Remarques  
 La copie en mémoire des métadonnées peut être interrogée à l’aide de méthodes de l’une des interfaces d’importation ou ajoutée à l’aide de méthodes à partir de l’une des interfaces d’émission.  
  
 La `OpenScopeOnMemory` méthode est semblable à la méthode [IMetaDataDispenser :: OpenScope](imetadatadispenser-openscope-method.md) , sauf que les métadonnées d’intérêt existent déjà en mémoire, plutôt que dans un fichier sur le disque.  
  
 Si la zone cible de la mémoire ne contient pas de métadonnées common language runtime (CLR), la `OpenScopeOnMemory` méthode échoue.  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
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
