---
title: Syntaxe détaillée
description: 'Découvrez la différence entre la syntaxe détaillée et la syntaxe simplifiée dans le langage de programmation F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 4e1725b58c8cb67c074ba12fd4ca25ce0c000a1e
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97595175"
---
# <a name="verbose-syntax"></a>Syntaxe détaillée

Il existe deux formes de syntaxe disponibles pour de nombreuses constructions en langage F # : *syntaxe détaillée* et *syntaxe simplifiée*. La syntaxe détaillée n’est pas aussi couramment utilisée, mais elle présente l’avantage d’être moins sensible à la mise en retrait. La syntaxe simplifiée est plus petite et utilise la mise en retrait pour signaler le début et la fin des constructions, plutôt que des mots clés supplémentaires tels que `begin` , `end` , `in` , etc. La syntaxe par défaut est la syntaxe simplifiée. Cette rubrique décrit la syntaxe des constructions F # lorsque la syntaxe simplifiée n’est pas activée. La syntaxe détaillée est toujours activée, donc même si vous activez la syntaxe légère, vous pouvez toujours utiliser la syntaxe détaillée pour certaines constructions. Vous pouvez désactiver la syntaxe simplifiée à l’aide de la `#light "off"` directive.

## <a name="table-of-constructs"></a>Table de constructions

Le tableau suivant montre la syntaxe légère et détaillée pour les constructions de langage F # dans les contextes où il existe une différence entre les deux formes. Dans ce tableau, les chevrons ( &lt; &gt; ) encadrent les éléments de syntaxe fournis par l’utilisateur. Reportez-vous à la documentation de chaque construction de langage pour obtenir des informations plus détaillées sur la syntaxe utilisée dans ces constructions.

<table>
<tr>
<th>Construction de langage</th>
<th>Syntaxe simplifiée</th>
<th>Syntaxe détaillée</th>
</tr>
<tr>
<td>
expressions composées
</td>
<td>

```fsharp
<expression1>
<expression2>
```

</td><td>

```fsharp
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>

liaisons imbriquées `let`

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
<tr><td>Union discriminée</td><td>

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
<tr><td>expression d’objet</td><td>

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

- [Informations de référence sur le langage F #](index.md)
- [Directives de compilateur](compiler-directives.md)
- [Indications pour la mise en forme du code](../style-guide/formatting.md)
