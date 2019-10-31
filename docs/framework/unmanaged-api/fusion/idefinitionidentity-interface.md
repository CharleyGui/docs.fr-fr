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
ms.openlocfilehash: 59578e1d3a66809c86f7daad1b208df2ae09568d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108038"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity, interface
Représente la signature unique du code qui définit l’application dans l’étendue actuelle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Obtient un pointeur d’interface vers un nouvel objet `IDefinitionIdentity` qui est identique à cet `IDefinitionIdentity`, à l’exception des modifications d’attribut spécifiées.|  
|`IDefinitionIdentity::EnumAttributes`|Obtient un pointeur d’interface vers un objet [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) qui contient les attributs associés à ce `IDefinitionIdentity`.|  
|`IDefinitionIdentity::GetAttribute`|Obtient la valeur de l’attribut avec le nom spécifié dans l’espace de noms spécifié.|  
|`IDefinitionIdentity::SetAttribute`|Affecte la valeur spécifiée à l’attribut qui porte le nom spécifié dans l’espace de noms spécifié.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Isolation. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
