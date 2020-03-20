---
title: IXCLRDataProcess, interface
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e7e53615e38d0ab76f9e7c0a753be3c13780057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178373"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess, interface

Fournit des méthodes pour interroger des informations sur un processus.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Méthodes

| Méthode                                                                                                                                               | Description                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetAppDomainByUniqueId](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | Obtient `AppDomain` un dans un processus par son id unique.                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | Fournit une poignée pour énumérer les modules d’un processus.                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | Énumère les modules de ce processus.                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | Libère les ressources utilisées par les itérateurs internes utilisés lors du recensement du module.               |
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | Fournit une poignée pour énumérer `AppDomain` les instances de méthode de commencer à une adresse donnée. |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | Énumère les instances de méthode de ce processus à partir d’une compensation d’adresse.                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | Libère les ressources utilisées par les itérateurs internes utilisés lors du recensement par exemple.             |

## <a name="remarks"></a>Notes 

Cette interface vit à l’intérieur du temps d’exécution et n’est pas exposée à travers des en-têtes ou des fichiers de bibliothèque. Cependant, c’est une interface COM `IUnknown` qui `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` dérive avec GUID qui peut être obtenue grâce aux mécanismes COM habituels.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).
**En-tête:** Aucun  
**Bibliothèque:** Aucun  
**.NET Versions-cadre:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [Interfaces de débogage](debugging-interfaces.md)
