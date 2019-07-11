---
title: IMetaDataImport::EnumFields, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65f59d3df96f46ad65650183bdb6f631356a4d0b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775532"
---
# <a name="imetadataimportenumfields-method"></a>IMetaDataImport::EnumFields, méthode
Énumère les jetons FieldDef pour le type référencé par le jeton TypeDef spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `phEnum`  
 [in, out] Pointeur vers l’énumérateur.  
  
 `cl`  
 [in] Le jeton TypeDef de la classe dont les champs doivent être énumérés.  
  
 `rFields`  
 [out] La liste des jetons FieldDef.  
  
 `cMax`  
 [in] Taille maximale du tableau `rFields`.  
  
 `pcTokens`  
 [out] Le nombre réel de jetons FieldDef retournés dans `rFields`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumFields` retourné avec succès.|  
|`S_FALSE`|Il n’existe pas de champs à énumérer. Dans ce cas, `pcTokens` est égal à zéro.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
