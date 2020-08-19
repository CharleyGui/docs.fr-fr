---
title: "Déclarations d'importation : mot clé open"
description: 'En savoir plus sur les déclarations d’importation F # et la façon dont elles spécifient un module ou un espace de noms dont vous pouvez référencer des éléments sans utiliser un nom complet.'
ms.date: 08/15/2020
ms.openlocfilehash: 6420df071f86159c44606c2710331d5f587023cc
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557605"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="fbe09-103">Déclarations d’importation : `open` mot clé</span><span class="sxs-lookup"><span data-stu-id="fbe09-103">Import declarations: The `open` keyword</span></span>

<span data-ttu-id="fbe09-104">Une *déclaration d’importation* spécifie un module ou un espace de noms dont vous pouvez référencer des éléments sans utiliser un nom qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="fbe09-104">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="fbe09-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbe09-105">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="fbe09-106">Notes</span><span class="sxs-lookup"><span data-stu-id="fbe09-106">Remarks</span></span>

<span data-ttu-id="fbe09-107">Le référencement du code à l’aide de l’espace de noms complet ou du chemin du module à chaque fois peut créer du code difficile à écrire, lire et gérer.</span><span class="sxs-lookup"><span data-stu-id="fbe09-107">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="fbe09-108">Au lieu de cela, vous pouvez utiliser le `open` mot clé pour les modules et les espaces de noms fréquemment utilisés. ainsi, lorsque vous référencez un membre de ce module ou de cet espace de noms, vous pouvez utiliser la forme abrégée du nom au lieu du nom complet.</span><span class="sxs-lookup"><span data-stu-id="fbe09-108">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="fbe09-109">Ce mot clé est semblable au `using` mot clé en C#, `using namespace` dans Visual C++ et `Imports` dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fbe09-109">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="fbe09-110">Le module ou l’espace de noms fourni doit se trouver dans le même projet ou dans un projet ou un assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="fbe09-110">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="fbe09-111">Si ce n’est pas le cas, vous pouvez ajouter une référence au projet ou utiliser l' `-reference` option de ligne de commande (ou son abréviation, `-r` ).</span><span class="sxs-lookup"><span data-stu-id="fbe09-111">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="fbe09-112">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="fbe09-112">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="fbe09-113">La déclaration d’importation rend les noms disponibles dans le code qui suit la déclaration, jusqu’à la fin de l’espace de noms, du module ou du fichier englobant.</span><span class="sxs-lookup"><span data-stu-id="fbe09-113">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="fbe09-114">Lorsque vous utilisez plusieurs déclarations d’importation, elles doivent apparaître sur des lignes distinctes.</span><span class="sxs-lookup"><span data-stu-id="fbe09-114">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="fbe09-115">Le code suivant illustre l’utilisation du `open` mot clé pour simplifier le code.</span><span class="sxs-lookup"><span data-stu-id="fbe09-115">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="fbe09-116">Le compilateur F # n’émet pas d’erreur ni d’avertissement quand des ambiguïtés se produisent lorsque le même nom se trouve dans plusieurs modules ou espaces de noms ouverts.</span><span class="sxs-lookup"><span data-stu-id="fbe09-116">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="fbe09-117">Quand des ambiguïtés se produisent, F # donne la préférence au module ou à l’espace de noms le plus récemment ouvert.</span><span class="sxs-lookup"><span data-stu-id="fbe09-117">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="fbe09-118">Par exemple, dans le code suivant, `empty` signifie `Seq.empty` , même si `empty` se trouve à la fois dans les `List` `Seq` modules et.</span><span class="sxs-lookup"><span data-stu-id="fbe09-118">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="fbe09-119">Par conséquent, soyez vigilant lorsque vous ouvrez des modules ou des espaces de noms tels que `List` ou `Seq` qui contiennent des membres qui ont des noms identiques ; à la place, envisagez d’utiliser les noms qualifiés.</span><span class="sxs-lookup"><span data-stu-id="fbe09-119">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="fbe09-120">Vous devez éviter toute situation dans laquelle le code dépend de l’ordre des déclarations d’importation.</span><span class="sxs-lookup"><span data-stu-id="fbe09-120">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="fbe09-121">Espaces de noms ouverts par défaut</span><span class="sxs-lookup"><span data-stu-id="fbe09-121">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="fbe09-122">Certains espaces de noms sont si souvent utilisés dans du code F # qu’ils sont ouverts implicitement sans avoir besoin d’une déclaration d’importation explicite.</span><span class="sxs-lookup"><span data-stu-id="fbe09-122">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="fbe09-123">Le tableau suivant répertorie les espaces de noms qui sont ouverts par défaut.</span><span class="sxs-lookup"><span data-stu-id="fbe09-123">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="fbe09-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="fbe09-124">Namespace</span></span>|<span data-ttu-id="fbe09-125">Description</span><span class="sxs-lookup"><span data-stu-id="fbe09-125">Description</span></span>|
|---------|-----------|
|`FSharp.Core`|<span data-ttu-id="fbe09-126">Contient des définitions de type F # de base pour les types intégrés tels que `int` et `float` .</span><span class="sxs-lookup"><span data-stu-id="fbe09-126">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`FSharp.Core.Operators`|<span data-ttu-id="fbe09-127">Contient des opérations arithmétiques de base telles que `+` et `*` .</span><span class="sxs-lookup"><span data-stu-id="fbe09-127">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`FSharp.Collections`|<span data-ttu-id="fbe09-128">Contient des classes de collection immuables telles que `List` et `Array` .</span><span class="sxs-lookup"><span data-stu-id="fbe09-128">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`FSharp.Control`|<span data-ttu-id="fbe09-129">Contient des types pour les constructions de contrôle telles que l’évaluation différée et les flux de travail asynchrones.</span><span class="sxs-lookup"><span data-stu-id="fbe09-129">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`FSharp.Text`|<span data-ttu-id="fbe09-130">Contient des fonctions pour les e/s mises en forme, telles que la `printf` fonction.</span><span class="sxs-lookup"><span data-stu-id="fbe09-130">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="fbe09-131">Attribut Open</span><span class="sxs-lookup"><span data-stu-id="fbe09-131">AutoOpen Attribute</span></span>

