---
title: "Déclarations d'importation : mot clé open"
description: Renseignez-vous sur les déclarations d’importation de F et comment elles spécifient un module ou un espace de nom dont vous pouvez référencer les éléments sans utiliser un nom entièrement qualifié.
ms.date: 04/04/2019
ms.openlocfilehash: 0baef27c7dc3181b9da0defb1c793fec04269c09
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021532"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="42fdd-103">Déclarations d’importation : mot clé `open`</span><span class="sxs-lookup"><span data-stu-id="42fdd-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="42fdd-104">Les liens des informations de référence sur les API qui figurent dans cet article pointent vers MSDN.</span><span class="sxs-lookup"><span data-stu-id="42fdd-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="42fdd-105">Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.</span><span class="sxs-lookup"><span data-stu-id="42fdd-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="42fdd-106">Une *déclaration d’importation* spécifie un module ou un espace de nom dont vous pouvez référencer les éléments sans utiliser un nom entièrement qualifié.</span><span class="sxs-lookup"><span data-stu-id="42fdd-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="42fdd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42fdd-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="42fdd-108">Notes</span><span class="sxs-lookup"><span data-stu-id="42fdd-108">Remarks</span></span>

<span data-ttu-id="42fdd-109">Le référencement du code en utilisant l’espace de nom ou le parcours du module entièrement qualifié à chaque fois peut créer du code qui est difficile à écrire, lire et maintenir.</span><span class="sxs-lookup"><span data-stu-id="42fdd-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="42fdd-110">Au lieu de `open` cela, vous pouvez utiliser le mot clé pour les modules fréquemment utilisés et les espaces de noms de sorte que lorsque vous référencez un membre de ce module ou l’espace de nom, vous pouvez utiliser la forme courte du nom au lieu du nom entièrement qualifié.</span><span class="sxs-lookup"><span data-stu-id="42fdd-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="42fdd-111">Ce mot clé `using` est similaire au `using namespace` mot clé dans `Imports` C, dans Visual CMD et dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="42fdd-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="42fdd-112">Le module ou l’espace de nom fourni doit être dans le même projet ou dans un projet ou un assemblage référencé.</span><span class="sxs-lookup"><span data-stu-id="42fdd-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="42fdd-113">Si ce n’est pas le cas, vous `-reference` pouvez ajouter une référence au projet, `-r`ou utiliser l’option de ligne de commande (ou son abréviation, ).</span><span class="sxs-lookup"><span data-stu-id="42fdd-113">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="42fdd-114">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="42fdd-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="42fdd-115">La déclaration d’importation met les noms disponibles dans le code qui suit la déclaration, jusqu’à la fin de l’espace de nom, du module ou du fichier.</span><span class="sxs-lookup"><span data-stu-id="42fdd-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="42fdd-116">Lorsque vous utilisez plusieurs déclarations d’importation, elles doivent apparaître sur des lignes distinctes.</span><span class="sxs-lookup"><span data-stu-id="42fdd-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="42fdd-117">Le code suivant affiche `open` l’utilisation du mot clé pour simplifier le code.</span><span class="sxs-lookup"><span data-stu-id="42fdd-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="42fdd-118">Le compilateur F n’émet pas d’erreur ou d’avertissement lorsque des ambiguïtés se produisent lorsque le même nom se produit dans plus d’un module ou un espace nom ouvert.</span><span class="sxs-lookup"><span data-stu-id="42fdd-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="42fdd-119">Lorsque des ambiguïtés se produisent, Fmd donne la préférence au module ou à l’espace de nom plus récemment ouvert.</span><span class="sxs-lookup"><span data-stu-id="42fdd-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="42fdd-120">Par exemple, dans le `empty` `Seq.empty`code suivant, signifie, même si est `empty` situé à la fois dans les `List` deux et `Seq` les modules.</span><span class="sxs-lookup"><span data-stu-id="42fdd-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="42fdd-121">Par conséquent, soyez prudent lorsque vous ouvrez `List` `Seq` des modules ou des espaces de nom tels que ou qui contiennent des membres qui ont des noms identiques; au lieu de cela, envisager d’utiliser les noms qualifiés.</span><span class="sxs-lookup"><span data-stu-id="42fdd-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="42fdd-122">Vous devez éviter toute situation dans laquelle le code dépend de l’ordre des déclarations d’importation.</span><span class="sxs-lookup"><span data-stu-id="42fdd-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="42fdd-123">Espaces de noms qui sont ouverts par défaut</span><span class="sxs-lookup"><span data-stu-id="42fdd-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="42fdd-124">Certains espaces nominatifs sont si fréquemment utilisés dans le code F qu’ils sont ouverts implicitement sans avoir besoin d’une déclaration d’importation explicite.</span><span class="sxs-lookup"><span data-stu-id="42fdd-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="42fdd-125">Le tableau suivant affiche les espaces nominaux qui sont ouverts par défaut.</span><span class="sxs-lookup"><span data-stu-id="42fdd-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="42fdd-126">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="42fdd-126">Namespace</span></span>|<span data-ttu-id="42fdd-127">Description</span><span class="sxs-lookup"><span data-stu-id="42fdd-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="42fdd-128">Contient des définitions de type FMD `int` de `float`base pour les types intégrés tels que et .</span><span class="sxs-lookup"><span data-stu-id="42fdd-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="42fdd-129">Contient des opérations arithmétiques de base telles que `+` et `*`.</span><span class="sxs-lookup"><span data-stu-id="42fdd-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="42fdd-130">Contient des classes de `List` collecte `Array`immuables telles que et .</span><span class="sxs-lookup"><span data-stu-id="42fdd-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="42fdd-131">Contient des types pour les constructions de contrôle telles que l’évaluation paresseuse et les flux de travail asynchrones.</span><span class="sxs-lookup"><span data-stu-id="42fdd-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="42fdd-132">Contient des fonctions pour IO `printf` formaté, telles que la fonction.</span><span class="sxs-lookup"><span data-stu-id="42fdd-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="42fdd-133">Attribut AutoOpen</span><span class="sxs-lookup"><span data-stu-id="42fdd-133">AutoOpen Attribute</span></span>

