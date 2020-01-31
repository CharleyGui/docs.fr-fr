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
ms.openlocfilehash: a5d707d61513b030e5968af28db3c2a606e4419b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790374"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess, interface

Fournit des méthodes pour interroger les informations relatives à un processus.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Méthodes

| Méthode                                                                                                                                               | Description                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetAppDomainByUniqueId](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | Obtient un `AppDomain` dans un processus par son ID unique.                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | Fournit un handle pour énumérer les modules d’un processus.                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | Énumère les modules de ce processus.                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération des modules.               |
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | Fournit un handle pour énumérer les instances de méthode de `AppDomain` à partir d’une adresse donnée. |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | Énumère les instances de méthode de ce processus à partir d’un décalage d’adresse.                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération d’instance.             |

## <a name="remarks"></a>Notes

Cette interface se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque. Toutefois, il s’agit d’une interface COM qui dérive de `IUnknown` avec GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` qui peuvent être obtenus par le biais des mécanismes COM habituels.

## <a name="requirements"></a>Configuration requise pour

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).   
**En-tête :** None  
**Bibliothèque :** None  
**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [Interfaces de débogage](debugging-interfaces.md)
