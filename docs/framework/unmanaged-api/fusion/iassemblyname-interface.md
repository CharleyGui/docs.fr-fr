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
ms.openlocfilehash: f6feed9f59715f9a2801cd3a2a99a087957d4377
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715067"
---
# <a name="iassemblyname-interface"></a>IAssemblyName, interface

Fournit des méthodes pour décrire et utiliser l’identité unique d’un assembly.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Clone, méthode](iassemblyname-clone-method.md)|Crée une copie superficielle de cet `IAssemblyName` objet.|  
|[Finalize, méthode](iassemblyname-finalize-method.md)|Permet `IAssemblyName` à cet objet de libérer des ressources et d’effectuer d’autres opérations de nettoyage avant l’appel de son destructeur.|  
|[GetDisplayName, méthode](iassemblyname-getdisplayname-method.md)|Obtient le nom explicite de l’assembly référencé par cet `IAssemblyName` objet.|  
|[GetName, méthode](iassemblyname-getname-method.md)|Obtient le nom simple et non chiffré de l’assembly référencé par cet `IAssemblyName` objet.|  
|[Méthode GetProperty](iassemblyname-getproperty-method.md)|Obtient un pointeur vers la propriété référencée par le spécifié `PropertyId` .|  
|[GetVersion, méthode](iassemblyname-getversion-method.md)|Obtient les informations de version de l’assembly référencé par cet `IAssemblyName` objet.|  
|[IsEqual, méthode](iassemblyname-isequal-method.md)|Détermine si un `IAssemblyName` objet spécifié est égal à ce `IAssemblyName` , en fonction des indicateurs de comparaison spécifiés.|  
|[SetProperty, méthode](iassemblyname-setproperty-method.md)|Définit la valeur de la propriété référencée par le spécifié `PropertyId` .|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
- [IAssemblyEnum, interface](iassemblyenum-interface.md)
