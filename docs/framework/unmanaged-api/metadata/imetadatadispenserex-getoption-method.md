---
title: IMetaDataDispenserEx::GetOption, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
ms.openlocfilehash: 816e2f2dc7d4d00f74f67720ee45d7b3483e57fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177720"
---
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption, méthode
Obtient la valeur de l’option spécifiée pour la portée actuelle des métadonnées. L’option contrôle la façon dont les appels à la portée actuelle des métadonnées sont traités.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `optionId`  
 [dans] Un pointeur à un GUID qui spécifie l’option à récupérer. Consultez la section Remarques pour une liste de GUIDs pris en charge.  
  
 `pValue`  
 [out] La valeur de l’option retournée. Le type de cette valeur sera une variante du type de l’option spécifiée.  
  
## <a name="remarks"></a>Notes   
 La liste suivante montre les GUIDs qui sont pris en charge pour cette méthode. Pour les descriptions, voir la méthode [IMetaDataDispenserEx::SetOption.](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) Si `optionId` ce n’est pas dans cette `E_INVALIDARG`liste, cette méthode renvoie HRESULT , indiquant un paramètre incorrect.  
  
- MetaDataCheckDuplicatesFor  
  
- MetaDataRefToDefCheck (en)  
  
- MétaDataNotificationForTokenMovement  
  
- MetaDataSetENC  
  
- MetaDataErrorIfEmitOutOfOrder MetaDataErrorIfEmitOutOfOrder MetaDataErrorIfEmitOutOfOrder MetaD  
  
- MétaDataGenerateTCEAdapters  
  
- MetaDataLinkerOptions MetaDataLinkerOptions MetaDataLinkerOptions MetaD  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataDispenserEx, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
