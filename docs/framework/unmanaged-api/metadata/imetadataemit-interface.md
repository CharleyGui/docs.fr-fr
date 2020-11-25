---
title: IMetaDataEmit, interface
ms.date: 03/30/2017
api_name:
- IMetaDataEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit
helpviewer_keywords:
- IMetaDataEmit interface [.NET Framework metadata]
ms.assetid: 3b48fd47-7397-4e2c-8bec-8157aa08978c
topic_type:
- apiref
ms.openlocfilehash: f5495c170abf3e991a6e28016687f8ae77f0b423
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722022"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit, interface

Fournit des méthodes pour créer, modifier et enregistrer des métadonnées relatives à l’assembly dans l’étendue actuellement définie. Les métadonnées peuvent être stockées dans la mémoire ou enregistrées sur le disque.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ApplyEditAndContinue, méthode](imetadataemit-applyeditandcontinue-method.md)|Met à jour la portée de l’assembly actuel avec les modifications apportées dans le spécifié `pImport` .|  
|[DefineCustomAttribute, méthode](imetadataemit-definecustomattribute-method.md)|Crée une définition pour un attribut personnalisé avec la signature de métadonnées spécifiée, à attacher à l’objet spécifié et obtient un jeton pour cette définition d’attribut personnalisé.|  
|[DefineEvent, méthode](imetadataemit-defineevent-method.md)|Crée une définition pour un événement avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition d’événement.|  
|[DefineField, méthode](imetadataemit-definefield-method.md)|Crée une définition pour un champ avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition de champ.|  
|[DefineImportMember, méthode](imetadataemit-defineimportmember-method.md)|Crée une définition pour un membre d’un type qui est défini dans un module à l’extérieur de la portée actuelle et obtient un jeton pour cette définition de référence.|  
|[DefineImportType, méthode](imetadataemit-defineimporttype-method.md)|Crée une définition pour une référence à un type défini dans un module à l’extérieur de la portée actuelle et obtient un jeton pour cette définition de référence.|  
|[DefineMemberRef, méthode](imetadataemit-definememberref-method.md)|Crée une définition pour une référence à un membre d’un module à l’extérieur de la portée actuelle et obtient un jeton pour cette définition de référence.|  
|[DefineMethod, méthode](imetadataemit-definemethod-method.md)|Crée une définition pour une méthode avec la signature spécifiée et retourne un jeton à cette définition de méthode.|  
|[DefineMethodImpl, méthode](imetadataemit-definemethodimpl-method.md)|Crée une définition pour l’implémentation d’une méthode héritée d’une interface et retourne un jeton à cette définition d’implémentation de méthode.|  
|[DefineModuleRef, méthode](imetadataemit-definemoduleref-method.md)|Crée la signature de métadonnées pour un module avec le nom spécifié.|  
|[DefineNestedType, méthode](imetadataemit-definenestedtype-method.md)|Crée la signature de métadonnées d’une définition de type et retourne un `mdTypeDef` jeton pour ce type, en spécifiant en outre que le type défini est un membre du type référencé par `tdEncloser` .|  
|[DefineParam, méthode](imetadataemit-defineparam-method.md)|Crée une définition de paramètre avec la signature spécifiée pour la méthode référencée par le jeton spécifié et obtient un jeton pour cette définition de paramètre.|  
|[DefinePermissionSet, méthode](imetadataemit-definepermissionset-method.md)|Crée une définition pour un jeu d’autorisations avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition de jeu d’autorisations.|  
|[DefinePinvokeMap, méthode](imetadataemit-definepinvokemap-method.md)|Définit les fonctionnalités de la signature PInvoke de la méthode référencée par le jeton spécifié.|  
|[DefineProperty, méthode](imetadataemit-defineproperty-method.md)|Crée une définition de propriété pour le type spécifié, avec les `get` accesseurs de méthode et spécifiés `set` , et obtient un jeton pour cette définition de propriété.|  
|[DefineSecurityAttributeSet, méthode](imetadataemit-definesecurityattributeset-method.md)|Crée un jeu d’autorisations de sécurité à attacher à l’objet référencé par le jeton spécifié.|  
|[DefineTypeDef, méthode](imetadataemit-definetypedef-method.md)|Crée une définition de type pour un type de common language runtime et obtient un jeton de métadonnées pour cette définition de type.|  
|[DefineTypeRefByName, méthode](imetadataemit-definetyperefbyname-method.md)|Obtient un jeton de métadonnées pour un type qui est défini dans un autre module à l’extérieur de la portée actuelle.|  
|[DefineUserString, méthode](imetadataemit-defineuserstring-method.md)|Obtient un jeton de métadonnées pour la chaîne littérale spécifiée.|  
|[DeleteClassLayout, méthode](imetadataemit-deleteclasslayout-method.md)|Détruit la signature des métadonnées de disposition de la classe pour le type référencé par le jeton spécifié.|  
|[DeleteFieldMarshal, méthode](imetadataemit-deletefieldmarshal-method.md)|Détruit la signature de métadonnées de marshaling PInvoke pour l’objet référencé par le jeton spécifié.|  
|[DeletePinvokeMap, méthode](imetadataemit-deletepinvokemap-method.md)|Détruit les métadonnées de mappage PInvoke pour l’objet référencé par le jeton spécifié.|  
|[DeleteToken, méthode](imetadataemit-deletetoken-method.md)|Supprime le jeton spécifié de la portée de métadonnées actuelle.|  
|[GetSaveSize, méthode](imetadataemit-getsavesize-method.md)|Obtient la taille estimée en binaire de l’assembly dans l’étendue actuelle.|  
|[GetTokenFromSig, méthode](imetadataemit-gettokenfromsig-method.md)|Obtient un jeton pour la signature de métadonnées spécifiée.|  
|[GetTokenFromTypeSpec, méthode](imetadataemit-gettokenfromtypespec-method.md)|Obtient un jeton de métadonnées pour le type avec la signature de métadonnées spécifiée.|  
|[Merge, méthode](imetadataemit-merge-method.md)|Ajoute l’étendue importée spécifiée à la liste des étendues à fusionner.|  
|[MergeEnd, méthode](imetadataemit-mergeend-method.md)|Fusionne dans la portée actuelle toutes les portées de métadonnées spécifiées par un ou plusieurs appels antérieurs à `IMetaDataEmit::Merge` .|  
|[Save, méthode](imetadataemit-save-method.md)|Enregistre toutes les métadonnées de l’étendue actuelle dans le fichier à l’adresse spécifiée.|  
|[SaveToMemory, méthode](imetadataemit-savetomemory-method.md)|Enregistre toutes les métadonnées dans la portée actuelle dans la zone de mémoire spécifiée.|  
|[SaveToStream, méthode](imetadataemit-savetostream-method.md)|Enregistre toutes les métadonnées dans la portée actuelle dans le spécifié `IStream` .|  
|[SetClassLayout, méthode](imetadataemit-setclasslayout-method.md)|Définit ou met à jour la signature de la disposition de la classe d’un type défini par un appel antérieur à `IMetaDataEmit::DefineTypeDef` .|  
|[SetCustomAttributeValue, méthode](imetadataemit-setcustomattributevalue-method.md)|Définit ou met à jour la valeur d’un attribut personnalisé défini par un appel antérieur à `IMetaDataEmit::DefineCustomAttribute` .|  
|[SetEventProps, méthode](imetadataemit-seteventprops-method.md)|Définit ou met à jour la fonctionnalité spécifiée d’un événement défini par un appel antérieur à `IMetaDataEmit::DefineEvent` .|  
|[SetFieldMarshal, méthode](imetadataemit-setfieldmarshal-method.md)|Définit les informations de marshaling PInvoke pour le champ, le retour de méthode ou le paramètre de méthode référencé par le jeton spécifié.|  
|[SetFieldProps, méthode](imetadataemit-setfieldprops-method.md)|Définit ou met à jour la valeur par défaut pour le champ référencé par le jeton de champ spécifié.|  
|[SetFieldRVA, méthode](imetadataemit-setfieldrva-method.md)|Définit une valeur de variable globale pour l’adresse virtuelle relative du champ référencé par le jeton spécifié.|  
|[SetHandler, méthode](imetadataemit-sethandler-method.md)|Définit la méthode référencée par le `IUnknown` pointeur spécifié comme un rappel de notification pour les remappages de jetons.|  
|[SetMethodImplFlags, méthode](imetadataemit-setmethodimplflags-method.md)|Définit ou met à jour la signature de métadonnées de l’implémentation de méthode héritée référencée par le jeton spécifié.|  
|[SetMethodProps, méthode](imetadataemit-setmethodprops-method.md)|Définit ou met à jour la fonctionnalité, stockée à l’adresse virtuelle relative spécifiée, d’une méthode définie par un appel antérieur à `IMetaDataEmit::DefineMethod` .|  
|[SetModuleProps, méthode](imetadataemit-setmoduleprops-method.md)|Met à jour les références à un module défini par un appel antérieur à `IMetaDataEmit::DefineModuleRef` .|  
|[SetParamProps, méthode](imetadataemit-setparamprops-method.md)|Définit ou modifie les fonctionnalités d’un paramètre de méthode qui a été défini par un appel antérieur à `IMetaDataEmit::DefineParam` .|  
|[SetParent, méthode](imetadataemit-setparent-method.md)|Établit que le membre spécifié, tel que défini par un appel antérieur à `IMetaDataEmit::DefineMemberRef` , est un membre du type spécifié, tel que défini par un appel antérieur à `IMetaDataEmit::DefineTypeDef` .|  
|[SetPermissionSetProps, méthode](imetadataemit-setpermissionsetprops-method.md)|Définit ou met à jour les fonctionnalités de la signature de métadonnées d’un jeu d’autorisations défini par un appel antérieur à `IMetaDataEmit::DefinePermissionSet` .|  
|[SetPinvokeMap, méthode](imetadataemit-setpinvokemap-method.md)|Définit ou modifie les fonctionnalités de la signature PInvoke d’une méthode, comme défini par un appel antérieur à `IMetaDataEmit::DefinePinvokeMap` .|  
|[SetPropertyProps, méthode](imetadataemit-setpropertyprops-method.md)|Définit les fonctionnalités stockées dans les métadonnées d’une propriété définie par un appel antérieur à `IMetaDataEmit::DefineProperty` .|  
|[SetRVA, méthode](imetadataemit-setrva-method.md)|Définit l’adresse virtuelle relative de la méthode spécifiée.|  
|[SetTypeDefProps, méthode](imetadataemit-settypedefprops-method.md)|Définit les fonctionnalités d’un type défini par un appel antérieur à `IMetaDataEmit::DefineTypeDef` .|  
|[TranslateSigWithScope, méthode](imetadataemit-translatesigwithscope-method.md)|Importe un assembly dans la portée actuelle et obtient une nouvelle signature de métadonnées pour la portée fusionnée.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](metadata-interfaces.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