<span data-ttu-id="42fdd-134">Vous pouvez `AutoOpen` appliquer l’attribut à un assemblage si vous souhaitez ouvrir automatiquement un espace de nom ou un module lorsque l’assemblage est référencé.</span><span class="sxs-lookup"><span data-stu-id="42fdd-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="42fdd-135">Vous pouvez également `AutoOpen` appliquer l’attribut à un module pour ouvrir automatiquement ce module lorsque le module parent ou l’espace de nom est ouvert.</span><span class="sxs-lookup"><span data-stu-id="42fdd-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="42fdd-136">Pour plus d’informations, voir [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="42fdd-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="42fdd-137">Exiger Un attribut d’access de qualification</span><span class="sxs-lookup"><span data-stu-id="42fdd-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="42fdd-138">Certains modules, enregistrements ou types `RequireQualifiedAccess` de syndicats peuvent spécifier l’attribut.</span><span class="sxs-lookup"><span data-stu-id="42fdd-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="42fdd-139">Lorsque vous faites référence à des éléments de ces modules, dossiers ou syndicats, vous devez utiliser un nom qualifié, que vous incluiez ou non une déclaration d’importation.</span><span class="sxs-lookup"><span data-stu-id="42fdd-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="42fdd-140">Si vous utilisez cet attribut stratégiquement sur les types qui définissent les noms couramment utilisés, vous aidez à éviter les collisions de noms et ainsi rendre le code plus résistant aux changements dans les bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="42fdd-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="42fdd-141">Pour plus d’informations, voir [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="42fdd-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="42fdd-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42fdd-142">See also</span></span>

- [<span data-ttu-id="42fdd-143">Référence linguistique F</span><span class="sxs-lookup"><span data-stu-id="42fdd-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="42fdd-144">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="42fdd-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="42fdd-145">Modules</span><span class="sxs-lookup"><span data-stu-id="42fdd-145">Modules</span></span>](modules.md)
