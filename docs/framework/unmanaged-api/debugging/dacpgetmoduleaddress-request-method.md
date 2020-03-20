---
title: DacpGetModuleAddress::Méthode de demande
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 6850dc256a70e0c0343104b3904e9eda62d11e7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179202"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>DacpGetModuleAddress::Méthode de demande

Effectue une demande de remplir la structure de la structure donnée runtime.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>Paramètres

`pDataModule`\
[dans] Un pointeur vers le module de données sur les semences.

## <a name="remarks"></a>Notes 

Cette structure vit à l’intérieur du temps d’exécution et n’est pas exposée à travers des en-têtes ou des fichiers de bibliothèque. Pour l’utiliser, le moyen le plus simple est d’imiter la mise en œuvre:

- Retournez la valeur obtenue `Request` en `IXCLRDataModule*` appelant la méthode sur le paramètre avec les paramètres suivants :`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête:** Aucune **bibliothèque:** Aucun  
**.NET Versions-cadre:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [DacpGetModuleAddress Interface](dacpgetmoduleaddress-structure.md)
