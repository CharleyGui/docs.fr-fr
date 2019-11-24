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
ms.openlocfilehash: b4ae599a0e5cdb604fd9a610728671b39c67af31
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440900"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit, interface
Provides methods to create, modify, and save metadata about the assembly in the currently defined scope. The metadata can be stored in memory or saved to disk.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ApplyEditAndContinue, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|Updates the current assembly scope with the changes made in the specified `pImport`.|  
|[DefineCustomAttribute, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.|  
|[DefineEvent, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.|  
|[DefineField, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.|  
|[DefineImportMember, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|Creates a definition for a member of a type that is defined in a module outside the current scope, and gets a token for that reference definition.|  
|[DefineImportType, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|Creates a definition for a reference to a type that is defined in a module outside the current scope, and gets a token to that reference definition.|  
|[DefineMemberRef, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|Creates a definition for a reference to a member of a module outside the current scope, and gets a token to that reference definition.|  
|[DefineMethod, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|Creates a definition for a method with the specified signature, and returns a token to that method definition.|  
|[DefineMethodImpl, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.|  
|[DefineModuleRef, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|Creates the metadata signature for a module with the specified name.|  
|[DefineNestedType, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|Creates the metadata signature of a type definition and returns an `mdTypeDef` token for that type, additionally specifying that the defined type is a member of the type referenced by `tdEncloser`.|  
|[DefineParam, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.|  
|[DefinePermissionSet, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.|  
|[DefinePinvokeMap, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|Sets features of the PInvoke signature of the method referenced by the specified token.|  
|[DefineProperty, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.|  
|[DefineSecurityAttributeSet, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|Creates a set of security permissions to attach to the object referenced by the specified token.|  
|[DefineTypeDef, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|Creates a type definition for a common language runtime type, and gets a metadata token to that type definition.|  
|[DefineTypeRefByName, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|Gets a metadata token for a type that is defined in another module outside the current scope.|  
|[DefineUserString, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|Gets a metadata token for the specified literal string.|  
|[DeleteClassLayout, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|Destroys the class layout metadata signature for the type referenced by the specified token.|  
|[DeleteFieldMarshal, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.|  
|[DeletePinvokeMap, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|Destroys the PInvoke mapping metadata for the object referenced by the specified token.|  
|[DeleteToken, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|Deletes the specified token from the current metadata scope.|  
|[GetSaveSize, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|Gets the estimated binary size of the assembly in the current scope.|  
|[GetTokenFromSig, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|Gets a token for the specified metadata signature.|  
|[GetTokenFromTypeSpec, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|Gets a metadata token for the type with the specified metadata signature.|  
|[Merge, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|Adds the specified imported scope to the list of scopes to be merged.|  
|[MergeEnd, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|Merges into the current scope all the metadata scopes specified by one or more prior calls to `IMetaDataEmit::Merge`.|  
|[Save, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|Saves all metadata in the current scope to the file at the specified address.|  
|[SaveToMemory, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|Saves all metadata in the current scope to the specified area of memory.|  
|[SaveToStream, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|Saves all metadata in the current scope to the specified `IStream`.|  
|[SetClassLayout, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|Sets or updates the class layout signature of a type defined by a prior call to `IMetaDataEmit::DefineTypeDef`.|  
|[SetCustomAttributeValue, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|Sets or updates the value of a custom attribute defined by a prior call to `IMetaDataEmit::DefineCustomAttribute`.|  
|[SetEventProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|Sets or updates the specified feature of an event defined by a prior call to `IMetaDataEmit::DefineEvent`.|  
|[SetFieldMarshal, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.|  
|[SetFieldProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|Sets or updates the default value for the field referenced by the specified field token.|  
|[SetFieldRVA, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|Sets a global variable value for the relative virtual address of the field referenced by the specified token.|  
|[SetHandler, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.|  
|[SetMethodImplFlags, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|Sets or updates the metadata signature of the inherited method implementation referenced by the specified token.|  
|[SetMethodProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to `IMetaDataEmit::DefineMethod`.|  
|[SetModuleProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|Updates references to a module defined by a prior call to `IMetaDataEmit::DefineModuleRef`.|  
|[SetParamProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|Sets or changes features of a method parameter that was defined by a prior call to `IMetaDataEmit::DefineParam`.|  
|[SetParent, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|Establishes that the specified member, as defined by a prior call to `IMetaDataEmit::DefineMemberRef`, is a member of the specified type, as defined by a prior call to `IMetaDataEmit::DefineTypeDef`.|  
|[SetPermissionSetProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|Sets or updates features of the metadata signature of a permission set defined by a prior call to `IMetaDataEmit::DefinePermissionSet`.|  
|[SetPinvokeMap, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|Sets or changes features of a method's PInvoke signature, as defined by a prior call to `IMetaDataEmit::DefinePinvokeMap`.|  
|[SetPropertyProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|Sets the features stored in metadata for a property defined by a prior call to `IMetaDataEmit::DefineProperty`.|  
|[SetRVA, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|Sets the relative virtual address of the specified method.|  
|[SetTypeDefProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|Sets features of a type defined by a prior call to `IMetaDataEmit::DefineTypeDef`.|  
|[TranslateSigWithScope, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|Imports an assembly into the current scope and gets a new metadata signature for the merged scope.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
