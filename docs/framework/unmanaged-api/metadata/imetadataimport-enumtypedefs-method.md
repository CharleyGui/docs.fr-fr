---
title: IMetaDataImport::EnumTypeDefs, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: cdfd4e10236d546af2555b125d44233172849a21
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503729"
---
# <a name="imetadataimportenumtypedefs-method"></a>IMetaDataImport::EnumTypeDefs, méthode
Énumère les jetons TypeDef représentant tous les types au sein la portée actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `phEnum`  
 à Pointeur vers le nouvel énumérateur. Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.  
  
 `rTypeDefs`  
 dans Tableau utilisé pour stocker les jetons TypeDef.  
  
 `cMax`  
 [in] Taille maximale du tableau `rTypeDefs`.  
  
 `pcTypeDefs`  
 à Nombre de jetons TypeDef retournés dans `rTypeDefs` .  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs`retourné avec succès.|  
|`S_FALSE`|Il n’y a aucun jeton à énumérer. Dans ce cas, `pcTypeDefs` est égal à zéro.|  
  
## <a name="remarks"></a>Remarques  
 Le jeton TypeDef représente un type tel qu’une classe ou une interface, ainsi qu’un type ajouté via un mécanisme d’extensibilité.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
