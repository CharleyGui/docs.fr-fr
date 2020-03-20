---
title: IMetaDataEmit::SetHandler, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
ms.openlocfilehash: 375c4b2cece0bdfd763ae383c5412c9e25614baf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177540"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler, méthode
Définit la méthode référencée par le pointeur spécifié `IUnknown` comme un rappel de notification pour les remaps symboliques.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pUnk`  
 [dans] Le gestionnaire de s’inscrire.  
  
## <a name="remarks"></a>Notes   
 Le moteur de métadonnées envoie la `SetHandler`notification en utilisant la méthode qui est fournie par , pour les compilateurs qui ne génèrent pas d’enregistrements d’une manière optimisée et qui voudraient optimiser les enregistrements enregistrés.  
  
 Si la méthode de rappel `SetHandler`n’est pas fournie par le biais, aucune optimisation `IMapToken` ne sera effectuée sur enregistrer, sauf lorsque plusieurs portées d’importation ont été fusionnées en utilisant sur la fusion pour chaque portée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
