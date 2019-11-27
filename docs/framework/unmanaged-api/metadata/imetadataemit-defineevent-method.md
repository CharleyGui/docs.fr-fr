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
ms.openlocfilehash: 6966d0ad2fefd8401b19d8e8dcf7776799a066b2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432566"
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
 dans Jeton de la classe ou de l’interface cible. Il s’agit d’un jeton `mdTypeDef` ou `mdTypeDefNil`.  
  
 `szEvent`  
 dans Nom de l’événement.  
  
 `dwEventFlags`  
 dans Indicateurs d’événement.  
  
 `tkEventType`  
 dans Jeton de la classe d’événements. Il s’agit d’un `mdTypeDef`, d’un `mdTypeRef`ou d’un jeton de `mdTokenNil`.  
  
 `mdAddOn`  
 dans Méthode utilisée pour s’abonner à l’événement, ou null.  
  
 `mdRemoveOn`  
 dans Méthode utilisée pour annuler l’abonnement à l’événement, ou null.  
  
 `mdFire`  
 dans Méthode utilisée (par une classe dérivée) pour déclencher l’événement.  
  
 `rmdOtherMethods[]`  
 dans Tableau de jetons pour d’autres méthodes associées à l’événement. Le tableau se termine par un jeton de `mdMethodDefNil`.  
  
 `pmdEvent`  
 à Jeton de métadonnées affecté à l’événement.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
