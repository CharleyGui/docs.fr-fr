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
ms.openlocfilehash: ebb689eee4a89a70e81d8f9d958e7826c3b3421b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420953"
---
# <a name="ixclrdatamethoddefinition-interface"></a>IXCLRDataMethodDefinition, interface

Fournit des méthodes pour interroger des informations sur une définition de méthode.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Méthodes

Voici quelques-unes des méthodes disponibles dans l’interface.

| Méthode                                                                                                                          | Description                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [StartEnumInstances](ixclrdatamethoddefinition-startenuminstances-method.md) | Fournit un handle pour l’énumération des instances de méthode pour un donné `IXCLRDataAppDomain` . |
| [EnumInstance](ixclrdatamethoddefinition-enuminstance-method.md)             | Énumère les instances de cette définition de méthode.                                         |
| [EndEnumInstances](ixclrdatamethoddefinition-endenuminstances-method.md)     | Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération d’instance.         |

## <a name="remarks"></a>Notes

Cette interface se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque. Toutefois, il s’agit d’une interface COM qui dérive de `IUnknown` avec `AAF60008-FB2C-420b-8FB1-42D244A54A97` un GUID qui peut être obtenu par le biais des mécanismes com habituels.

## <a name="requirements"></a>Conditions requises

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
**En-tête :** None  
**Bibliothèque :** None  
**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [Interfaces de débogage](debugging-interfaces.md)
