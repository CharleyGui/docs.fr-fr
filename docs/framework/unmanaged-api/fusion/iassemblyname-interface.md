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
ms.openlocfilehash: de49d66667033dfc6918b139f90cd5523661597f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134318"
---
# <a name="iassemblyname-interface"></a>IAssemblyName, interface
Fournit des méthodes pour décrire et utiliser l’identité unique d’un assembly.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Clone, méthode](iassemblyname-clone-method.md)|Crée une copie superficielle de cet objet `IAssemblyName`.|  
|[Finalize, méthode](iassemblyname-finalize-method.md)|Permet à cet objet `IAssemblyName` de libérer des ressources et d’effectuer d’autres opérations de nettoyage avant l’appel de son destructeur.|  
|[GetDisplayName, méthode](iassemblyname-getdisplayname-method.md)|Obtient le nom explicite de l’assembly référencé par cet objet `IAssemblyName`.|  
|[GetName, méthode](iassemblyname-getname-method.md)|Obtient le nom simple et non chiffré de l’assembly référencé par cet objet `IAssemblyName`.|  
|[GetProperty, méthode](iassemblyname-getproperty-method.md)|Obtient un pointeur vers la propriété référencée par le `PropertyId`spécifié.|  
|[GetVersion, méthode](iassemblyname-getversion-method.md)|Obtient les informations de version de l’assembly référencé par cet objet `IAssemblyName`.|  
|[IsEqual, méthode](iassemblyname-isequal-method.md)|Détermine si un objet `IAssemblyName` spécifié est égal à cet `IAssemblyName`, en fonction des indicateurs de comparaison spécifiés.|  
|[SetProperty, méthode](iassemblyname-setproperty-method.md)|Définit la valeur de la propriété référencée par le `PropertyId`spécifié.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
- [IAssemblyEnum, interface](iassemblyenum-interface.md)
