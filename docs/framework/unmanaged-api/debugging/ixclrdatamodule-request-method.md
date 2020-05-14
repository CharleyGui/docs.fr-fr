---
title: 'IXCLRDataModule :: Request, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 44ee4fc7fc2368b65f6f2fffe6ac239beddc6293
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395265"
---
# <a name="ixclrdatamodulerequest-method"></a>IXCLRDataModule :: Request, méthode

Demandes de remplissage de la mémoire tampon donnée avec les données du module.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a>Paramètres

`reqCode`\
dans Type de demande à envoyer.

`inBufferSize`\
[in] taille de la mémoire tampon d’entrée à passer.

`inBuffer`\
[in, size_is (inBufferSize)] Pointeur de mémoire tampon pour les données brutes à envoyer dans la demande.

`outBufferSize`\
dans Taille de la mémoire tampon de sortie.

`outBuffer`\
[out, size_is (outBufferSize)] Pointeur de la mémoire tampon à utiliser pour stocker la réponse à la demande.

## <a name="remarks"></a>Notes

La méthode fournie fait partie de l' `IXCLRDataModule` interface et correspond à l’emplacement 37th de la table de méthodes virtuelles.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).
**En-tête :** **Bibliothèque None :** aucune **.NET Framework versions :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [IXCLRDataModule, interface](ixclrdatamodule-interface.md)
