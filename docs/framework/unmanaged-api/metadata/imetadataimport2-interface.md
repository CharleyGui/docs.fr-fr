---
title: IMetaDataImport2, interface
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
ms.openlocfilehash: fe9e87618291218a41e52f80198ce9068c9c56e2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490392"
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2, interface
Étend l’interface [IMetaDataImport](imetadataimport-interface.md) pour offrir la possibilité d’utiliser des types génériques.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumGenericParamConstraints, méthode](imetadataimport2-enumgenericparamconstraints-method.md)|Obtient un énumérateur pour un tableau de contraintes de paramètres génériques associées au paramètre générique représenté par le jeton spécifié.|  
|[EnumGenericParams, méthode](imetadataimport2-enumgenericparams-method.md)|Obtient un énumérateur pour un tableau de jetons de paramètres génériques associés au jeton TypeDef ou MethodDef spécifié.|  
|[EnumMethodSpecs, méthode](imetadataimport2-enummethodspecs-method.md)|Obtient un énumérateur pour un tableau de jetons MethodSpec associés au jeton MethodDef ou MemberRef spécifié.|  
|[GetGenericParamConstraintProps, méthode](imetadataimport2-getgenericparamconstraintprops-method.md)|Obtient les métadonnées associées à la contrainte de paramètre générique représentée par le jeton de contrainte spécifié.|  
|[GetGenericParamProps, méthode](imetadataimport2-getgenericparamprops-method.md)|Obtient les métadonnées associées au paramètre générique représenté par le jeton spécifié.|  
|[GetMethodSpecProps, méthode](imetadataimport2-getmethodspecprops-method.md)|Obtient la signature de métadonnées de la méthode référencée par le jeton MethodSpec spécifié.|  
|[GetPEKind, méthode](imetadataimport2-getpekind-method.md)|Obtient une valeur identifiant la nature du code dans un fichier exécutable portable (PE), généralement un fichier DLL ou EXE, défini dans la portée des métadonnées actuelle.|  
|[GetVersionString, méthode](imetadataimport2-getversionstring-method.md)|Obtient le numéro de version du runtime qui a été utilisé pour générer l’assembly.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.PortableExecutableKinds>
- [Interfaces de métadonnées](metadata-interfaces.md)
- [IMetaDataImport, interface](imetadataimport-interface.md)
