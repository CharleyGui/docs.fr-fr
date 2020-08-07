---
title: "Déclarations d'importation : mot clé open"
description: 'En savoir plus sur les déclarations d’importation F # et la façon dont elles spécifient un module ou un espace de noms dont vous pouvez référencer des éléments sans utiliser un nom complet.'
ms.date: 04/04/2019
ms.openlocfilehash: 2b88427ca92212fb4a7598447dd1a5e12061093a
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855086"
---
# <a name="import-declarations-the-open-keyword"></a>Déclarations d’importation : `open` mot clé

Une *déclaration d’importation* spécifie un module ou un espace de noms dont vous pouvez référencer des éléments sans utiliser un nom qualifié complet.

## <a name="syntax"></a>Syntaxe

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Notes

> [!NOTE]
> La référence de l’API docs.microsoft.com pour F # n’est pas terminée. Si vous rencontrez des liens rompus, consultez plutôt [la documentation de la bibliothèque principale F #](https://fsharp.github.io/fsharp-core-docs/) .

Le référencement du code à l’aide de l’espace de noms complet ou du chemin du module à chaque fois peut créer du code difficile à écrire, lire et gérer. Au lieu de cela, vous pouvez utiliser le `open` mot clé pour les modules et les espaces de noms fréquemment utilisés. ainsi, lorsque vous référencez un membre de ce module ou de cet espace de noms, vous pouvez utiliser la forme abrégée du nom au lieu du nom complet. Ce mot clé est semblable au `using` mot clé en C#, `using namespace` dans Visual C++ et `Imports` dans Visual Basic.

Le module ou l’espace de noms fourni doit se trouver dans le même projet ou dans un projet ou un assembly référencé. Si ce n’est pas le cas, vous pouvez ajouter une référence au projet ou utiliser l' `-reference` option de ligne de commande (ou son abréviation, `-r` ). Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).

La déclaration d’importation rend les noms disponibles dans le code qui suit la déclaration, jusqu’à la fin de l’espace de noms, du module ou du fichier englobant.

Lorsque vous utilisez plusieurs déclarations d’importation, elles doivent apparaître sur des lignes distinctes.

Le code suivant illustre l’utilisation du `open` mot clé pour simplifier le code.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

Le compilateur F # n’émet pas d’erreur ni d’avertissement quand des ambiguïtés se produisent lorsque le même nom se trouve dans plusieurs modules ou espaces de noms ouverts. Quand des ambiguïtés se produisent, F # donne la préférence au module ou à l’espace de noms le plus récemment ouvert. Par exemple, dans le code suivant, `empty` signifie `Seq.empty` , même si `empty` se trouve à la fois dans les `List` `Seq` modules et.

```fsharp
open List
open Seq
printfn "%A" empty
```

Par conséquent, soyez vigilant lorsque vous ouvrez des modules ou des espaces de noms tels que `List` ou `Seq` qui contiennent des membres qui ont des noms identiques ; à la place, envisagez d’utiliser les noms qualifiés. Vous devez éviter toute situation dans laquelle le code dépend de l’ordre des déclarations d’importation.

## <a name="namespaces-that-are-open-by-default"></a>Espaces de noms ouverts par défaut

Certains espaces de noms sont si souvent utilisés dans du code F # qu’ils sont ouverts implicitement sans avoir besoin d’une déclaration d’importation explicite. Le tableau suivant répertorie les espaces de noms qui sont ouverts par défaut.

|Espace de noms|Description|
|---------|-----------|
|`Microsoft.FSharp.Core`|Contient des définitions de type F # de base pour les types intégrés tels que `int` et `float` .|
|`Microsoft.FSharp.Core.Operators`|Contient des opérations arithmétiques de base telles que `+` et `*` .|
|`Microsoft.FSharp.Collections`|Contient des classes de collection immuables telles que `List` et `Array` .|
|`Microsoft.FSharp.Control`|Contient des types pour les constructions de contrôle telles que l’évaluation différée et les flux de travail asynchrones.|
|`Microsoft.FSharp.Text`|Contient des fonctions pour les e/s mises en forme, telles que la `printf` fonction.|

## <a name="autoopen-attribute"></a>Attribut Open

Vous pouvez appliquer l' `AutoOpen` attribut à un assembly si vous souhaitez ouvrir automatiquement un espace de noms ou un module lorsque l’assembly est référencé. Vous pouvez également appliquer l' `AutoOpen` attribut à un module pour ouvrir automatiquement ce module lors de l’ouverture du module ou de l’espace de noms parent. Pour plus d’informations, consultez [Core. AutoOpenAttribute, classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).

## <a name="requirequalifiedaccess-attribute"></a>Attribut RequireQualifiedAccess

Certains modules, enregistrements ou types d’Union peuvent spécifier l' `RequireQualifiedAccess` attribut. Lorsque vous référencez des éléments de ces modules, enregistrements ou unions, vous devez utiliser un nom qualifié, que vous incluiez ou non une déclaration d’importation. Si vous utilisez cet attribut de façon stratégique sur des types qui définissent des noms couramment utilisés, vous évitez les conflits de noms et rendez le code plus résilient aux modifications dans les bibliothèques. Pour plus d’informations, consultez [Core. RequireQualifiedAccessAttribute (, classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Espaces de noms](namespaces.md)
- [Modules](modules.md)
