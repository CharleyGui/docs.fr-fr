---
title: IXCLRDataMethodInstance::GetRepresentativeEntryAddress (méthode)
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 5c79e916a06e796fc87b57eb949cccda77b8a9bd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744663"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a>IXCLRDataMethodInstance::GetRepresentativeEntryAddress (méthode)

Obtient l’adresse de point d’entrée plus représentatif de la compilation native de tous les points d’entrée possibles pour une méthode.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a>Paramètres

`addr`\
[out] L’adresse du point d’entrée natif plus représentatif pour la méthode.

## <a name="remarks"></a>Notes

La méthode fournie fait partie de la [ `IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) et correspond à l’emplacement de la table de la méthode virtuelle de 19.

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête :** Aucun  
**Bibliothèque :** Aucun  
**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [Interface de IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)
