---
title: 'IXCLRDataProcess :: StartEnumMethodInstancesByAddress, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e28fa73300e147ac07a2d325fbf517480bb73797
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394945"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a>IXCLRDataProcess :: StartEnumMethodInstancesByAddress, méthode

Fournit un handle pour énumérer les instances de méthode de `AppDomain` à partir d’une adresse donnée.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a>Paramètres

`address`\
dans Adresse de la première instance de la méthode.

`appDomain`\
dans AppDomain des instances de méthode.

`handle`\
à Handle pour énumérer les instances de méthode.

## <a name="remarks"></a>Notes

La méthode fournie fait partie de l' `IXCLRDataProcess` interface et correspond au 28ème emplacement de la table de méthodes virtuelles.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête :** None  
**Bibliothèque :** None  
**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Énumération CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Débogage](index.md)
- [IXCLRDataProcess, interface](ixclrdataprocess-interface.md)
