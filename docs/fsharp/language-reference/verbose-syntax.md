---
title: Syntaxe détaillée
description: Apprenez la différence entre la syntaxe verbeuse et la syntaxe légère dans le langage de programmation de F.
ms.date: 05/16/2016
ms.openlocfilehash: 722807695c56beb0d681b95a78ed8cb8c1df3ddf
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463903"
---
# <a name="verbose-syntax"></a>Syntaxe détaillée

Il existe deux formes de syntaxe disponibles pour de nombreuses constructions dans la langue F: *syntaxe verbeuse* et *syntaxe légère*. La syntaxe verbeuse n’est pas aussi couramment utilisée, mais a l’avantage d’être moins sensible à l’indentation. La syntaxe légère est plus courte et utilise l’indentation pour signaler `begin` `end`le `in`début et la fin des constructions, plutôt que des mots clés supplémentaires comme , , et ainsi de suite. La syntaxe par défaut est la syntaxe légère. Ce sujet décrit la syntaxe pour les constructions de F lorsque la syntaxe légère n’est pas activée. La syntaxe Verbose est toujours activée, donc même si vous activez la syntaxe légère, vous pouvez toujours utiliser la syntaxe verbeux pour certaines constructions. Vous pouvez désactiver la syntaxe légère en utilisant la `#light "off"` directive.

## <a name="table-of-constructs"></a>Tableau des constructions

Le tableau suivant montre la syntaxe légère et verbeuse pour les constructions linguistiques de F dans des contextes où il y a une différence entre les deux formes. Dans ce tableau, les&lt;&gt;supports d’angle () enferment les éléments syntaxiques fournis par l’utilisateur. Consultez la documentation de chaque construction linguistique pour obtenir des informations plus détaillées sur la syntaxe utilisée dans ces constructions.

<table>
<tr>
<th>Construction linguistique</th>
<th>Syntaxe légère</th>
<th>Syntaxe Verbose</th>
</tr>
<tr>
<td>
expressions composées
</td>
<td>

```xml
<expression1 />
<expression2 />
```

</td><td>

```fsharp
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>

reliures `let` imbriquées

</td><td>

```fsharp
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```fsharp
let f x =
    let a = 1 in
    let b = 2 in
    x + a + b
```

</td>
</tr>
<tr><td>
bloc de code
</td><td>

```fsharp
(
    <expression1>
    <expression2>
)
```

</td><td>

```fsharp
begin
    <expression1>;
    <expression2>;
end
```

</td>
</tr>
<tr><td>
`for...do`
</td><td>

```fsharp
for counter = start to finish do
    ...
```

</td><td>

```fsharp
for counter = start to finish do
    ...
done
```

</td>
</tr>
<tr><td>
`while...do`
</td><td>

```fsharp
while <condition> do
    ...
```

</td><td>

```fsharp
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```fsharp
for var in start .. finish do
    ...
```

</td><td>

```fsharp
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```fsharp
do
    ...
```

</td><td>

```fsharp
do
    ...
in
```

</td>
</tr>
<tr><td>enregistrement
</td><td>

```fsharp
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```fsharp
type <record-name> =
    {
        <field-declarations>
    }
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>class
</td><td>

```fsharp
type <class-name>(<params>) =
    ...
```

</td><td>

```fsharp
type <class-name>(<params>) =
    class
        ...
    end
```

</td>
</tr>
<tr><td>structure</td><td>

```fsharp
[<StructAttribute>]
type <structure-name> =
    ...
```

</td><td>

```fsharp
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td>syndicat discriminé</td><td>

```fsharp
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```

</td><td>

```fsharp
type <union-name> =
    | ...
    | ...
    ...
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>interface</td><td>

```fsharp
type <interface-name> =
    ...
```

</td><td>

```fsharp
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td>expression de l’objet</td><td>

```fsharp
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```fsharp
{ new <type-name>
    with
        <value-or-member-definitions>
    end
    <interface-implementations>
}
```

</td>
</tr>
<tr><td>implémentation de l'interface</td><td>

```fsharp
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```fsharp
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>extension de type</td><td>

```fsharp
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```fsharp
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>module</td><td>

```fsharp
module <module-name> =
    ...
```

</td><td>

```fsharp
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>

## <a name="see-also"></a>Voir aussi

- [Référence linguistique F](index.md)
- [Directives de compilateur](compiler-directives.md)
- [Indications pour la mise en forme du code](../style-guide/formatting.md)
