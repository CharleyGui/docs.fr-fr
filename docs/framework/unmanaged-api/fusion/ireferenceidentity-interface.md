---
title: IReferenceIdentity, interface
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
ms.openlocfilehash: 867c09caa3bd3aed50de21c2ef91a02782830be2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704550"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity, interface

Représente une référence à la signature unique d’un objet de code.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Obtient un pointeur d’interface vers une nouvelle `IReferenceIdentity` instance qui est identique à celle-ci `IReferenceIdentity` , à l’exception des modifications d’attribut spécifiées.|  
|`IReferenceIdentity::EnumAttributes`|Obtient un pointeur d’interface vers une `IEnumIDENTITY_ATTRIBUTE` instance de qui contient les attributs associés à ce `IReferenceIdentity` .|  
|`IReferenceIdentity::GetAttribute`|Obtient la valeur de l’attribut dans l’espace de noms spécifié, avec le nom spécifié.|  
|`IReferenceIdentity::SetAttribute`|Définit l’attribut qui a l’espace de noms spécifié et le nom spécifié sur la valeur spécifiée.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Isolation. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE, interface](ienumidentity-attribute-interface.md)
