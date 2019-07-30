---
title: Abréviations de types
description: En savoir F# plus sur les abréviations de type pour donner un nom plus explicite à un type afin de faciliter la lecture du code.
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630215"
---
# <a name="type-abbreviations"></a><span data-ttu-id="e0f3d-103">Abréviations de types</span><span class="sxs-lookup"><span data-stu-id="e0f3d-103">Type Abbreviations</span></span>

<span data-ttu-id="e0f3d-104">Une *abréviation de type* est un alias ou un nom de remplacement pour un type.</span><span class="sxs-lookup"><span data-stu-id="e0f3d-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0f3d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0f3d-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="e0f3d-106">Notes</span><span class="sxs-lookup"><span data-stu-id="e0f3d-106">Remarks</span></span>

<span data-ttu-id="e0f3d-107">Vous pouvez utiliser des abréviations de type pour donner un nom plus explicite à un type, afin de rendre le code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="e0f3d-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="e0f3d-108">Vous pouvez également les utiliser pour créer un nom facile à utiliser pour un type qui est autrement lourd à écrire. En outre, vous pouvez utiliser des abréviations de type pour faciliter la modification d’un type sous-jacent sans modifier l’ensemble du code qui utilise le type.</span><span class="sxs-lookup"><span data-stu-id="e0f3d-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="e0f3d-109">Voici une abréviation de type simple.</span><span class="sxs-lookup"><span data-stu-id="e0f3d-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="e0f3d-110">L’accessibilité des abréviations de type est `public`définie par défaut sur.</span><span class="sxs-lookup"><span data-stu-id="e0f3d-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="e0f3d-111">Les abréviations de type peuvent inclure des paramètres génériques, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e0f3d-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="e0f3d-112">Dans le code précédent, `Transform` est une abréviation de type qui représente une fonction qui accepte un argument unique de n’importe quel type et qui retourne une valeur unique de ce même type.</span><span class="sxs-lookup"><span data-stu-id="e0f3d-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="e0f3d-113">Les abréviations de type ne sont pas conservées dans le code MSIL .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e0f3d-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="e0f3d-114">Par conséquent, lorsque vous utilisez F# un assembly d’un autre langage de .NET Framework, vous devez utiliser le nom de type sous-jacent pour une abréviation de type.</span><span class="sxs-lookup"><span data-stu-id="e0f3d-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="e0f3d-115">Les abréviations de type peuvent également être utilisées sur les unités de mesure.</span><span class="sxs-lookup"><span data-stu-id="e0f3d-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="e0f3d-116">Pour plus d’informations, consultez [unités de mesure](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="e0f3d-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0f3d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0f3d-117">See also</span></span>

- [<span data-ttu-id="e0f3d-118">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="e0f3d-118">F# Language Reference</span></span>](index.md)
