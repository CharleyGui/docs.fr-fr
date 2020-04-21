---
title: Copie et mise à jour des expressions d’enregistrement
description: Découvrez comment écrire une « expression de copie et mise à jour » qui copie un enregistrement existant ou un enregistrement anonyme, met à jour les champs spécifiés et renvoie l’enregistrement mis à jour ou l’enregistrement anonyme.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: bec3e0ac2fb34e358b199c509c4599b55d7bf35e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739284"
---
# <a name="copy-and-update-record-expressions"></a>Copie et mise à jour des expressions d’enregistrement

Une *expression d’enregistrement de copie et de mise à jour* est une expression qui copie un enregistrement existant, met à jour les champs spécifiés et renvoie l’enregistrement mis à jour.

## <a name="syntax"></a>Syntaxe

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Notes

Les enregistrements et les enregistrements anonymes sont immuables par défaut, il n’est donc pas possible de mettre à jour un enregistrement existant. Pour créer un enregistrement mis à jour, tous les champs d’un enregistrement devraient être spécifiés à nouveau. Pour simplifier cette tâche, une *copie et une mise à jour de l’expression* peuvent être utilisées. Cette expression prend un enregistrement existant, crée un nouveau du même type en utilisant des champs spécifiés de l’expression et le champ manquant spécifié par l’expression.

Cela peut être utile lorsque vous devez copier un enregistrement existant, et peut-être changer certaines des valeurs de champ.

Prenez par exemple un disque nouvellement créé.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Pour mettre à jour seulement deux champs de cet enregistrement, vous pouvez utiliser la *copie et mettre à jour l’expression d’enregistrement*:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Voir aussi

- [Dossiers](records.md)
- [Enregistrements anonymes](anonymous-records.md)
- [Référence linguistique F](index.md)
