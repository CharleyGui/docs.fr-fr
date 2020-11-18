---
title: Chaînes interpolées
description: 'En savoir plus sur les chaînes interpolées, une forme spéciale de chaîne qui vous permet d’incorporer des expressions F # directement à l’intérieur de celles-ci.'
ms.date: 11/12/2020
ms.openlocfilehash: a49d4e743306fd9bdabb1e019ec4e6c77e0e1f5a
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688601"
---
# <a name="interpolated-strings"></a><span data-ttu-id="c9ef2-103">Chaînes interpolées</span><span class="sxs-lookup"><span data-stu-id="c9ef2-103">Interpolated strings</span></span>

<span data-ttu-id="c9ef2-104">Les chaînes interpolées sont des [chaînes](strings.md) qui vous permettent d’incorporer des expressions F # dans celles-ci.</span><span class="sxs-lookup"><span data-stu-id="c9ef2-104">Interpolated strings are [strings](strings.md) that allow you to embed F# expressions into them.</span></span> <span data-ttu-id="c9ef2-105">Elles sont utiles dans un large éventail de scénarios où la valeur d’une chaîne peut changer selon le résultat d’une valeur ou d’une expression.</span><span class="sxs-lookup"><span data-stu-id="c9ef2-105">They are helpful in a wide range of scenarios where the value of a string may change based on the result of a value or expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9ef2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9ef2-106">Syntax</span></span>

```fsharp
$"string-text {expr}"
$"string-text %format-specifier{expr}"
$"""string-text {"embedded string literal"}"""
```

## <a name="remarks"></a><span data-ttu-id="c9ef2-107">Notes</span><span class="sxs-lookup"><span data-stu-id="c9ef2-107">Remarks</span></span>

<span data-ttu-id="c9ef2-108">Les chaînes interpolées vous permettent d’écrire du code dans des « trous » à l’intérieur d’un littéral de chaîne.</span><span class="sxs-lookup"><span data-stu-id="c9ef2-108">Interpolated strings let you write code in "holes" inside of a string literal.</span></span> <span data-ttu-id="c9ef2-109">Voici un exemple de base :</span><span class="sxs-lookup"><span data-stu-id="c9ef2-109">Here's a basic example:</span></span>

```fsharp
let name = "Phillip"
let age = 30
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

<span data-ttu-id="c9ef2-110">Le contenu entre chaque `{}` paire d’accolades peut être n’importe quelle expression F #.</span><span class="sxs-lookup"><span data-stu-id="c9ef2-110">The contents in between each `{}` brace pair can be any F# expression.</span></span>

<span data-ttu-id="c9ef2-111">Pour échapper à une `{}` paire d’accolades, écrivez deux d’entre eux comme suit :</span><span class="sxs-lookup"><span data-stu-id="c9ef2-111">To escape a `{}` brace pair, write two of them like so:</span></span>

```fsharp
let str = $"A pair of braces: {{}}"
// "A pair of braces: {}"
```

## <a name="typed-interpolated-strings"></a><span data-ttu-id="c9ef2-112">Chaînes interpolées typées</span><span class="sxs-lookup"><span data-stu-id="c9ef2-112">Typed interpolated strings</span></span>

<span data-ttu-id="c9ef2-113">Les chaînes interpolées peuvent également avoir des spécificateurs de format F # pour appliquer le type safe.</span><span class="sxs-lookup"><span data-stu-id="c9ef2-113">Interpolated strings can also have F# format specifiers to enforce type safey.</span></span>

```fsharp
let name = "Phillip"
let age = 30

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

<span data-ttu-id="c9ef2-114">Dans l’exemple précédent, le code passe par erreur la `age` valeur où `name` doit être, et vice/versa.</span><span class="sxs-lookup"><span data-stu-id="c9ef2-114">In the previous example, the code mistakenly passes the `age` value where `name` should be, and vice/versa.</span></span> <span data-ttu-id="c9ef2-115">Étant donné que les chaînes interpolées utilisent des spécificateurs de format, il s’agit d’une erreur de compilation au lieu d’un bogue de Runtime discret.</span><span class="sxs-lookup"><span data-stu-id="c9ef2-115">Because the interpolated strings use format specifiers, this is a compile error instead of a subtle runtime bug.</span></span>

