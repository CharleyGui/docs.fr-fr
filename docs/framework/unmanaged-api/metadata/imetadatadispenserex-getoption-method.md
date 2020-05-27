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
ms.openlocfilehash: 832adacac4a6df9ccf21578538a1c557150f3ba1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008779"
---
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption, méthode
Obtient la valeur de l’option spécifiée pour la portée des métadonnées actuelle. L’option contrôle la manière dont les appels à la portée de métadonnées actuelle sont gérés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `optionId`  
 dans Pointeur vers un GUID qui spécifie l’option à récupérer. Consultez la section Notes pour obtenir la liste des GUID pris en charge.  
  
 `pValue`  
 à Valeur de l’option retournée. Le type de cette valeur sera une variante du type de l’option spécifiée.  
  
## <a name="remarks"></a>Remarques  
 La liste suivante répertorie les GUID pris en charge pour cette méthode. Pour obtenir des descriptions, consultez la méthode [IMetaDataDispenserEx :: SetOption](imetadatadispenserex-setoption-method.md) . Si `optionId` n’est pas dans cette liste, cette méthode retourne HRESULT `E_INVALIDARG` , indiquant un paramètre incorrect.  
  
- MetaDataCheckDuplicatesFor  
  
- MetaDataRefToDefCheck  
  
- MetaDataNotificationForTokenMovement  
  
- MetaDataSetENC  
  
- MetaDataErrorIfEmitOutOfOrder  
  
- MetaDataGenerateTCEAdapters  
  
- MetaDataLinkerOptions  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataDispenserEx, interface](imetadatadispenserex-interface.md)
- [IMetaDataDispenser, interface](imetadatadispenser-interface.md)
