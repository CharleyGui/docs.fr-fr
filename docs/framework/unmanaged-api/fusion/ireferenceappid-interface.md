---
title: IReferenceAppId, interface
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 522ed80f161f114af25e1fa7ad041c8238073d6f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796367"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId, interface
Représente une référence à l’identificateur unique de l’application dans l’étendue actuelle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de code pour l’application référencée par ce `IReferenceAppId`.|  
|`IReferenceAppId::put_CodeBase`|Définit l’identificateur de code pour l’application référencée par ce `IReferenceAppId`.|  
|`IReferenceAppId::EnumAppPath`|Obtient un pointeur d’interface vers `IEnumReferenceIdentity` une instance de `IReferenceIdentity` contenant les instances qui représentent les `IReferenceAppId`membres de ce.|  
|`IReferenceAppId::get_SubscriptionId`|Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de jeton pour un `IReferenceAppId`abonnement à ce.|  
|`IReferenceAppId::put_SubscriptionId`|Définit l’identificateur de jeton pour un abonnement à ce `IReferenceAppId` à la valeur de chaîne spécifiée.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Isolation. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
- [IEnumReferenceIdentity, interface](ienumreferenceidentity-interface.md)
- [IReferenceIdentity, interface](ireferenceidentity-interface.md)
