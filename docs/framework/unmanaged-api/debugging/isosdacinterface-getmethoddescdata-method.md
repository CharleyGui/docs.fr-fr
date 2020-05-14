---
title: 'ISOSDacInterface :: GetMethodDescData, méthode'
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e4c44379d9db0f5e98f3ca66ec0486961ec2df3a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396944"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>ISOSDacInterface :: GetMethodDescData, méthode

Obtient les données pour le pointeur MethodDesc donné.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a>Paramètres

`methodDesc`\
dans Adresse du MethodDesc.

`ip`\
dans Adresse IP de la méthode.

`data`\
à Données associées à MethodDesc, telles qu’elles sont retournées par les API internes.

`cRevertedRejitVersions`\
à Nombre de versions de ReJIT restaurées.

`rgRevertedRejitData`\
à Les données associées aux versions ReJIT restaurées sont retournées par les API internes.

`pcNeededRevertedRejitData`\
à Nombre d’octets requis pour stocker les données associées aux versions ReJit restaurées.

## <a name="remarks"></a>Notes

La méthode fournie fait partie de l' `ISOSDacInterface` interface et correspond à l’emplacement du 21e de la table de méthodes virtuelles. Pour pouvoir les utiliser, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) doit être défini en tant qu’entier non signé 64 bits.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête :** None  
**Bibliothèque :** None  
**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [ISOSDacInterface, interface](isosdacinterface-interface.md)
