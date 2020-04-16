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
# <a name="verbose-syntax"></a><span data-ttu-id="e8703-103">Syntaxe détaillée</span><span class="sxs-lookup"><span data-stu-id="e8703-103">Verbose Syntax</span></span>

<span data-ttu-id="e8703-104">Il existe deux formes de syntaxe disponibles pour de nombreuses constructions dans la langue F: *syntaxe verbeuse* et *syntaxe légère*.</span><span class="sxs-lookup"><span data-stu-id="e8703-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="e8703-105">La syntaxe verbeuse n’est pas aussi couramment utilisée, mais a l’avantage d’être moins sensible à l’indentation.</span><span class="sxs-lookup"><span data-stu-id="e8703-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="e8703-106">La syntaxe légère est plus courte et utilise l’indentation pour signaler `begin` `end`le `in`début et la fin des constructions, plutôt que des mots clés supplémentaires comme , , et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="e8703-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="e8703-107">La syntaxe par défaut est la syntaxe légère.</span><span class="sxs-lookup"><span data-stu-id="e8703-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="e8703-108">Ce sujet décrit la syntaxe pour les constructions de F lorsque la syntaxe légère n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="e8703-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="e8703-109">La syntaxe Verbose est toujours activée, donc même si vous activez la syntaxe légère, vous pouvez toujours utiliser la syntaxe verbeux pour certaines constructions.</span><span class="sxs-lookup"><span data-stu-id="e8703-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="e8703-110">Vous pouvez désactiver la syntaxe légère en utilisant la `#light "off"` directive.</span><span class="sxs-lookup"><span data-stu-id="e8703-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="e8703-111">Tableau des constructions</span><span class="sxs-lookup"><span data-stu-id="e8703-111">Table of Constructs</span></span>

<span data-ttu-id="e8703-112">Le tableau suivant montre la syntaxe légère et verbeuse pour les constructions linguistiques de F dans des contextes où il y a une différence entre les deux formes.</span><span class="sxs-lookup"><span data-stu-id="e8703-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="e8703-113">Dans ce tableau, les&lt;&gt;supports d’angle () enferment les éléments syntaxiques fournis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e8703-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="e8703-114">Consultez la documentation de chaque construction linguistique pour obtenir des informations plus détaillées sur la syntaxe utilisée dans ces constructions.</span><span class="sxs-lookup"><span data-stu-id="e8703-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="e8703-115">Construction linguistique</span><span class="sxs-lookup"><span data-stu-id="e8703-115">Language construct</span></span></th>
<th><span data-ttu-id="e8703-116">Syntaxe légère</span><span class="sxs-lookup"><span data-stu-id="e8703-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="e8703-117">Syntaxe Verbose</span><span class="sxs-lookup"><span data-stu-id="e8703-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="e8703-118">expressions composées</span><span class="sxs-lookup"><span data-stu-id="e8703-118">compound expressions</span></span>
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

<span data-ttu-id="e8703-119">reliures `let` imbriquées</span><span class="sxs-lookup"><span data-stu-id="e8703-119">nested `let` bindings</span></span>

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
<span data-ttu-id="e8703-120">bloc de code</span><span class="sxs-lookup"><span data-stu-id="e8703-120">code block</span></span>
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
<tr><td><span data-ttu-id="e8703-121">enregistrement</span><span class="sxs-lookup"><span data-stu-id="e8703-121">record</span></span>
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
<tr><td><span data-ttu-id="e8703-122">class</span><span class="sxs-lookup"><span data-stu-id="e8703-122">class</span></span>
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
<tr><td><span data-ttu-id="e8703-123">structure</span><span class="sxs-lookup"><span data-stu-id="e8703-123">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="e8703-124">syndicat discriminé</span><span class="sxs-lookup"><span data-stu-id="e8703-124">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="e8703-125">interface</span><span class="sxs-lookup"><span data-stu-id="e8703-125">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="e8703-126">expression de l’objet</span><span class="sxs-lookup"><span data-stu-id="e8703-126">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="e8703-127">implémentation de l'interface</span><span class="sxs-lookup"><span data-stu-id="e8703-127">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="e8703-128">extension de type</span><span class="sxs-lookup"><span data-stu-id="e8703-128">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="e8703-129">module</span><span class="sxs-lookup"><span data-stu-id="e8703-129">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="e8703-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8703-130">See also</span></span>

- [<span data-ttu-id="e8703-131">Référence linguistique F</span><span class="sxs-lookup"><span data-stu-id="e8703-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="e8703-132">Directives de compilateur</span><span class="sxs-lookup"><span data-stu-id="e8703-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="e8703-133">Indications pour la mise en forme du code</span><span class="sxs-lookup"><span data-stu-id="e8703-133">Code Formatting Guidelines</span></span>](../style-guide/formatting.md)
