---
title: IAssemblyName, interface
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aee9b986c1e26c1b2e34dac7151a00172451bbad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796554"
---
# <a name="iassemblyname-interface"></a>IAssemblyName, interface
Fournit des méthodes pour décrire et utiliser l’identité unique d’un assembly.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Clone, méthode](iassemblyname-clone-method.md)|Crée une copie superficielle de cet `IAssemblyName` objet.|  
|[Finalize, méthode](iassemblyname-finalize-method.md)|Permet à `IAssemblyName` cet objet de libérer des ressources et d’effectuer d’autres opérations de nettoyage avant l’appel de son destructeur.|  
|[GetDisplayName, méthode](iassemblyname-getdisplayname-method.md)|Obtient le nom explicite de l’assembly référencé par cet `IAssemblyName` objet.|  
|[GetName, méthode](iassemblyname-getname-method.md)|Obtient le nom simple et non chiffré de l’assembly référencé par cet `IAssemblyName` objet.|  
|[GetProperty, méthode](iassemblyname-getproperty-method.md)|Obtient un pointeur vers la propriété référencée par le spécifié `PropertyId`.|  
|[GetVersion, méthode](iassemblyname-getversion-method.md)|Obtient les informations de version de l’assembly référencé par `IAssemblyName` cet objet.|  
|[IsEqual, méthode](iassemblyname-isequal-method.md)|Détermine si un objet `IAssemblyName` spécifié est égal à ce `IAssemblyName`, en fonction des indicateurs de comparaison spécifiés.|  
|[SetProperty, méthode](iassemblyname-setproperty-method.md)|Définit la valeur de la propriété référencée par le spécifié `PropertyId`.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
- [IAssemblyEnum, interface](iassemblyenum-interface.md)
