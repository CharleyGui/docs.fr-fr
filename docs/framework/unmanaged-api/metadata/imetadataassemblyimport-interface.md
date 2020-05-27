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
ms.openlocfilehash: 2a67f50fa1042e8d3957a9a0394507f260a328c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009013"
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport, interface
Fournit des méthodes pour accéder au contenu d'un manifeste d'assembly et l'examiner.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CloseEnum, méthode](imetadataassemblyimport-closeenum-method.md)|Libère le handle de l’énumérateur spécifié.|  
|[EnumAssemblyRefs, méthode](imetadataassemblyimport-enumassemblyrefs-method.md)|Obtient un pointeur d’interface vers un énumérateur qui contient les `mdAssemblyRef` jetons des assemblys référencés par l’assembly dans la portée de métadonnées actuelle.|  
|[EnumExportedTypes, méthode](imetadataassemblyimport-enumexportedtypes-method.md)|Obtient un pointeur d’interface vers un énumérateur qui contient les `mdExportedType` jetons des types com référencés par l’assembly dans la portée de métadonnées actuelle.|  
|[EnumFiles, méthode](imetadataassemblyimport-enumfiles-method.md)|Obtient un pointeur d’interface vers un énumérateur qui contient les `mdFile` jetons des fichiers référencés par l’assembly dans la portée de métadonnées actuelle.|  
|[EnumManifestResources, méthode](imetadataassemblyimport-enummanifestresources-method.md)|Obtient un pointeur d’interface vers un énumérateur qui contient les `mdManifestResource` jetons des ressources référencées par l’assembly dans la portée de métadonnées actuelle.|  
|[FindAssembliesByName, méthode](imetadataassemblyimport-findassembliesbyname-method.md)|Obtient un tableau de `mdAssemblyRef` jetons pour les assemblys avec le nom spécifié.|  
|[FindExportedTypeByName, méthode](imetadataassemblyimport-findexportedtypebyname-method.md)|Obtient un `mdExportedType` jeton pour le type com avec le nom spécifié.|  
|[FindManifestResourceByName, méthode](imetadataassemblyimport-findmanifestresourcebyname-method.md)|Obtient un `mdManifestResource` jeton pour la ressource avec le nom spécifié.|  
|[GetAssemblyFromScope, méthode](imetadataassemblyimport-getassemblyfromscope-method.md)|Obtient le jeton de l’assembly dans la portée de métadonnées actuelle.|  
|[GetAssemblyProps, méthode](imetadataassemblyimport-getassemblyprops-method.md)|Obtient les paramètres de propriété de l’assembly spécifié.|  
|[GetAssemblyRefProps, méthode](imetadataassemblyimport-getassemblyrefprops-method.md)|Obtient les paramètres de propriété du `mdAssemblyRef` jeton spécifié.|  
|[GetExportedTypeProps, méthode](imetadataassemblyimport-getexportedtypeprops-method.md)|Obtient les paramètres de propriété du type COM spécifié.|  
|[GetFileProps, méthode](imetadataassemblyimport-getfileprops-method.md)|Obtient les paramètres de propriété du fichier spécifié.|  
|[GetManifestResourceProps, méthode](imetadataassemblyimport-getmanifestresourceprops-method.md)|Obtient les paramètres de propriété de la ressource de manifeste spécifiée.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](metadata-interfaces.md)
- [IMetaDataAssemblyEmit, interface](imetadataassemblyemit-interface.md)
