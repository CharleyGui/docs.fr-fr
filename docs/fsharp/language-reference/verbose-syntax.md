---
title: Syntaxe détaillée
description: Découvrez la différence entre la syntaxe détaillée et la syntaxe simplifiée dans le F# langage de programmation.
ms.date: 05/16/2016
ms.openlocfilehash: 575585b201acc1366980cfc5cf523c4117259084
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421177"
---
# <a name="verbose-syntax"></a><span data-ttu-id="c7316-103">Syntaxe détaillée</span><span class="sxs-lookup"><span data-stu-id="c7316-103">Verbose Syntax</span></span>

<span data-ttu-id="c7316-104">Il existe deux formes de syntaxe disponibles pour de nombreuses constructions dans le F# langage : la *syntaxe détaillée* et la *syntaxe simplifiée*.</span><span class="sxs-lookup"><span data-stu-id="c7316-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="c7316-105">La syntaxe détaillée n’est pas aussi couramment utilisée, mais elle présente l’avantage d’être moins sensible à la mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="c7316-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="c7316-106">La syntaxe simplifiée est plus petite et utilise la mise en retrait pour signaler le début et la fin des constructions, plutôt que des mots clés supplémentaires comme `begin`, `end`, `in`, etc.</span><span class="sxs-lookup"><span data-stu-id="c7316-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="c7316-107">La syntaxe par défaut est la syntaxe simplifiée.</span><span class="sxs-lookup"><span data-stu-id="c7316-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="c7316-108">Cette rubrique décrit la syntaxe des F# constructions lorsque la syntaxe simplifiée n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="c7316-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="c7316-109">La syntaxe détaillée est toujours activée, donc même si vous activez la syntaxe légère, vous pouvez toujours utiliser la syntaxe détaillée pour certaines constructions.</span><span class="sxs-lookup"><span data-stu-id="c7316-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="c7316-110">Vous pouvez désactiver la syntaxe simplifiée à l’aide de la directive `#light "off"`.</span><span class="sxs-lookup"><span data-stu-id="c7316-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="c7316-111">Table de constructions</span><span class="sxs-lookup"><span data-stu-id="c7316-111">Table of Constructs</span></span>

<span data-ttu-id="c7316-112">Le tableau suivant montre la syntaxe légère et détaillée pour F# les constructions de langage dans les contextes où il existe une différence entre les deux formes.</span><span class="sxs-lookup"><span data-stu-id="c7316-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="c7316-113">Dans ce tableau, les chevrons (&lt;&gt;) encadrent les éléments de syntaxe fournis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c7316-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="c7316-114">Reportez-vous à la documentation de chaque construction de langage pour obtenir des informations plus détaillées sur la syntaxe utilisée dans ces constructions.</span><span class="sxs-lookup"><span data-stu-id="c7316-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="c7316-115">Construction de langage</span><span class="sxs-lookup"><span data-stu-id="c7316-115">Language construct</span></span></th>
<th><span data-ttu-id="c7316-116">Syntaxe simplifiée</span><span class="sxs-lookup"><span data-stu-id="c7316-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="c7316-117">Syntaxe détaillée</span><span class="sxs-lookup"><span data-stu-id="c7316-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="c7316-118">expressions composées</span><span class="sxs-lookup"><span data-stu-id="c7316-118">compound expressions</span></span>
</td>
<td>

```xml
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

<span data-ttu-id="c7316-119">liaisons de `let` imbriquées</span><span class="sxs-lookup"><span data-stu-id="c7316-119">nested `let` bindings</span></span>

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
<span data-ttu-id="c7316-120">bloc de code</span><span class="sxs-lookup"><span data-stu-id="c7316-120">code block</span></span>
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
<tr><td><span data-ttu-id="c7316-121">Enregistrement</span><span class="sxs-lookup"><span data-stu-id="c7316-121">record</span></span>
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
<tr><td><span data-ttu-id="c7316-122">classe</span><span class="sxs-lookup"><span data-stu-id="c7316-122">class</span></span>
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
<tr><td><span data-ttu-id="c7316-123">structure</span><span class="sxs-lookup"><span data-stu-id="c7316-123">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="c7316-124">Union discriminée</span><span class="sxs-lookup"><span data-stu-id="c7316-124">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="c7316-125">interface</span><span class="sxs-lookup"><span data-stu-id="c7316-125">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="c7316-126">expression d’objet</span><span class="sxs-lookup"><span data-stu-id="c7316-126">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="c7316-127">implémentation de l'interface</span><span class="sxs-lookup"><span data-stu-id="c7316-127">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="c7316-128">extension de type</span><span class="sxs-lookup"><span data-stu-id="c7316-128">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="c7316-129">module</span><span class="sxs-lookup"><span data-stu-id="c7316-129">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="c7316-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7316-130">See also</span></span>

- [<span data-ttu-id="c7316-131">Informations de référence sur le langage F#</span><span class="sxs-lookup"><span data-stu-id="c7316-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c7316-132">Directives de compilateur</span><span class="sxs-lookup"><span data-stu-id="c7316-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="c7316-133">Indications pour la mise en forme du code</span><span class="sxs-lookup"><span data-stu-id="c7316-133">Code Formatting Guidelines</span></span>](../style-guide/formatting.md)
