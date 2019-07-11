---
title: IMetaDataImport::CountEnum, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1f657957d42cef1421ab3aa19f297bd04b0cacd8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781331"
---
# <a name="imetadataimportcountenum-method"></a>IMetaDataImport::CountEnum, méthode
Obtient le nombre d’éléments dans l’énumération qui a été récupérée par l’énumérateur spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `hEnum`  
 [in] Le handle pour l’énumérateur.  
  
 `pulCount`  
 [out] Le nombre d’éléments énumérés.  
  
## <a name="remarks"></a>Notes  
 Le handle spécifié par `hEnum` est obtenue à partir d’une précédente `Enum` *nom* appeler (par exemple, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
