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
ms.openlocfilehash: f664e694303691fb1132150037dcbcdb5549539a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177526"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps, méthode
Définit ou met à jour la fonction spécifiée d’un événement défini par un appel antérieur à [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).  
  
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
 [dans] Le jeton de l’événement.  
  
 `dwEventFlags`  
 [dans] Drapeaux de l’événement. C’est un peu `CorEventAttr` de valeur.  
  
 `tkEventType`  
 [dans] Le jeton pour la classe d’événement. C’est `mdTypeDef` soit `mdTypeRef` un ou un jeton.  
  
 `mdAddOn`  
 [dans] La méthode utilisée pour s’abonner à l’événement, ou nulle.  
  
 `mdRemoveOn`  
 [dans] La méthode utilisée pour se désabonner à l’événement, ou nulle.  
  
 `mdFire`  
 [dans] La méthode utilisée (par une classe dérivée) pour élever l’événement.  
  
 `rmdOtherMethods[]`  
 [dans] Un éventail de jetons pour d’autres méthodes associées à l’événement. Le dernier élément du `mdMethodDefNil`tableau doit être .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
