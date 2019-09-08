---
title: IEnumReferenceIdentity, interface
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c5d4bc1fa82f7623168050f4ee36f0ea3cd171e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796432"
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity, interface
Sert d’énumérateur pour une collection d' `IReferenceIdentity` objets.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|Obtient un pointeur d’interface vers un `IEnumReferenceIdentity` nouveau qui contient les mêmes membres que `IEnumReferenceIdentity`ce.|  
|`IEnumReferenceIdentity::Next`|Obtient le nombre spécifié d' `IReferenceIdentity` objets, en commençant à la position actuelle.|  
|`IEnumReferenceIdentity::Reset`|Déplace le pointeur d’instruction au début de ce `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Skip`|Déplace le pointeur d’instruction vers l’avant par le nombre d’éléments spécifié, en commençant à la position actuelle.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Isolation. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
- [IReferenceIdentity, interface](ireferenceidentity-interface.md)
