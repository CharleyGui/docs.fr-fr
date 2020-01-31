---
title: 'IXCLRDataMethodDefinition :: EnumInstance, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: b6393d7fa4853c230203521e665bbe89d7b228e2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790442"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a>IXCLRDataMethodDefinition :: EnumInstance, méthode

Énumère les instances de cette définition de méthode.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a>Parameters

`handle`\
[in, out] Handle pour énumérer les instances.

`instance`\
à Instance énumérée.

## <a name="remarks"></a>Notes

La méthode fournie fait partie de l’interface `IXCLRDataMethodDefinition` et correspond au quatrième emplacement de la table de méthodes virtuelles.

## <a name="requirements"></a>Configuration requise pour

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête :** None  
**Bibliothèque :** None  
**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Énumération CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Débogage](index.md)
- [Interface IXCLRDataMethodDefinition](ixclrdatamethoddefinition-interface.md)
- [Interface IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)
