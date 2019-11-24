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
ms.openlocfilehash: 93dd8c56176890d04d792f3c336492e4f232825b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442469"
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
|`MDThreadSafetyDefault`|Default value. Comme pour `MDThreadSafetyOff`.|
|`MDThreadSafetyOff`|Indicates that a reader/writer lock cannot be set.|
|`MDThreadSafetyOn`|Indicates that a reader/writer lock can be set.|

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**Header:** CorHdr.h

**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
