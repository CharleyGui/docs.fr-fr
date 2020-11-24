---
title: IMetaDataImport::EnumPermissionSets, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
ms.openlocfilehash: eef2c733f96d74e3353a940cc90f1a631cf48a36
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690519"
---
# <a name="imetadataimportenumpermissionsets-method"></a>IMetaDataImport::EnumPermissionSets, méthode

Énumère les autorisations pour les objets inclus dans une portée des métadonnées spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,
   [in]      mdToken       tk,
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `phEnum`  
 [in, out] Pointeur vers l’énumérateur. Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.  
  
 `tk`  
 dans Un jeton de métadonnées qui limite l’étendue de la recherche, ou NULL pour effectuer une recherche dans l’étendue la plus étendue possible.  
  
 `dwActions`  
 dans Indicateurs représentant les <xref:System.Security.Permissions.SecurityAction> valeurs à inclure dans `rPermission` , ou zéro pour retourner toutes les actions.  
  
 `rPermission`  
 à Tableau utilisé pour stocker les jetons d’autorisation.  
  
 `cMax`  
 [in] Taille maximale du tableau `rPermission`.  
  
 `pcTokens`  
 à Nombre de jetons d’autorisation retournés dans `rPermission` .  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumPermissionSets` retourné avec succès.|  
|`S_FALSE`|Il n’y a aucun jeton à énumérer. Dans ce cas, `pcTokens` est égal à zéro.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
