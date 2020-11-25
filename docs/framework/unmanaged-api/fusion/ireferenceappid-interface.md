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
ms.openlocfilehash: 9aa7173d81d84d9080d90b0890769ffeaee6a738
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728613"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId, interface

Représente une référence à l’identificateur unique de l’application dans l’étendue actuelle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de code pour l’application référencée par ce `IReferenceAppId` .|  
|`IReferenceAppId::put_CodeBase`|Définit l’identificateur de code pour l’application référencée par ce `IReferenceAppId` .|  
|`IReferenceAppId::EnumAppPath`|Obtient un pointeur d’interface vers une `IEnumReferenceIdentity` instance de contenant les `IReferenceIdentity` instances qui représentent les membres de ce `IReferenceAppId` .|  
|`IReferenceAppId::get_SubscriptionId`|Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de jeton pour un abonnement à ce `IReferenceAppId` .|  
|`IReferenceAppId::put_SubscriptionId`|Définit l’identificateur de jeton pour un abonnement à ce `IReferenceAppId` à la valeur de chaîne spécifiée.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Isolation. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
- [IEnumReferenceIdentity, interface](ienumreferenceidentity-interface.md)
- [IReferenceIdentity, interface](ireferenceidentity-interface.md)
