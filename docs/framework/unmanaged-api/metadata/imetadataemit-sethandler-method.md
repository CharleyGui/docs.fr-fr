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
ms.openlocfilehash: 9b03dc5460875af3bb3e5e20799a4d26eb74da05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730368"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler, méthode

Définit la méthode référencée par le `IUnknown` pointeur spécifié comme un rappel de notification pour les remappages de jetons.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pUnk`  
 dans Gestionnaire à inscrire.  
  
## <a name="remarks"></a>Remarques  

 Le moteur de métadonnées envoie une notification à l’aide de la méthode fournie par `SetHandler` , aux compilateurs qui ne génèrent pas d’enregistrements de manière optimisée et qui souhaitent optimiser les enregistrements enregistrés.  
  
 Si la méthode de rappel n’est pas fournie par le biais de `SetHandler` , aucune optimisation n’est effectuée lors de l’enregistrement, sauf si plusieurs étendues d’importation ont été fusionnées à l’aide `IMapToken` de lors de la fusion pour chaque étendue.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
