---
title: IMetaDataAssemblyEmit, interface
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
ms.openlocfilehash: 807e1ee831a43a4ef1e7b0a269ee38131f24081e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008116"
---
# <a name="imetadataassemblyemit-interface"></a>IMetaDataAssemblyEmit, interface
Fournit des méthodes qui prennent en charge le modèle d'autodescription utilisé par le Common Language Runtime pour résoudre et consommer des ressources.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[DefineAssembly, méthode](imetadataassemblyemit-defineassembly-method.md)|Crée une structure de données d'assembly contenant les métadonnées pour l'assembly spécifié et retourne le jeton de métadonnées associé.|  
|[DefineAssemblyRef, méthode](imetadataassemblyemit-defineassemblyref-method.md)|Crée une structure `AssemblyRef` contenant les métadonnées pour l'assembly que cet assembly référence et retourne le jeton de métadonnées associé.|  
|[DefineExportedType, méthode](imetadataassemblyemit-defineexportedtype-method.md)|Crée une structure `ExportedType` contenant les métadonnées pour le type exporté spécifié et retourne le jeton de métadonnées associé.|  
|[DefineFile, méthode](imetadataassemblyemit-definefile-method.md)|Crée une structure `File` contenant les métadonnées pour l'assembly référencé par cet assembly et retourne le jeton de métadonnées associé.|  
|[DefineManifestResource, méthode](imetadataassemblyemit-definemanifestresource-method.md)|Crée une structure `ManifestResource` contenant les métadonnées pour la ressource de manifeste spécifiée et retourne le jeton de métadonnées associé.|  
|[SetAssemblyProps, méthode](imetadataassemblyemit-setassemblyprops-method.md)|Modifie la structure de métadonnées `Assembly` spécifiée.|  
|[SetAssemblyRefProps, méthode](imetadataassemblyemit-setassemblyrefprops-method.md)|Modifie la structure de métadonnées `AssemblyRef` spécifiée.|  
|[SetExportedTypeProps, méthode](imetadataassemblyemit-setexportedtypeprops-method.md)|Modifie la structure de métadonnées `ExportedType` spécifiée.|  
|[SetFileProps, méthode](imetadataassemblyemit-setfileprops-method.md)|Modifie la structure de métadonnées `File` spécifiée.|  
|[SetManifestResourceProps, méthode](imetadataassemblyemit-setmanifestresourceprops-method.md)|Modifie la structure de métadonnées `ManifestResource` spécifiée.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](metadata-interfaces.md)
- [IMetaDataAssemblyImport, interface](imetadataassemblyimport-interface.md)
