---
title: 'Déclarations d’importation : mot clé open'
description: En savoir F# plus sur les déclarations d’importation et la façon dont elles spécifient un module ou un espace de noms dont vous pouvez référencer des éléments sans utiliser un nom complet.
ms.date: 04/04/2019
ms.openlocfilehash: 816bac551692c3397290f64c6267ee22e4ce90fb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630577"
---
# <a name="import-declarations-the-open-keyword"></a>Déclarations d’importation : mot clé `open`

> [!NOTE]
> Les liens des informations de référence sur les API qui figurent dans cet article pointent vers MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Une *déclaration d’importation* spécifie un module ou un espace de noms dont vous pouvez référencer des éléments sans utiliser un nom qualifié complet.

## <a name="syntax"></a>Syntaxe

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Notes

Le référencement du code à l’aide de l’espace de noms complet ou du chemin du module à chaque fois peut créer du code difficile à écrire, lire et gérer. Au lieu de cela, vous `open` pouvez utiliser le mot clé pour les modules et les espaces de noms fréquemment utilisés. ainsi, lorsque vous référencez un membre de ce module ou de cet espace de noms, vous pouvez utiliser la forme abrégée du nom au lieu du nom complet. Ce mot clé est semblable au `using` mot clé C#dans `using namespace` , en C++Visual et `Imports` dans Visual Basic.

Le module ou l’espace de noms fourni doit se trouver dans le même projet ou dans un projet ou un assembly référencé. Si ce n’est pas le cas, vous pouvez ajouter une référence au projet ou utiliser `-reference` l'`-`option de ligne de commande (ou son `-r`abréviation,). Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).

La déclaration d’importation rend les noms disponibles dans le code qui suit la déclaration, jusqu’à la fin de l’espace de noms, du module ou du fichier englobant.

Lorsque vous utilisez plusieurs déclarations d’importation, elles doivent apparaître sur des lignes distinctes.

Le code suivant illustre l’utilisation du `open` mot clé pour simplifier le code.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

Le F# compilateur n’émet pas d’erreur ou d’avertissement quand des ambiguïtés se produisent lorsque le même nom se trouve dans plusieurs modules ou espaces de noms ouverts. Quand des ambiguïtés se F# produisent, donne la préférence au module ou à l’espace de noms récemment ouvert. Par exemple, dans le code suivant, `empty` signifie `Seq.empty`, même si `empty` se trouve à la fois `List` dans `Seq` les modules et.

```fsharp
open List
open Seq
printfn "%A" empty
```

Par conséquent, soyez vigilant lorsque vous ouvrez des modules ou des espaces `List` de `Seq` noms tels que ou qui contiennent des membres qui ont des noms identiques; à la place, envisagez d’utiliser les noms qualifiés. Vous devez éviter toute situation dans laquelle le code dépend de l’ordre des déclarations d’importation.

## <a name="namespaces-that-are-open-by-default"></a>Espaces de noms ouverts par défaut

Certains espaces de noms sont si souvent utilisés F# dans le code qu’ils sont ouverts implicitement sans qu’une déclaration d’importation explicite soit nécessaire. Le tableau suivant répertorie les espaces de noms qui sont ouverts par défaut.

|Espace de noms|Description|
|---------|-----------|
|`Microsoft.FSharp.Core`|Contient des F# définitions de type de base pour les types intégrés `int` tels `float`que et.|
|`Microsoft.FSharp.Core.Operators`|Contient des opérations arithmétiques de `+` base `*`telles que et.|
|`Microsoft.FSharp.Collections`|Contient des classes de collection immuables `List` telles `Array`que et.|
|`Microsoft.FSharp.Control`|Contient des types pour les constructions de contrôle telles que l’évaluation différée et les flux de travail asynchrones.|
|`Microsoft.FSharp.Text`|Contient des fonctions pour les e/s mises `printf` en forme, telles que la fonction.|

## <a name="autoopen-attribute"></a>Attribut Open

Vous pouvez appliquer l' `AutoOpen` attribut à un assembly si vous souhaitez ouvrir automatiquement un espace de noms ou un module lorsque l’assembly est référencé. Vous pouvez également appliquer l' `AutoOpen` attribut à un module pour ouvrir automatiquement ce module lors de l’ouverture du module ou de l’espace de noms parent. Pour plus d’informations, consultez [Core. AutoOpenAttribute, classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).

## <a name="requirequalifiedaccess-attribute"></a>Attribut RequireQualifiedAccess

Certains modules, enregistrements ou types d’Union peuvent spécifier l' `RequireQualifiedAccess` attribut. Lorsque vous référencez des éléments de ces modules, enregistrements ou unions, vous devez utiliser un nom qualifié, que vous incluiez ou non une déclaration d’importation. Si vous utilisez cet attribut de façon stratégique sur des types qui définissent des noms couramment utilisés, vous évitez les conflits de noms et rendez le code plus résilient aux modifications dans les bibliothèques. Pour plus d’informations, consultez [Core. RequireQualifiedAccessAttribute (, classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Espaces de noms](namespaces.md)
- [Modules](modules.md)
