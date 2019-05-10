---
title: IMetaDataImport, interface
ms.date: 03/30/2017
api_name:
- IMetaDataImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport
helpviewer_keywords:
- IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0adbbd35-5e8d-4fec-8268-dc70a07c5975
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0f4eb244e02e13e418a55351dbc1eb1f5b5d16d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617739"
---
# <a name="imetadataimport-interface"></a>IMetaDataImport, interface
Fournit des méthodes pour importer et manipuler les métadonnées existantes à partir d'un fichier exécutable portable (PE) ou d'une autre source, comme une bibliothèque de types ou un fichier binaire de métadonnées autonome au moment de l'exécution.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CloseEnum, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|Ferme l'énumérateur avec le handle spécifié.|  
|[CountEnum, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|Obtient le nombre d'éléments dans l'énumérateur avec le handle spécifié.|  
|[EnumCustomAttributes, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|Énumère la liste des jetons de définition d'attributs personnalisés associée au type ou membre spécifié.|  
|[EnumEvents, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|Énumère les jetons de définition d'événements pour le jeton TypeDef spécifié.|  
|[EnumFields, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|Énumère les jetons FieldDef pour le type référencé par le jeton TypeDef spécifié.|  
|[EnumFieldsWithName, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|Énumère les jetons FieldDef du type spécifié avec le nom spécifié.|  
|[EnumInterfaceImpls, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|Énumère les jetons MethodDef représentant des implémentations d'interface.|  
|[EnumMemberRefs, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|Énumère les jetons MemberRef représentant les membres du type spécifié.|  
|[EnumMembers, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|Énumère les jetons MemberRef représentant les membres du type spécifié.|  
|[EnumMembersWithName, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|Énumère les jetons MemberDef représentant les membres du type spécifié avec le nom spécifié.|  
|[EnumMethodImpls, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|Énumère les jetons MethodBody et MethodDeclaration représentant les méthodes du type spécifié.|  
|[EnumMethods, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|Énumère les jetons MethodDef représentant les méthodes du type spécifié.|  
|[EnumMethodSemantics, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|Énumère les propriétés et les événements de modification de propriétés auxquels la méthode spécifiée est associée.|  
|[EnumMethodsWithName, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|Énumère les méthodes portant le nom spécifié et définies par le type référencé par le jeton TypeDef spécifié.|  
|[EnumModuleRefs, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|Énumère les jetons ModuleRef qui représentent des modules importés.|  
|[EnumParams, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|Énumère les jetons ParamDef représentant les paramètres de la méthode référencée par le jeton MethodDef spécifié.|  
|[EnumPermissionSets, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|Énumère les autorisations pour les objets inclus dans une portée des métadonnées spécifiée.|  
|[EnumProperties, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|Énumère les jetons PropertyDef représentant les propriétés du type référencé par le jeton TypeDef spécifié.|  
|[EnumSignatures, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|Énumère les jetons Signature représentant des signatures autonomes dans la portée actuelle.|  
|[EnumTypeDefs, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|Énumère les jetons TypeDef représentant tous les types au sein la portée actuelle.|  
|[EnumTypeRefs, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|Énumère les jetons TypeRef définis dans la portée des métadonnées actuelle.|  
|[EnumTypeSpecs, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|Énumère les jetons TypeSpec définis dans la portée des métadonnées actuelle.|  
|[EnumUnresolvedMethods, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|Énumère les jetons MemberDef représentant les méthodes non résolues dans la portée des métadonnées actuelle.|  
|[EnumUserStrings, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|Énumère les jetons String représentant des chaînes codées en dur dans la portée des métadonnées actuelle.|  
|[FindField, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|Obtient le jeton FieldDef pour le champ qui est membre du type spécifié et qui porte le nom spécifié et possède la signature de métadonnées spécifiée.|  
|[FindMember, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|Obtient un pointeur vers le jeton MemberDef pour le membre défini par le type spécifié avec le nom et la signature de métadonnées spécifiés.|  
|[FindMemberRef, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|Obtient un pointeur vers le jeton MemberRef pour le membre défini par le type spécifié avec le nom et la signature de métadonnées spécifiés.|  
|[FindMethod, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|Obtient un pointeur vers le jeton MethodDef pour la méthode définie par le type spécifié avec le nom et la signature de métadonnées spécifiés.|  
|[FindTypeDefByName, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|Obtient un pointeur vers le jeton de métadonnées TypeDef pour le type avec le nom spécifié.|  
|[FindTypeRef, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|Obtient un pointeur vers le jeton de métadonnées TypeRef qui référence le type dans l'étendue de recherche spécifiée avec le nom spécifié.|  
|[GetClassLayout, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|Obtient les informations de disposition pour la classe référencée par le jeton TypeDef spécifié.|  
|[GetCustomAttributeByName, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|Obtient la valeur de l'attribut personnalisé, en fonction de son nom.|  
|[GetCustomAttributeProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|Obtient la valeur de l'attribut personnalisé, en fonction de son jeton de métadonnées.|  
|[GetEventProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|Obtient les informations de métadonnées (notamment le type déclarant, les méthodes d’ajout et de suppression pour les délégués et tous les indicateurs et autres données associés) pour l’événement représenté par le jeton d’événement spécifié.|  
|[GetFieldMarshal, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|Obtient un pointeur vers le type natif non managé du champ représenté par le jeton de métadonnées Field spécifié.|  
|[GetFieldProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|Obtient les métadonnées associées au champ référencé par le jeton FieldDef spécifié.|  
|[GetInterfaceImplProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|Obtient un pointeur vers les jetons de métadonnées du type qui implémente la méthode spécifiée et de l'interface qui déclare cette méthode.|  
|[GetMemberProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|Obtient les informations de métadonnées (notamment le nom, le signature binaire et l'adresse virtuelle relative) du membre du type référencé par le jeton de métadonnées spécifié.|  
|[GetMemberRefProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|Obtient les métadonnées associées au membre référencé par le jeton spécifié.|  
|[GetMethodProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|Obtient les métadonnées associées à la méthode référencée par le jeton MethodDef spécifié.|  
|[GetMethodSemantics, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|Obtient un pointeur vers la relation entre la méthode référencée par le jeton MethodDef spécifié et la paire propriété-événement référencée par le jeton EventProp spécifié.|  
|[GetModuleFromScope, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|Obtient un pointeur vers le jeton de métadonnées pour le module référencé dans la portée de métadonnées actuelle.|  
|[GetModuleRefProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|Obtient le nom du module référencé par le jeton de métadonnées spécifié.|  
|[GetNameFromToken, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|Obtient le nom UTF-8 de l'objet référencé par le jeton de métadonnées spécifié.|  
|[GetNativeCallConvFromSig, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|Obtient la convention d’appel native pour la méthode représentée par le pointeur de signature spécifié.|  
|[GetNestedClassProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|Obtient le jeton TypeDef pour le type parent englobant du type imbriqué spécifié.|  
|[GetParamForMethodIndex, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|Obtient un pointeur vers le jeton qui représente le paramètre à la position ordinale spécifiée dans la séquence des paramètres de méthode pour la méthode représentée par le jeton MethodDef spécifié.|  
|[GetParamProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|Obtient les valeurs de métadonnées pour le paramètre référencé par le jeton ParamDef spécifié.|  
|[GetPermissionSetProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|Obtient les métadonnées associées au System.Security.PermissionSet représenté par le jeton Permission spécifié.|  
|[GetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|Obtient un jeton ModuleRef pour représenter l'assembly cible d'un appel PInvoke.|  
|[GetPropertyProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|Obtient les métadonnées associées à la propriété représentée par le jeton spécifié.|  
|[GetRVA, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|Obtient le décalage de l'adresse virtuelle relative de l'objet de code représenté par le jeton spécifié.|  
|[GetScopeProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|Obtient le nom et éventuellement l'identificateur de version de l'assembly ou du module dans la portée de métadonnées actuelle.|  
|[GetSigFromToken, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|Obtient la signature de métadonnées binaires associée au jeton spécifié.|  
|[GetTypeDefProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|Retourne des informations de métadonnées pour le type représenté par le jeton TypeDef spécifié.|  
|[GetTypeRefProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|Obtient les métadonnées associées au type référencé par le jeton TypeRef spécifié.|  
|[GetTypeSpecFromToken, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|Obtient la signature de métadonnées binaires de la spécification de type représentée par le jeton spécifié.|  
|[GetUserString, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|Obtient la chaîne littérale représentée par le jeton de métadonnées spécifié.|  
|[IsGlobal, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|Obtient une valeur qui indique si le champ, la méthode ou le type représenté(e) par le jeton de métadonnées spécifié a une portée globale.|  
|[IsValidToken, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|Obtient une valeur indiquant si le jeton spécifié contient une référence valide à un objet de code.|  
|[ResetEnum, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|Réinitialise l'énumérateur spécifié à la position spécifiée.|  
|[ResolveTypeRef, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|Obtient des informations de type pour le type référencé par le jeton TypeRef spécifié.|  
  
## <a name="remarks"></a>Notes  
 La vocation première de la conception de l'interface `IMetaDataImport` est d'être utilisée par les outils et services qui importent des informations de type (par exemple, les outils de développement) ou qui gèrent des composants déployés (par exemple, les services de résolution/d'activation). Les méthodes `IMetaDataImport` appartiennent aux catégories de tâches suivantes :  
  
- Énumération des collections d'éléments dans la portée des métadonnées.  
  
- Recherche d'un élément qui possède un ensemble spécifique de caractéristiques.  
  
- Obtention des propriétés d'un élément spécifié.  
  
- Les méthodes Get sont conçues spécifiquement pour retourner les propriétés à valeur unique d'un élément de métadonnées. Quand la propriété est une référence à un autre élément, un jeton est retourné pour cet élément. Tout type d'entrée de pointeur peut être NULL pour indiquer que la valeur particulière n'est pas demandée. Pour obtenir les propriétés qui sont essentiellement des objets de collection (par exemple, la collection des interfaces qu’une classe implémente), utilisez les méthodes d’énumération.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
