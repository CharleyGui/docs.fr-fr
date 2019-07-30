---
title: Copie et mise à jour des expressions d’enregistrement
description: Découvrez comment écrire une «copie et une expression de mise à jour» qui copie un enregistrement ou un enregistrement anonyme existant, met à jour les champs spécifiés et retourne l’enregistrement ou l’enregistrement anonyme mis à jour.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: dfb20a6ff8282ae5988772cc0f0841db23aad942
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630381"
---
# <a name="copy-and-update-record-expressions"></a>Copie et mise à jour des expressions d’enregistrement

Une *expression d’enregistrement de copie et de mise à jour* est une expression qui copie un enregistrement existant, met à jour les champs spécifiés et retourne l’enregistrement mis à jour.

## <a name="syntax"></a>Syntaxe

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Notes

Par défaut, les enregistrements et les enregistrements anonymes sont immuables, ce qui signifie qu’il n’existe pas de mise à jour d’un enregistrement existant. Pour créer un enregistrement mis à jour, tous les champs d’un enregistrement doivent être spécifiés à nouveau. Pour simplifier cette tâche, vous pouvez utiliser une *expression de copie et de mise à jour* . Cette expression prend un enregistrement existant, crée un nouveau du même type en utilisant les champs spécifiés de l’expression et le champ manquant spécifié par l’expression.

Cela peut être utile lorsque vous devez copier un enregistrement existant et éventuellement modifier certaines valeurs de champ.

Prenons l’exemple d’un enregistrement nouvellement créé.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Si vous mettez à jour uniquement le champ de cet enregistrement, vous pouvez utiliser l' *expression d’enregistrement copier et mettre à jour* comme suit:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Voir aussi

- [Enregistrements](records.md)
- [Enregistrements anonymes](anonymous-records.md)
- [Informations de référence du langage F#](index.md)
