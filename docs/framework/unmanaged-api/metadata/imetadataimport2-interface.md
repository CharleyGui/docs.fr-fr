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
ms.openlocfilehash: 0fd7915ef46899bdce8312bc6e8a466167e26382
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429210"
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2, interface
Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumGenericParamConstraints, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.|  
|[EnumGenericParams, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.|  
|[EnumMethodSpecs, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.|  
|[GetGenericParamConstraintProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.|  
|[GetGenericParamProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|Gets the metadata associated with the generic parameter represented by the specified token.|  
|[GetMethodSpecProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|Gets the metadata signature of the method referenced by the specified MethodSpec token.|  
|[GetPEKind, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope|  
|[GetVersionString, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|Gets the version number of the runtime that was used to build the assembly.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.PortableExecutableKinds>
- [Interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
