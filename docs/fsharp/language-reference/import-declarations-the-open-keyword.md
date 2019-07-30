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
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="e12fb-103">Déclarations d’importation : mot clé `open`</span><span class="sxs-lookup"><span data-stu-id="e12fb-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="e12fb-104">Les liens des informations de référence sur les API qui figurent dans cet article pointent vers MSDN.</span><span class="sxs-lookup"><span data-stu-id="e12fb-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="e12fb-105">Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.</span><span class="sxs-lookup"><span data-stu-id="e12fb-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="e12fb-106">Une *déclaration d’importation* spécifie un module ou un espace de noms dont vous pouvez référencer des éléments sans utiliser un nom qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="e12fb-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="e12fb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e12fb-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="e12fb-108">Notes</span><span class="sxs-lookup"><span data-stu-id="e12fb-108">Remarks</span></span>

<span data-ttu-id="e12fb-109">Le référencement du code à l’aide de l’espace de noms complet ou du chemin du module à chaque fois peut créer du code difficile à écrire, lire et gérer.</span><span class="sxs-lookup"><span data-stu-id="e12fb-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="e12fb-110">Au lieu de cela, vous `open` pouvez utiliser le mot clé pour les modules et les espaces de noms fréquemment utilisés. ainsi, lorsque vous référencez un membre de ce module ou de cet espace de noms, vous pouvez utiliser la forme abrégée du nom au lieu du nom complet.</span><span class="sxs-lookup"><span data-stu-id="e12fb-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="e12fb-111">Ce mot clé est semblable au `using` mot clé C#dans `using namespace` , en C++Visual et `Imports` dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e12fb-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="e12fb-112">Le module ou l’espace de noms fourni doit se trouver dans le même projet ou dans un projet ou un assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="e12fb-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="e12fb-113">Si ce n’est pas le cas, vous pouvez ajouter une référence au projet ou utiliser `-reference` l'`-`option de ligne de commande (ou son `-r`abréviation,).</span><span class="sxs-lookup"><span data-stu-id="e12fb-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="e12fb-114">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="e12fb-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="e12fb-115">La déclaration d’importation rend les noms disponibles dans le code qui suit la déclaration, jusqu’à la fin de l’espace de noms, du module ou du fichier englobant.</span><span class="sxs-lookup"><span data-stu-id="e12fb-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="e12fb-116">Lorsque vous utilisez plusieurs déclarations d’importation, elles doivent apparaître sur des lignes distinctes.</span><span class="sxs-lookup"><span data-stu-id="e12fb-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="e12fb-117">Le code suivant illustre l’utilisation du `open` mot clé pour simplifier le code.</span><span class="sxs-lookup"><span data-stu-id="e12fb-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="e12fb-118">Le F# compilateur n’émet pas d’erreur ou d’avertissement quand des ambiguïtés se produisent lorsque le même nom se trouve dans plusieurs modules ou espaces de noms ouverts.</span><span class="sxs-lookup"><span data-stu-id="e12fb-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="e12fb-119">Quand des ambiguïtés se F# produisent, donne la préférence au module ou à l’espace de noms récemment ouvert.</span><span class="sxs-lookup"><span data-stu-id="e12fb-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="e12fb-120">Par exemple, dans le code suivant, `empty` signifie `Seq.empty`, même si `empty` se trouve à la fois `List` dans `Seq` les modules et.</span><span class="sxs-lookup"><span data-stu-id="e12fb-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="e12fb-121">Par conséquent, soyez vigilant lorsque vous ouvrez des modules ou des espaces `List` de `Seq` noms tels que ou qui contiennent des membres qui ont des noms identiques; à la place, envisagez d’utiliser les noms qualifiés.</span><span class="sxs-lookup"><span data-stu-id="e12fb-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="e12fb-122">Vous devez éviter toute situation dans laquelle le code dépend de l’ordre des déclarations d’importation.</span><span class="sxs-lookup"><span data-stu-id="e12fb-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="e12fb-123">Espaces de noms ouverts par défaut</span><span class="sxs-lookup"><span data-stu-id="e12fb-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="e12fb-124">Certains espaces de noms sont si souvent utilisés F# dans le code qu’ils sont ouverts implicitement sans qu’une déclaration d’importation explicite soit nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e12fb-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="e12fb-125">Le tableau suivant répertorie les espaces de noms qui sont ouverts par défaut.</span><span class="sxs-lookup"><span data-stu-id="e12fb-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="e12fb-126">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="e12fb-126">Namespace</span></span>|<span data-ttu-id="e12fb-127">Description</span><span class="sxs-lookup"><span data-stu-id="e12fb-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="e12fb-128">Contient des F# définitions de type de base pour les types intégrés `int` tels `float`que et.</span><span class="sxs-lookup"><span data-stu-id="e12fb-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="e12fb-129">Contient des opérations arithmétiques de `+` base `*`telles que et.</span><span class="sxs-lookup"><span data-stu-id="e12fb-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="e12fb-130">Contient des classes de collection immuables `List` telles `Array`que et.</span><span class="sxs-lookup"><span data-stu-id="e12fb-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="e12fb-131">Contient des types pour les constructions de contrôle telles que l’évaluation différée et les flux de travail asynchrones.</span><span class="sxs-lookup"><span data-stu-id="e12fb-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="e12fb-132">Contient des fonctions pour les e/s mises `printf` en forme, telles que la fonction.</span><span class="sxs-lookup"><span data-stu-id="e12fb-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="e12fb-133">Attribut Open</span><span class="sxs-lookup"><span data-stu-id="e12fb-133">AutoOpen Attribute</span></span>

<span data-ttu-id="e12fb-134">Vous pouvez appliquer l' `AutoOpen` attribut à un assembly si vous souhaitez ouvrir automatiquement un espace de noms ou un module lorsque l’assembly est référencé.</span><span class="sxs-lookup"><span data-stu-id="e12fb-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="e12fb-135">Vous pouvez également appliquer l' `AutoOpen` attribut à un module pour ouvrir automatiquement ce module lors de l’ouverture du module ou de l’espace de noms parent.</span><span class="sxs-lookup"><span data-stu-id="e12fb-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="e12fb-136">Pour plus d’informations, consultez [Core. AutoOpenAttribute, classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="e12fb-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="e12fb-137">Attribut RequireQualifiedAccess</span><span class="sxs-lookup"><span data-stu-id="e12fb-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="e12fb-138">Certains modules, enregistrements ou types d’Union peuvent spécifier l' `RequireQualifiedAccess` attribut.</span><span class="sxs-lookup"><span data-stu-id="e12fb-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="e12fb-139">Lorsque vous référencez des éléments de ces modules, enregistrements ou unions, vous devez utiliser un nom qualifié, que vous incluiez ou non une déclaration d’importation.</span><span class="sxs-lookup"><span data-stu-id="e12fb-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="e12fb-140">Si vous utilisez cet attribut de façon stratégique sur des types qui définissent des noms couramment utilisés, vous évitez les conflits de noms et rendez le code plus résilient aux modifications dans les bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="e12fb-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="e12fb-141">Pour plus d’informations, consultez [Core. RequireQualifiedAccessAttribute (, classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="e12fb-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="e12fb-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e12fb-142">See also</span></span>

- [<span data-ttu-id="e12fb-143">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="e12fb-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="e12fb-144">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="e12fb-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="e12fb-145">Modules</span><span class="sxs-lookup"><span data-stu-id="e12fb-145">Modules</span></span>](modules.md)
