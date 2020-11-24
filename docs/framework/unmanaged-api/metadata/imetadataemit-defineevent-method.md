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
ms.openlocfilehash: 3c03497f48b8199da545d796637e5f8a5c532362
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675683"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent, méthode

Crée une définition pour un événement avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition d’événement.  
  
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
 dans Jeton de la classe ou de l’interface cible. Il s’agit d' `mdTypeDef` un `mdTypeDefNil` jeton ou.  
  
 `szEvent`  
 [in] Nom de l'événement.  
  
 `dwEventFlags`  
 dans Indicateurs d’événement.  
  
 `tkEventType`  
 dans Jeton de la classe d’événements. Il s’agit d’un `mdTypeDef` , d’un `mdTypeRef` ou d’un `mdTokenNil` jeton.  
  
 `mdAddOn`  
 dans Méthode utilisée pour s’abonner à l’événement, ou null.  
  
 `mdRemoveOn`  
 dans Méthode utilisée pour annuler l’abonnement à l’événement, ou null.  
  
 `mdFire`  
 dans Méthode utilisée (par une classe dérivée) pour déclencher l’événement.  
  
 `rmdOtherMethods[]`  
 dans Tableau de jetons pour d’autres méthodes associées à l’événement. Le tableau se termine par un `mdMethodDefNil` jeton.  
  
 `pmdEvent`  
 à Jeton de métadonnées affecté à l’événement.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
