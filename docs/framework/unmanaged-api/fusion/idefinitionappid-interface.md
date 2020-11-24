---
title: IDefinitionAppId, interface
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
ms.openlocfilehash: 1e6c42d8e74d2d3e7925c657c67832f662416e64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673863"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId, interface

Représente un identificateur unique pour le code qui définit l’application dans l’étendue actuelle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Obtient une chaîne mise en forme qui représente le code de cet `IDefinitionAppId` objet.|  
|`IDefinitionAppId::put_Codebase`|Définit le code de cet `IDefinitionAppId` objet à la valeur de chaîne mise en forme spécifiée.|  
|`IDefinitionAppId::EnumAppPath`|Obtient un pointeur d’interface vers un objet [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) qui contient les assemblys dans le chemin d’accès de l’application actuelle.|  
|`IDefinitionAppId::SetAppPath`|Définit le chemin d’accès de l’application de l’assembly dans la portée actuelle à la valeur référencée par l’objet [IDefinitionIdentity](idefinitionidentity-interface.md) spécifié.|  
|`IDefinitionAppId::get_SubscriptionId`|Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de jeton pour un abonnement à cet `IDefinitionAppId` objet.|  
|`IDefinitionAppId::put_SubscriptionId`|Définit l’identificateur de jeton pour un abonnement à cet `IDefinitionAppId` objet à la valeur de chaîne spécifiée.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Isolation. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
