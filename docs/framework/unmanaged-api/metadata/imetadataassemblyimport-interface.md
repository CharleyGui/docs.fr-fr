---
title: IMetaDataAssemblyImport, interface
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
ms.openlocfilehash: 289e26868ff2eb9e1d97cf084e9a888815062ea4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436305"
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport, interface
Fournit des méthodes pour accéder au contenu d'un manifeste d'assembly et l'examiner.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CloseEnum, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|Libère le handle de l’énumérateur spécifié.|  
|[EnumAssemblyRefs, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|Obtient un pointeur d’interface vers un énumérateur qui contient les `mdAssemblyRef` jetons des assemblys référencés par l’assembly dans la portée de métadonnées actuelle.|  
|[EnumExportedTypes, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|Obtient un pointeur d’interface vers un énumérateur qui contient les `mdExportedType` jetons des types COM référencés par l’assembly dans la portée de métadonnées actuelle.|  
|[EnumFiles, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|Obtient un pointeur d’interface vers un énumérateur qui contient les `mdFile` jetons des fichiers référencés par l’assembly dans la portée de métadonnées actuelle.|  
|[EnumManifestResources, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|Obtient un pointeur d’interface vers un énumérateur qui contient les `mdManifestResource` jetons des ressources référencées par l’assembly dans la portée de métadonnées actuelle.|  
|[FindAssembliesByName, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|Obtient un tableau de `mdAssemblyRef` jetons pour les assemblys portant le nom spécifié.|  
|[FindExportedTypeByName, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|Obtient un jeton de `mdExportedType` pour le type COM portant le nom spécifié.|  
|[FindManifestResourceByName, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|Obtient un jeton de `mdManifestResource` pour la ressource avec le nom spécifié.|  
|[GetAssemblyFromScope, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|Obtient le jeton de l’assembly dans la portée de métadonnées actuelle.|  
|[GetAssemblyProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|Obtient les paramètres de propriété de l’assembly spécifié.|  
|[GetAssemblyRefProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|Obtient les paramètres de propriété du jeton de `mdAssemblyRef` spécifié.|  
|[GetExportedTypeProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|Obtient les paramètres de propriété du type COM spécifié.|  
|[GetFileProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|Obtient les paramètres de propriété du fichier spécifié.|  
|[GetManifestResourceProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|Obtient les paramètres de propriété de la ressource de manifeste spécifiée.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
