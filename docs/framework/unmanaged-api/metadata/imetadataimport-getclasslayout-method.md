---
title: IMetaDataImport::GetClassLayout, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6094bbedcc5386d3f5c0400960e47ac91defe2a1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782444"
---
# <a name="imetadataimportgetclasslayout-method"></a>IMetaDataImport::GetClassLayout, méthode
Obtient les informations de disposition pour la classe référencée par le jeton TypeDef spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetClassLayout  (   
   [in]  mdTypeDef          td,   
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `td`  
 [in] Le jeton TypeDef pour la classe avec la mise en page à retourner.  
  
 `pdwPackSize`  
 [out] Une des valeurs 1, 2, 4, 8 ou 16, qui représente la taille de pack de la classe.  
  
 `rFieldOffset`  
 [out] Un tableau de [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) valeurs.  
  
 `cMax`  
 [in] Taille maximale du tableau `rFieldOffset`.  
  
 `pcFieldOffset`  
 [out] Le nombre d’éléments retournés dans `rFieldOffset`.  
  
 `pulClassSize`  
 [out] La taille en octets de la classe représentée par `td`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
