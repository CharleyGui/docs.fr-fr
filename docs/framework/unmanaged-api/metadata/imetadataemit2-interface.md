---
title: IMetaDataEmit2, interface
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
ms.openlocfilehash: 7ceae6f7713ab0eb1feff550838325df0ea52de2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447917"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2, interface
Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[DefineGenericParam, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|Creates a definition for a generic type parameter, and gets a token to that generic type parameter.|  
|[DefineMethodSpec, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|Creates a generic instance of a method, and gets a token to the definition.|  
|[GetDeltaSaveSize, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.|  
|[ResetENCLog, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|Resets the edit-and-continue log and starts a new session.|  
|[SaveDelta, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|Saves changes from the current edit-and-continue session to the specified file.|  
|[SaveDeltaToMemory, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|Saves changes from the current edit-and-continue session to memory.|  
|[SaveDeltaToStream, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|Saves changes from the current edit-and-continue session to the specified stream.|  
|[SetGenericParamProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|Sets property values for the generic parameter definition referenced by the specified token.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
