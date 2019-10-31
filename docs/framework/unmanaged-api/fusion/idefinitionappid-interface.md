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
ms.openlocfilehash: 5114f74e80da925c7a153b9e481c54067152eaec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108197"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId, interface
Représente un identificateur unique pour le code qui définit l’application dans l’étendue actuelle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Obtient une chaîne mise en forme qui représente le code de cet objet `IDefinitionAppId`.|  
|`IDefinitionAppId::put_Codebase`|Définit le code de cet objet `IDefinitionAppId` à la valeur de chaîne mise en forme spécifiée.|  
|`IDefinitionAppId::EnumAppPath`|Obtient un pointeur d’interface vers un objet [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) qui contient les assemblys dans le chemin d’accès de l’application actuelle.|  
|`IDefinitionAppId::SetAppPath`|Définit le chemin d’accès de l’application de l’assembly dans la portée actuelle à la valeur référencée par l’objet [IDefinitionIdentity](idefinitionidentity-interface.md) spécifié.|  
|`IDefinitionAppId::get_SubscriptionId`|Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de jeton pour un abonnement à cet objet `IDefinitionAppId`.|  
|`IDefinitionAppId::put_SubscriptionId`|Définit l’identificateur de jeton pour un abonnement à cet objet `IDefinitionAppId` à la valeur de chaîne spécifiée.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Isolation. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
