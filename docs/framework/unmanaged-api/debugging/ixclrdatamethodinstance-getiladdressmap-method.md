---
title: IXCLRDataMethodInstance::GetILAddressMap Method
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance::GetILAddressMap Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method
helpviewer.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 66e4768acff7ab735c6ac9e8f8f51a9511f7e371
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744681"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a>IXCLRDataMethodInstance::GetILAddressMap Method

Obtient le langage intermédiaire aux informations de mappage d’adresse.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a>Paramètres

`mapLen`\
[in] La longueur du tableau des mappages fournis.

`mapNeeded`\
[out] Le nombre d’entrées de mappage dont a besoin de la méthode.

`maps`\
[out, size_is(mapLen)] Le tableau pour stocker les entrées de mappage.

## <a name="remarks"></a>Notes

La méthode fournie fait partie de la `IXCLRDataMethodInstance` interface et correspond à l’emplacement de la table de la méthode virtuelle de 14.

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête :** Aucun  
**Bibliothèque :** Aucun  
**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [Interface de IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)
