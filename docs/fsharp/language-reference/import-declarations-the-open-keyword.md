---
title: "Déclarations d'importation : mot clé open"
description: Renseignez-vous sur les déclarations d’importation de F et comment elles spécifient un module ou un espace de nom dont vous pouvez référencer les éléments sans utiliser un nom entièrement qualifié.
ms.date: 04/04/2019
ms.openlocfilehash: 0baef27c7dc3181b9da0defb1c793fec04269c09
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021532"
---
# <a name="import-declarations-the-open-keyword"></a>Déclarations d’importation : mot clé `open`

> [!NOTE]
> Les liens des informations de référence sur les API qui figurent dans cet article pointent vers MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Une *déclaration d’importation* spécifie un module ou un espace de nom dont vous pouvez référencer les éléments sans utiliser un nom entièrement qualifié.

## <a name="syntax"></a>Syntaxe

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Notes

Le référencement du code en utilisant l’espace de nom ou le parcours du module entièrement qualifié à chaque fois peut créer du code qui est difficile à écrire, lire et maintenir. Au lieu de `open` cela, vous pouvez utiliser le mot clé pour les modules fréquemment utilisés et les espaces de noms de sorte que lorsque vous référencez un membre de ce module ou l’espace de nom, vous pouvez utiliser la forme courte du nom au lieu du nom entièrement qualifié. Ce mot clé `using` est similaire au `using namespace` mot clé dans `Imports` C, dans Visual CMD et dans Visual Basic.

Le module ou l’espace de nom fourni doit être dans le même projet ou dans un projet ou un assemblage référencé. Si ce n’est pas le cas, vous `-reference` pouvez ajouter une référence au projet, `-r`ou utiliser l’option de ligne de commande (ou son abréviation, ). Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).

La déclaration d’importation met les noms disponibles dans le code qui suit la déclaration, jusqu’à la fin de l’espace de nom, du module ou du fichier.

Lorsque vous utilisez plusieurs déclarations d’importation, elles doivent apparaître sur des lignes distinctes.

Le code suivant affiche `open` l’utilisation du mot clé pour simplifier le code.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

Le compilateur F n’émet pas d’erreur ou d’avertissement lorsque des ambiguïtés se produisent lorsque le même nom se produit dans plus d’un module ou un espace nom ouvert. Lorsque des ambiguïtés se produisent, Fmd donne la préférence au module ou à l’espace de nom plus récemment ouvert. Par exemple, dans le `empty` `Seq.empty`code suivant, signifie, même si est `empty` situé à la fois dans les `List` deux et `Seq` les modules.

```fsharp
open List
open Seq
printfn "%A" empty
```

Par conséquent, soyez prudent lorsque vous ouvrez `List` `Seq` des modules ou des espaces de nom tels que ou qui contiennent des membres qui ont des noms identiques; au lieu de cela, envisager d’utiliser les noms qualifiés. Vous devez éviter toute situation dans laquelle le code dépend de l’ordre des déclarations d’importation.

## <a name="namespaces-that-are-open-by-default"></a>Espaces de noms qui sont ouverts par défaut

Certains espaces nominatifs sont si fréquemment utilisés dans le code F qu’ils sont ouverts implicitement sans avoir besoin d’une déclaration d’importation explicite. Le tableau suivant affiche les espaces nominaux qui sont ouverts par défaut.

|Espace de noms|Description|
|---------|-----------|
|`Microsoft.FSharp.Core`|Contient des définitions de type FMD `int` de `float`base pour les types intégrés tels que et .|
|`Microsoft.FSharp.Core.Operators`|Contient des opérations arithmétiques de base telles que `+` et `*`.|
|`Microsoft.FSharp.Collections`|Contient des classes de `List` collecte `Array`immuables telles que et .|
|`Microsoft.FSharp.Control`|Contient des types pour les constructions de contrôle telles que l’évaluation paresseuse et les flux de travail asynchrones.|
|`Microsoft.FSharp.Text`|Contient des fonctions pour IO `printf` formaté, telles que la fonction.|

## <a name="autoopen-attribute"></a>Attribut AutoOpen

Vous pouvez `AutoOpen` appliquer l’attribut à un assemblage si vous souhaitez ouvrir automatiquement un espace de nom ou un module lorsque l’assemblage est référencé. Vous pouvez également `AutoOpen` appliquer l’attribut à un module pour ouvrir automatiquement ce module lorsque le module parent ou l’espace de nom est ouvert. Pour plus d’informations, voir [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).

## <a name="requirequalifiedaccess-attribute"></a>Exiger Un attribut d’access de qualification

Certains modules, enregistrements ou types `RequireQualifiedAccess` de syndicats peuvent spécifier l’attribut. Lorsque vous faites référence à des éléments de ces modules, dossiers ou syndicats, vous devez utiliser un nom qualifié, que vous incluiez ou non une déclaration d’importation. Si vous utilisez cet attribut stratégiquement sur les types qui définissent les noms couramment utilisés, vous aidez à éviter les collisions de noms et ainsi rendre le code plus résistant aux changements dans les bibliothèques. Pour plus d’informations, voir [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).

## <a name="see-also"></a>Voir aussi

- [Référence linguistique F](index.md)
- [Espaces de noms](namespaces.md)
- [Modules](modules.md)
