---
title: IMetaDataEmit::DefineEvent, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: a9598be850604f16ee8cc62187e1fed7ecf3a7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175848"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent, méthode
Crée une définition pour un événement avec la signature spécifiée de métadonnées, et obtient un jeton à cette définition d’événement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineEvent (
    [in]  mdTypeDef    td,
    [in]  LPCWSTR      szEvent,
    [in]  DWORD        dwEventFlags,
    [in]  mdToken      tkEventType,
    [in]  mdMethodDef  mdAddOn,
    [in]  mdMethodDef  mdRemoveOn,
    [in]  mdMethodDef  mdFire,
    [in]  mdMethodDef  rmdOtherMethods[],
    [out] mdEvent      *pmdEvent
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `td`  
 [dans] Le jeton pour la classe ou l’interface cible. C’est `mdTypeDef` un `mdTypeDefNil` ou un jeton.  
  
 `szEvent`  
 [in] Nom de l'événement.  
  
 `dwEventFlags`  
 [dans] Drapeaux de l’événement.  
  
 `tkEventType`  
 [dans] Le jeton pour la classe d’événement. Il s’agit d’un `mdTypeDef`, un `mdTypeRef`, ou un `mdTokenNil` jeton.  
  
 `mdAddOn`  
 [dans] La méthode utilisée pour s’abonner à l’événement, ou nulle.  
  
 `mdRemoveOn`  
 [dans] La méthode utilisée pour se désabonner à l’événement, ou nulle.  
  
 `mdFire`  
 [dans] La méthode utilisée (par une classe dérivée) pour élever l’événement.  
  
 `rmdOtherMethods[]`  
 [dans] Un éventail de jetons pour d’autres méthodes associées à l’événement. Le tableau est `mdMethodDefNil` terminé avec un jeton.  
  
 `pmdEvent`  
 [out] Le jeton des métadonnées attribué à l’événement.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
