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
ms.openlocfilehash: 0ceadf42ac49fd3fc89c78a6a26b2f529afeeaf0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700559"
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
  
## <a name="requirements"></a>Configuration requise  

 **Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataDispenserEx, interface](imetadatadispenserex-interface.md)
- [IMetaDataDispenser, interface](imetadatadispenser-interface.md)
