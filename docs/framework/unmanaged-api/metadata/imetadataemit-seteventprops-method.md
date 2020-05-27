---
title: IMetaDataEmit::SetEventProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: 720133e64c02aa09c9ff7e43a20630b0d55c1acf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008753"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps, méthode
Définit ou met à jour la fonctionnalité spécifiée d’un événement défini par un appel antérieur à [IMetaDataEmit ::D efineevent](imetadataemit-defineevent-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,
    [in]  DWORD       dwEventFlags,
    [in]  mdToken     tkEventType,
    [in]  mdMethodDef mdAddOn,
    [in]  mdMethodDef mdRemoveOn,
    [in]  mdMethodDef mdFire,
    [in]  mdMethodDef rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ev`  
 dans Jeton d’événement.  
  
 `dwEventFlags`  
 dans Indicateurs d’événement. Il s’agit d’un masque de `CorEventAttr` valeur de valeurs.  
  
 `tkEventType`  
 dans Jeton de la classe d’événements. Il s’agit soit d’un jeton, soit d’un `mdTypeDef` `mdTypeRef` jeton.  
  
 `mdAddOn`  
 dans Méthode utilisée pour s’abonner à l’événement, ou null.  
  
 `mdRemoveOn`  
 dans Méthode utilisée pour annuler l’abonnement à l’événement, ou null.  
  
 `mdFire`  
 dans Méthode utilisée (par une classe dérivée) pour déclencher l’événement.  
  
 `rmdOtherMethods[]`  
 dans Tableau de jetons pour d’autres méthodes associées à l’événement. Le dernier élément du tableau doit être `mdMethodDefNil` .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
