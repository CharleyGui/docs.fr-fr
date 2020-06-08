---
title: IMetaDataImport::EnumUnresolvedMethods, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
ms.openlocfilehash: c991c0af845bc6825db6b3bf258fe0809d5db804
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503692"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a>IMetaDataImport::EnumUnresolvedMethods, méthode
Énumère les jetons MemberDef représentant les méthodes non résolues dans la portée des métadonnées actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `phEnum`  
 [in, out] Pointeur vers l’énumérateur. Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.  
  
 `rMethods`  
 à Tableau utilisé pour stocker les jetons MemberDef.  
  
 `cMax`  
 [in] Taille maximale du tableau `rMethods`.  
  
 `pcTokens`  
 à Nombre de jetons MemberDef retournés dans `rMethods` .  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumUnresolvedMethods`retourné avec succès.|  
|`S_FALSE`|Il n’y a aucun jeton à énumérer. Dans ce cas, `pcTokens` est égal à zéro.|  
  
## <a name="remarks"></a>Remarques  
 Une méthode non résolue est une méthode qui a été déclarée mais qui n’est pas implémentée. Une méthode est incluse dans l’énumération si la méthode est marquée `miForwardRef` et si `mdPinvokeImpl` ou a la `miRuntime` valeur zéro. En d’autres termes, une méthode non résolue est une méthode de classe marquée `miForwardRef` mais qui n’est pas implémentée dans du code non managé (atteinte via PInvoke), ni implémentée en interne par le runtime lui-même  
  
 L’énumération exclut toutes les méthodes définies au niveau de la portée du module (globales) ou dans les interfaces ou les classes abstraites.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
