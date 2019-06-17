---
title: Copie et mise à jour des expressions d’enregistrement
description: Découvrez comment écrire une « copie et mise à jour expression » qui copie un enregistrement existant ou enregistrement anonyme, les mises à jour spécifié de champs et retourne l’enregistrement mis à jour ou anonyme.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: d16f5ca337047ab2eecc8828b21d8a423bf39a1f
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041733"
---
# <a name="copy-and-update-record-expressions"></a>Copie et mise à jour des expressions d’enregistrement

Un *copier et mettre à jour d’expression d’enregistrement* est une expression qui copie un enregistrement existant, met à jour les champs spécifiés et retourne l’enregistrement mis à jour.

## <a name="syntax"></a>Syntaxe

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Notes

Enregistrements et des enregistrements anonymes sont immuables par défaut, pour qu’il n’y a aucune mise à jour un enregistrement existant possible. Pour créer un enregistrement mis à jour tous les champs d’un enregistrement devrait être spécifiés à nouveau. Pour simplifier cette tâche un *copier et mettre à jour expression* peut être utilisé. Cette expression prend un enregistrement existant, crée un nouveau du même type à l’aide des champs spécifiés à partir de l’expression et le champ manquant spécifié par l’expression.

Cela peut être utile lorsque vous devez copier un enregistrement existant et éventuellement modifier certaines valeurs de champ.

Prenez par exemple un enregistrement qui vient d’être créé.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Si vous deviez mettre à jour uniquement sur le champ de cet enregistrement, vous pouvez utiliser la *copier et mettre à jour d’expression d’enregistrement* comme suit :

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Voir aussi

- [Enregistrements](records.md)
- [Enregistrements anonymes](anonymous-records.md)
- [Informations de référence du langage F#](index.md)
