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
ms.openlocfilehash: 3c18fc5c947cbb89fc4e9aed60d3cedcbe22d749
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420810"
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

## <a name="requirements"></a>Conditions requises

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).
**En-tête :** **Bibliothèque None :** aucune **.NET Framework versions :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [IXCLRDataModule, interface](ixclrdatamodule-interface.md)
