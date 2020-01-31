---
title: IXCLRDataMethodDefinition, interface
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 708c681a98113a406249a360c2fc81087e5b97f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790424"
---
# <a name="ixclrdatamethoddefinition-interface"></a>IXCLRDataMethodDefinition, interface

Fournit des méthodes pour interroger des informations sur une définition de méthode.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Méthodes

Voici quelques-unes des méthodes disponibles dans l’interface.

| Méthode                                                                                                                          | Description                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [StartEnumInstances](ixclrdatamethoddefinition-startenuminstances-method.md) | Fournit un handle pour l’énumération des instances de méthode pour un `IXCLRDataAppDomain`donné. |
| [EnumInstance](ixclrdatamethoddefinition-enuminstance-method.md)             | Énumère les instances de cette définition de méthode.                                         |
| [EndEnumInstances](ixclrdatamethoddefinition-endenuminstances-method.md)     | Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération d’instance.         |

## <a name="remarks"></a>Notes

Cette interface se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque. Toutefois, il s’agit d’une interface COM qui dérive de `IUnknown` avec GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` qui peuvent être obtenus par le biais des mécanismes COM habituels.

## <a name="requirements"></a>Configuration requise pour

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête :** None  
**Bibliothèque :** None  
**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [Interfaces de débogage](debugging-interfaces.md)