<span data-ttu-id="fbe09-132">Vous pouvez appliquer l' `AutoOpen` attribut à un assembly si vous souhaitez ouvrir automatiquement un espace de noms ou un module lorsque l’assembly est référencé.</span><span class="sxs-lookup"><span data-stu-id="fbe09-132">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="fbe09-133">Vous pouvez également appliquer l' `AutoOpen` attribut à un module pour ouvrir automatiquement ce module lors de l’ouverture du module ou de l’espace de noms parent.</span><span class="sxs-lookup"><span data-stu-id="fbe09-133">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="fbe09-134">Pour plus d’informations, consultez [AutoOpenAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html).</span><span class="sxs-lookup"><span data-stu-id="fbe09-134">For more information, see [AutoOpenAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="fbe09-135">Attribut RequireQualifiedAccess</span><span class="sxs-lookup"><span data-stu-id="fbe09-135">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="fbe09-136">Certains modules, enregistrements ou types d’Union peuvent spécifier l' `RequireQualifiedAccess` attribut.</span><span class="sxs-lookup"><span data-stu-id="fbe09-136">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="fbe09-137">Lorsque vous référencez des éléments de ces modules, enregistrements ou unions, vous devez utiliser un nom qualifié, que vous incluiez ou non une déclaration d’importation.</span><span class="sxs-lookup"><span data-stu-id="fbe09-137">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="fbe09-138">Si vous utilisez cet attribut de façon stratégique sur des types qui définissent des noms couramment utilisés, vous évitez les conflits de noms et rendez le code plus résilient aux modifications dans les bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="fbe09-138">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="fbe09-139">Pour plus d’informations, consultez [RequireQualifiedAccessAttribute (](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html).</span><span class="sxs-lookup"><span data-stu-id="fbe09-139">For more information, see [RequireQualifiedAccessAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbe09-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbe09-140">See also</span></span>

- [<span data-ttu-id="fbe09-141">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="fbe09-141">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="fbe09-142">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="fbe09-142">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="fbe09-143">Modules</span><span class="sxs-lookup"><span data-stu-id="fbe09-143">Modules</span></span>](modules.md)
