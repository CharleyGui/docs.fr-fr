---
title: 'IXCLRDataModule :: GetVersionId, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ff8ccf42d1131fb15d7473ae12ecefde9d55177f
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395279"
---
# <a name="ixclrdatamodulegetversionid-method"></a>IXCLRDataModule :: GetVersionId, méthode

Obtient l’identificateur de version du module.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a>Paramètres

`vid`\
à Identificateur de version du module.

## <a name="remarks"></a>Notes

La méthode fournie fait partie de l' `IXCLRDataModule` interface et correspond à l’emplacement 41e de la table de méthodes virtuelles.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête :** None  
**Bibliothèque :** None  
**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [IXCLRDataModule, interface](ixclrdatamodule-interface.md)