<span data-ttu-id="c9ef2-116">Tous les spécificateurs de format couverts dans la [mise en forme de texte en clair](plaintext-formatting.md) sont valides dans une chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="c9ef2-116">All format specifiers covered in [plaintext formatting](plaintext-formatting.md) are valid inside of an interpolated string.</span></span>

## <a name="verbatim-interpolated-strings"></a><span data-ttu-id="c9ef2-117">Chaînes interpolées Verbatim</span><span class="sxs-lookup"><span data-stu-id="c9ef2-117">Verbatim interpolated strings</span></span>

<span data-ttu-id="c9ef2-118">F # prend en charge les chaînes interpolées Verbatim avec des guillemets triples afin que vous puissiez incorporer des littéraux de chaîne.</span><span class="sxs-lookup"><span data-stu-id="c9ef2-118">F# supports verbatim interpolated strings with triple quotes so that you can embed string literals.</span></span>

```fsharp
let age = 30

printfn $"""Name: {"Phillip"}, Age: %d{age}"""
```

## <a name="aligning-expressions-in-interpolated-strings"></a><span data-ttu-id="c9ef2-119">Alignement d’expressions dans des chaînes interpolées</span><span class="sxs-lookup"><span data-stu-id="c9ef2-119">Aligning expressions in interpolated strings</span></span>

<span data-ttu-id="c9ef2-120">Vous pouvez aligner les expressions à gauche ou à droite à l’intérieur des chaînes interpolées avec `|` et une spécification du nombre d’espaces.</span><span class="sxs-lookup"><span data-stu-id="c9ef2-120">You can left-align or right-align expressions inside interpolated strings with `|` and a specification of how many spaces.</span></span> <span data-ttu-id="c9ef2-121">La chaîne interpolée suivante aligne les expressions de gauche et de droite à gauche et à droite, respectivement, sur 7 espaces.</span><span class="sxs-lookup"><span data-stu-id="c9ef2-121">The following interpolated string aligns the left and right expressions to the left and right, respectively, by 7  spaces.</span></span>

```fsharp
printfn $"""|{"Left",-7}|{"Right",7}|"""
// |Left   |  Right|
```

## <a name="interpolated-strings-and-formattablestring-formatting"></a><span data-ttu-id="c9ef2-122">Chaînes interpolées et `FormattableString` mise en forme</span><span class="sxs-lookup"><span data-stu-id="c9ef2-122">Interpolated strings and `FormattableString` formatting</span></span>

<span data-ttu-id="c9ef2-123">Vous pouvez également appliquer une mise en forme conforme aux règles pour <xref:System.FormattableString> :</span><span class="sxs-lookup"><span data-stu-id="c9ef2-123">You can also apply formatting that adheres to the rules for <xref:System.FormattableString>:</span></span>

```fsharp
let speedOfLight = 299792.458
printfn $"The speed of light is {speedOfLight:N3} km/s."
// "The speed of light is 299,792.458 km/s."
```

<span data-ttu-id="c9ef2-124">En outre, une chaîne interpolée peut également être typechecked comme un <xref:System.FormattableString> via une annotation de type :</span><span class="sxs-lookup"><span data-stu-id="c9ef2-124">Additionally, an interpolated string can also be typechecked as a <xref:System.FormattableString> via a type annotation:</span></span>

```fsharp
let frmtStr = $"The speed of light is {speedOfLight:N3} km/s." : FormattableString
// Type: FormattableString
// The speed of light is 299,792.458 km/s.
```

<span data-ttu-id="c9ef2-125">Notez que l’annotation de type doit se trouver sur l’expression de chaîne interpolée elle-même.</span><span class="sxs-lookup"><span data-stu-id="c9ef2-125">Note that the type annotation must be on the interpolated string expression itself.</span></span> <span data-ttu-id="c9ef2-126">F # ne convertit pas implicitement une chaîne interpolée en <xref:System.FormattableString> .</span><span class="sxs-lookup"><span data-stu-id="c9ef2-126">F# does not implicitly convert an interpolated string into a <xref:System.FormattableString>.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9ef2-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9ef2-127">See also</span></span>

* [<span data-ttu-id="c9ef2-128">Chaînes</span><span class="sxs-lookup"><span data-stu-id="c9ef2-128">Strings</span></span>](strings.md)
