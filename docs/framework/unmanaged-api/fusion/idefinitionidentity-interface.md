---
title: IDefinitionIdentity, interface
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84c595bfdcca84ee43a53e2ea913cc978ae0953e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796522"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity, interface
Représente la signature unique du code qui définit l’application dans l’étendue actuelle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Obtient un pointeur d’interface vers un `IDefinitionIdentity` nouvel objet qui est identique à `IDefinitionIdentity`celui-ci, à l’exception des modifications d’attribut spécifiées.|  
|`IDefinitionIdentity::EnumAttributes`|Obtient un pointeur d’interface vers un objet [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) qui contient les attributs associés à `IDefinitionIdentity`ce.|  
|`IDefinitionIdentity::GetAttribute`|Obtient la valeur de l’attribut avec le nom spécifié dans l’espace de noms spécifié.|  
|`IDefinitionIdentity::SetAttribute`|Affecte la valeur spécifiée à l’attribut qui porte le nom spécifié dans l’espace de noms spécifié.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Isolation. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
