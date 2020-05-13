---
title: ICorDebugProcess4, interface
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: fcf725ea98fa4351e72cf592f92968ee2233ecb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213580"
---
# <a name="icordebugprocess4-interface"></a>ICorDebugProcess4, interface

Prend en charge le contrôle de l’exécution hors processus.

## <a name="methods"></a>Méthodes

| Méthode                                                                 | Description                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [Processstatechanged,](icordebugprocess4-processstatechanged-method.md) | Notifie le pipeline ICorDebug que le débogueur hors processus poursuit l’exécution du débogueur. |

## <a name="remarks"></a>Remarks

Cette interface réside à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque. Toutefois, il s’agit d’une interface COM qui dérive de `IUnknown` avec `E930C679-78AF-4953-8AB7-B0AABF0F9F80` un GUID qui peut être obtenu par le biais des mécanismes com habituels.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** None

**Bibliothèque :** None

**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
