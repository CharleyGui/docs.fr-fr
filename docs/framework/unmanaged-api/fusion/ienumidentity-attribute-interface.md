---
title: IEnumIDENTITY_ATTRIBUTE, interface
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbb3ac150ebfe9fe3698427d8bb2bfb3e3347c07
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796463"
---
# <a name="ienumidentity_attribute-interface"></a>IEnumIDENTITY_ATTRIBUTE, interface
Sert d’énumérateur pour les attributs de l’objet de code dans l’étendue actuelle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|Obtient un pointeur d’interface vers un `IEnumIDENTITY_ATTRIBUTE` nouveau qui contient les mêmes membres que `IEnumIDENTITY_ATTRIBUTE`ce.|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|Écrit les données contenues dans les éléments de `IEnumIDENTITY_ATTRIBUTE` ce dans la mémoire tampon de données spécifiée.|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|Obtient le nombre d’attributs spécifié, en commençant à la position actuelle.|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|Déplace le pointeur d’instruction au début de ce `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|Déplace le pointeur d’instruction vers l’avant par le nombre d’éléments spécifié, en commençant à la position actuelle.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Isolation. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
