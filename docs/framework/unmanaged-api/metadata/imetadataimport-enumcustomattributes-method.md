---
title: IMetaDataImport::EnumCustomAttributes, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 3b12200dae23a7b6a2f6e1654e46fdf74dc90968
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700533"
---
# <a name="imetadataimportenumcustomattributes-method"></a>IMetaDataImport::EnumCustomAttributes, méthode

Énumère les jetons de définition d’attribut personnalisés associés au type ou au membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `phEnum`  
 [in, out] Pointeur vers l’énumérateur retourné.  
  
 `tk`  
 dans Jeton pour la portée de l’énumération, ou zéro pour tous les attributs personnalisés.  
  
 `tkType`  
 dans Jeton pour le constructeur du type des attributs à énumérer, ou `null` pour tous les types.  
  
 `rCustomAttributes`  
 à Tableau de jetons d’attributs personnalisés.  
  
 `cMax`  
 [in] Taille maximale du tableau `rCustomAttributes`.  
  
 `pcCustomAttributes`  
 [out, optional] Nombre réel de valeurs de jeton retournées dans `rCustomAttributes` .  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumCustomAttributes` retourné avec succès.|  
|`S_FALSE`|Il n’existe aucun attribut personnalisé à énumérer. Dans ce cas, `pcCustomAttributes` est égal à zéro.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
