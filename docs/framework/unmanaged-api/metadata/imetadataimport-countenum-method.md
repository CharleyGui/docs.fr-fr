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
ms.openlocfilehash: 4521a3f15ec358a4d786a4533efb6b99d0e1c1cc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492380"
---
# <a name="imetadataimportcountenum-method"></a>IMetaDataImport::CountEnum, méthode
Obtient le nombre d’éléments de l’énumération récupérés par l’énumérateur spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `hEnum`  
 dans Handle de l’énumérateur.  
  
 `pulCount`  
 à Nombre d’éléments énumérés.  
  
## <a name="remarks"></a>Remarques  
 Le handle spécifié par `hEnum` est obtenu à partir d’un appel de `Enum` *nom* précédent (par exemple, [IMetaDataImport :: EnumTypeDefs,](imetadataimport-enumtypedefs-method.md)).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
