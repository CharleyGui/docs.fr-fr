---
title: CorThreadSafetyOptions, énumération
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
ms.openlocfilehash: 8c0527a7bc3cde7344bf809dc8e6f5a3fac04852
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007505"
---
# <a name="corthreadsafetyoptions-enumeration"></a>CorThreadSafetyOptions, énumération

Spécifie des indicateurs permettant de sélectionner des options pour la sécurité des threads.

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a>Membres

|Membre|Description|
|------------|-----------------|
|`MDThreadSafetyDefault`|Valeur par défaut. Identique à `MDThreadSafetyOff`.|
|`MDThreadSafetyOff`|Indique qu’un verrou de lecture/écriture ne peut pas être défini.|
|`MDThreadSafetyOn`|Indique qu’un verrou de lecture/écriture peut être défini.|

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** CorHdr. h

**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
