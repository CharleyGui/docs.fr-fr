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
ms.openlocfilehash: 0049db66d7a753488388c85e87e1f907db56c7cf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679089"
---
# <a name="imetadataimport-interface"></a>IMetaDataImport, interface

Fournit des méthodes pour importer et manipuler les métadonnées existantes à partir d'un fichier exécutable portable (PE) ou d'une autre source, comme une bibliothèque de types ou un fichier binaire de métadonnées autonome au moment de l'exécution.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CloseEnum, méthode](imetadataimport-closeenum-method.md)|Ferme l'énumérateur avec le handle spécifié.|  
|[CountEnum, méthode](imetadataimport-countenum-method.md)|Obtient le nombre d'éléments dans l'énumérateur avec le handle spécifié.|  
|[EnumCustomAttributes, méthode](imetadataimport-enumcustomattributes-method.md)|Énumère la liste des jetons de définition d'attributs personnalisés associée au type ou membre spécifié.|  
|[EnumEvents, méthode](imetadataimport-enumevents-method.md)|Énumère les jetons de définition d'événements pour le jeton TypeDef spécifié.|  
|[EnumFields, méthode](imetadataimport-enumfields-method.md)|Énumère les jetons FieldDef pour le type référencé par le jeton TypeDef spécifié.|  
|[EnumFieldsWithName, méthode](imetadataimport-enumfieldswithname-method.md)|Énumère les jetons FieldDef du type spécifié avec le nom spécifié.|  
|[EnumInterfaceImpls, méthode](imetadataimport-enuminterfaceimpls-method.md)|Énumère les jetons MethodDef représentant des implémentations d'interface.|  
|[EnumMemberRefs, méthode](imetadataimport-enummemberrefs-method.md)|Énumère les jetons MemberRef représentant les membres du type spécifié.|  
|[EnumMembers, méthode](imetadataimport-enummembers-method.md)|Énumère les jetons MemberRef représentant les membres du type spécifié.|  
|[EnumMembersWithName, méthode](imetadataimport-enummemberswithname-method.md)|Énumère les jetons MemberDef représentant les membres du type spécifié avec le nom spécifié.|  
|[EnumMethodImpls, méthode](imetadataimport-enummethodimpls-method.md)|Énumère les jetons MethodBody et MethodDeclaration représentant les méthodes du type spécifié.|  
|[EnumMethods, méthode](imetadataimport-enummethods-method.md)|Énumère les jetons MethodDef représentant les méthodes du type spécifié.|  
|[EnumMethodSemantics, méthode](imetadataimport-enummethodsemantics-method.md)|Énumère les propriétés et les événements de modification de propriétés auxquels la méthode spécifiée est associée.|  
|[EnumMethodsWithName, méthode](imetadataimport-enummethodswithname-method.md)|Énumère les méthodes portant le nom spécifié et définies par le type référencé par le jeton TypeDef spécifié.|  
|[EnumModuleRefs, méthode](imetadataimport-enummodulerefs-method.md)|Énumère les jetons ModuleRef qui représentent des modules importés.|  
|[EnumParams, méthode](imetadataimport-enumparams-method.md)|Énumère les jetons ParamDef représentant les paramètres de la méthode référencée par le jeton MethodDef spécifié.|  
|[EnumPermissionSets, méthode](imetadataimport-enumpermissionsets-method.md)|Énumère les autorisations pour les objets inclus dans une portée des métadonnées spécifiée.|  
|[EnumProperties, méthode](imetadataimport-enumproperties-method.md)|Énumère les jetons PropertyDef représentant les propriétés du type référencé par le jeton TypeDef spécifié.|  
|[EnumSignatures, méthode](imetadataimport-enumsignatures-method.md)|Énumère les jetons Signature représentant des signatures autonomes dans la portée actuelle.|  
|[EnumTypeDefs, méthode](imetadataimport-enumtypedefs-method.md)|Énumère les jetons TypeDef représentant tous les types au sein la portée actuelle.|  
|[EnumTypeRefs, méthode](imetadataimport-enumtyperefs-method.md)|Énumère les jetons TypeRef définis dans la portée des métadonnées actuelle.|  
|[EnumTypeSpecs, méthode](imetadataimport-enumtypespecs-method.md)|Énumère les jetons TypeSpec définis dans la portée des métadonnées actuelle.|  
|[EnumUnresolvedMethods, méthode](imetadataimport-enumunresolvedmethods-method.md)|Énumère les jetons MemberDef représentant les méthodes non résolues dans la portée des métadonnées actuelle.|  
|[EnumUserStrings, méthode](imetadataimport-enumuserstrings-method.md)|Énumère les jetons String représentant des chaînes codées en dur dans la portée des métadonnées actuelle.|  
|[FindField, méthode](imetadataimport-findfield-method.md)|Obtient le jeton FieldDef pour le champ qui est membre du type spécifié et qui porte le nom spécifié et possède la signature de métadonnées spécifiée.|  
|[FindMember, méthode](imetadataimport-findmember-method.md)|Obtient un pointeur vers le jeton MemberDef pour le membre défini par le type spécifié avec le nom et la signature de métadonnées spécifiés.|  
|[FindMemberRef, méthode](imetadataimport-findmemberref-method.md)|Obtient un pointeur vers le jeton MemberRef pour le membre défini par le type spécifié avec le nom et la signature de métadonnées spécifiés.|  
|[FindMethod, méthode](imetadataimport-findmethod-method.md)|Obtient un pointeur vers le jeton MethodDef pour la méthode définie par le type spécifié avec le nom et la signature de métadonnées spécifiés.|  
|[FindTypeDefByName, méthode](imetadataimport-findtypedefbyname-method.md)|Obtient un pointeur vers le jeton de métadonnées TypeDef pour le type avec le nom spécifié.|  
|[FindTypeRef, méthode](imetadataimport-findtyperef-method.md)|Obtient un pointeur vers le jeton de métadonnées TypeRef qui référence le type dans l'étendue de recherche spécifiée avec le nom spécifié.|  
|[GetClassLayout, méthode](imetadataimport-getclasslayout-method.md)|Obtient les informations de disposition pour la classe référencée par le jeton TypeDef spécifié.|  
|[GetCustomAttributeByName, méthode](imetadataimport-getcustomattributebyname-method.md)|Obtient la valeur de l'attribut personnalisé, en fonction de son nom.|  
|[GetCustomAttributeProps, méthode](imetadataimport-getcustomattributeprops-method.md)|Obtient la valeur de l'attribut personnalisé, en fonction de son jeton de métadonnées.|  
|[GetEventProps, méthode](imetadataimport-geteventprops-method.md)|Obtient les informations de métadonnées (notamment le type déclarant, les méthodes d’ajout et de suppression pour les délégués et tous les indicateurs et autres données associés) pour l’événement représenté par le jeton d’événement spécifié.|  
|[GetFieldMarshal, méthode](imetadataimport-getfieldmarshal-method.md)|Obtient un pointeur vers le type natif non managé du champ représenté par le jeton de métadonnées Field spécifié.|  
|[GetFieldProps, méthode](imetadataimport-getfieldprops-method.md)|Obtient les métadonnées associées au champ référencé par le jeton FieldDef spécifié.|  
|[GetInterfaceImplProps, méthode](imetadataimport-getinterfaceimplprops-method.md)|Obtient un pointeur vers les jetons de métadonnées du type qui implémente la méthode spécifiée et de l'interface qui déclare cette méthode.|  
|[GetMemberProps, méthode](imetadataimport-getmemberprops-method.md)|Obtient les informations de métadonnées (notamment le nom, le signature binaire et l'adresse virtuelle relative) du membre du type référencé par le jeton de métadonnées spécifié.|  
|[GetMemberRefProps, méthode](imetadataimport-getmemberrefprops-method.md)|Obtient les métadonnées associées au membre référencé par le jeton spécifié.|  
|[GetMethodProps, méthode](imetadataimport-getmethodprops-method.md)|Obtient les métadonnées associées à la méthode référencée par le jeton MethodDef spécifié.|  
|[GetMethodSemantics, méthode](imetadataimport-getmethodsemantics-method.md)|Obtient un pointeur vers la relation entre la méthode référencée par le jeton MethodDef spécifié et la paire propriété-événement référencée par le jeton EventProp spécifié.|  
|[GetModuleFromScope, méthode](imetadataimport-getmodulefromscope-method.md)|Obtient un pointeur vers le jeton de métadonnées pour le module référencé dans la portée de métadonnées actuelle.|  
|[GetModuleRefProps, méthode](imetadataimport-getmodulerefprops-method.md)|Obtient le nom du module référencé par le jeton de métadonnées spécifié.|  
|[GetNameFromToken, méthode](imetadataimport-getnamefromtoken-method.md)|Obtient le nom UTF-8 de l'objet référencé par le jeton de métadonnées spécifié.|  
|[GetNativeCallConvFromSig, méthode](imetadataimport-getnativecallconvfromsig-method.md)|Obtient la convention d’appel native pour la méthode représentée par le pointeur de signature spécifié.|  
|[GetNestedClassProps, méthode](imetadataimport-getnestedclassprops-method.md)|Obtient le jeton TypeDef pour le type parent englobant du type imbriqué spécifié.|  
|[GetParamForMethodIndex, méthode](imetadataimport-getparamformethodindex-method.md)|Obtient un pointeur vers le jeton qui représente le paramètre à la position ordinale spécifiée dans la séquence des paramètres de méthode pour la méthode représentée par le jeton MethodDef spécifié.|  
|[GetParamProps, méthode](imetadataimport-getparamprops-method.md)|Obtient les valeurs de métadonnées pour le paramètre référencé par le jeton ParamDef spécifié.|  
|[GetPermissionSetProps, méthode](imetadataimport-getpermissionsetprops-method.md)|Obtient les métadonnées associées au System.Security.PermissionSet représenté par le jeton Permission spécifié.|  
|[GetPinvokeMap](imetadataimport-getpinvokemap-method.md)|Obtient un jeton ModuleRef pour représenter l'assembly cible d'un appel PInvoke.|  
|[GetPropertyProps, méthode](imetadataimport-getpropertyprops-method.md)|Obtient les métadonnées associées à la propriété représentée par le jeton spécifié.|  
|[GetRVA, méthode](imetadataimport-getrva-method.md)|Obtient le décalage de l'adresse virtuelle relative de l'objet de code représenté par le jeton spécifié.|  
|[GetScopeProps, méthode](imetadataimport-getscopeprops-method.md)|Obtient le nom et éventuellement l'identificateur de version de l'assembly ou du module dans la portée de métadonnées actuelle.|  
|[GetSigFromToken, méthode](imetadataimport-getsigfromtoken-method.md)|Obtient la signature de métadonnées binaires associée au jeton spécifié.|  
|[GetTypeDefProps, méthode](imetadataimport-gettypedefprops-method.md)|Retourne des informations de métadonnées pour le type représenté par le jeton TypeDef spécifié.|  
|[GetTypeRefProps, méthode](imetadataimport-gettyperefprops-method.md)|Obtient les métadonnées associées au type référencé par le jeton TypeRef spécifié.|  
|[GetTypeSpecFromToken, méthode](imetadataimport-gettypespecfromtoken-method.md)|Obtient la signature de métadonnées binaires de la spécification de type représentée par le jeton spécifié.|  
|[GetUserString, méthode](imetadataimport-getuserstring-method.md)|Obtient la chaîne littérale représentée par le jeton de métadonnées spécifié.|  
|[IsGlobal, méthode](imetadataimport-isglobal-method.md)|Obtient une valeur qui indique si le champ, la méthode ou le type représenté(e) par le jeton de métadonnées spécifié a une portée globale.|  
|[IsValidToken, méthode](imetadataimport-isvalidtoken-method.md)|Obtient une valeur indiquant si le jeton spécifié contient une référence valide à un objet de code.|  
|[ResetEnum, méthode](imetadataimport-resetenum-method.md)|Réinitialise l'énumérateur spécifié à la position spécifiée.|  
|[ResolveTypeRef, méthode](imetadataimport-resolvetyperef-method.md)|Obtient des informations de type pour le type référencé par le jeton TypeRef spécifié.|  
  
## <a name="remarks"></a>Remarques  

 La vocation première de la conception de l'interface `IMetaDataImport` est d'être utilisée par les outils et services qui importent des informations de type (par exemple, les outils de développement) ou qui gèrent des composants déployés (par exemple, les services de résolution/d'activation). Les méthodes `IMetaDataImport` appartiennent aux catégories de tâches suivantes :  
  
- Énumération des collections d'éléments dans la portée des métadonnées.  
  
- Recherche d'un élément qui possède un ensemble spécifique de caractéristiques.  
  
- Obtention des propriétés d'un élément spécifié.  
  
- Les méthodes Get sont conçues spécifiquement pour retourner les propriétés à valeur unique d'un élément de métadonnées. Quand la propriété est une référence à un autre élément, un jeton est retourné pour cet élément. Tout type d'entrée de pointeur peut être NULL pour indiquer que la valeur particulière n'est pas demandée. Pour obtenir les propriétés qui sont essentiellement des objets de collection (par exemple, la collection des interfaces qu’une classe implémente), utilisez les méthodes d’énumération.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](metadata-interfaces.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
