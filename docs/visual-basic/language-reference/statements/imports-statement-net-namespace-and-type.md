---
title: Instruction Imports-espace de noms et type .NET
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: 39fa4e74f973bcb575b5751c387c0b879f4e398d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351067"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="6e4df-102">Imports, instruction (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="6e4df-102">Imports Statement (.NET Namespace and Type)</span></span>

<span data-ttu-id="6e4df-103">Permet de référencer des noms de types sans qualification d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="6e4df-103">Enables type names to be referenced without namespace qualification.</span></span>

## <a name="syntax"></a><span data-ttu-id="6e4df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e4df-104">Syntax</span></span>

```vb
Imports [ aliasname = ] namespace
' -or-
Imports [ aliasname = ] namespace.element
```

## <a name="parts"></a><span data-ttu-id="6e4df-105">Composants</span><span class="sxs-lookup"><span data-stu-id="6e4df-105">Parts</span></span>

|<span data-ttu-id="6e4df-106">Terme</span><span class="sxs-lookup"><span data-stu-id="6e4df-106">Term</span></span>|<span data-ttu-id="6e4df-107">Définition</span><span class="sxs-lookup"><span data-stu-id="6e4df-107">Definition</span></span>|
|---|---|
|`aliasname`|<span data-ttu-id="6e4df-108">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6e4df-108">Optional.</span></span> <span data-ttu-id="6e4df-109">*Alias d’importation* ou nom par lequel le code peut faire référence à `namespace` au lieu de la chaîne de qualification complète.</span><span class="sxs-lookup"><span data-stu-id="6e4df-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="6e4df-110">Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="6e4df-110">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`namespace`|<span data-ttu-id="6e4df-111">Requis.</span><span class="sxs-lookup"><span data-stu-id="6e4df-111">Required.</span></span> <span data-ttu-id="6e4df-112">Nom qualifié complet de l’espace de noms importé.</span><span class="sxs-lookup"><span data-stu-id="6e4df-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="6e4df-113">Peut être une chaîne d’espaces de noms imbriqués à n’importe quel niveau.</span><span class="sxs-lookup"><span data-stu-id="6e4df-113">Can be a string of namespaces nested to any level.</span></span>|
|`element`|<span data-ttu-id="6e4df-114">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6e4df-114">Optional.</span></span> <span data-ttu-id="6e4df-115">Nom d’un élément de programmation déclaré dans l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="6e4df-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="6e4df-116">Peut être n’importe quel élément conteneur.</span><span class="sxs-lookup"><span data-stu-id="6e4df-116">Can be any container element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6e4df-117">Notes</span><span class="sxs-lookup"><span data-stu-id="6e4df-117">Remarks</span></span>

<span data-ttu-id="6e4df-118">L’instruction `Imports` permet de référencer directement les types contenus dans un espace de noms donné.</span><span class="sxs-lookup"><span data-stu-id="6e4df-118">The `Imports` statement enables types that are contained in a given namespace to be referenced directly.</span></span>

<span data-ttu-id="6e4df-119">Vous pouvez fournir un nom d’espace de noms unique ou une chaîne d’espaces de noms imbriqués.</span><span class="sxs-lookup"><span data-stu-id="6e4df-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="6e4df-120">Chaque espace de noms imbriqué est séparé de l’espace de noms de niveau supérieur suivant par un point (`.`), comme l’illustre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6e4df-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates:</span></span>

```vb
Imports System.Collections.Generic
```

<span data-ttu-id="6e4df-121">Chaque fichier source peut contenir un nombre quelconque d’instructions `Imports`.</span><span class="sxs-lookup"><span data-stu-id="6e4df-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="6e4df-122">Celles-ci doivent suivre les déclarations d’option, telles que l’instruction `Option Strict`, et elles doivent précéder toutes les déclarations d’éléments de programmation, telles que les instructions `Module` ou `Class`.</span><span class="sxs-lookup"><span data-stu-id="6e4df-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>

<span data-ttu-id="6e4df-123">Vous pouvez utiliser `Imports` uniquement au niveau du fichier.</span><span class="sxs-lookup"><span data-stu-id="6e4df-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="6e4df-124">Cela signifie que le contexte de déclaration pour l’importation doit être un fichier source et ne peut pas être un espace de noms, une classe, une structure, un module, une interface, une procédure ou un bloc.</span><span class="sxs-lookup"><span data-stu-id="6e4df-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>

<span data-ttu-id="6e4df-125">Notez que l’instruction `Imports` ne rend pas les éléments d’autres projets et assemblys disponibles pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="6e4df-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="6e4df-126">L’importation ne remplace pas la définition d’une référence.</span><span class="sxs-lookup"><span data-stu-id="6e4df-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="6e4df-127">Il n’est plus nécessaire de qualifier des noms déjà disponibles pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="6e4df-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="6e4df-128">Pour plus d’informations, consultez « importation d’éléments contenants » dans les [références aux éléments déclarés](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="6e4df-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6e4df-129">Vous pouvez définir des instructions `Imports` implicites à l’aide de la [page références, concepteur de projets (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6e4df-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="6e4df-130">Pour plus d’informations, consultez [Comment : ajouter ou supprimer des espaces de noms importés (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6e4df-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>

## <a name="import-aliases"></a><span data-ttu-id="6e4df-131">Alias d’importation</span><span class="sxs-lookup"><span data-stu-id="6e4df-131">Import Aliases</span></span>

<span data-ttu-id="6e4df-132">Un *alias d’importation* définit l’alias pour un espace de noms ou un type.</span><span class="sxs-lookup"><span data-stu-id="6e4df-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="6e4df-133">Les alias d’importation sont utiles quand vous devez utiliser des éléments portant le même nom et qui sont déclarés dans un ou plusieurs espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="6e4df-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="6e4df-134">Pour plus d’informations et pour obtenir un exemple, consultez « qualifier un nom d’élément » dans les [références aux éléments déclarés](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="6e4df-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="6e4df-135">Vous ne devez pas déclarer un membre au niveau du module avec le même nom que `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="6e4df-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="6e4df-136">Si vous le faites, le compilateur Visual Basic utilise `aliasname` uniquement pour le membre déclaré et ne le reconnaît plus comme alias d’importation.</span><span class="sxs-lookup"><span data-stu-id="6e4df-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>

<span data-ttu-id="6e4df-137">Bien que la syntaxe utilisée pour déclarer un alias d’importation soit similaire à celle utilisée pour l’importation d’un préfixe d’espace de noms XML, les résultats sont différents.</span><span class="sxs-lookup"><span data-stu-id="6e4df-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="6e4df-138">Un alias d’importation peut être utilisé en tant qu’expression dans votre code, alors qu’un préfixe d’espace de noms XML ne peut être utilisé que dans des littéraux XML ou des propriétés d’axe XML en tant que préfixe d’un élément qualifié ou d’un nom d’attribut.</span><span class="sxs-lookup"><span data-stu-id="6e4df-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>

### <a name="element-names"></a><span data-ttu-id="6e4df-139">Noms des éléments</span><span class="sxs-lookup"><span data-stu-id="6e4df-139">Element Names</span></span>

<span data-ttu-id="6e4df-140">Si vous fournissez `element`, il doit représenter un *élément conteneur*, autrement dit un élément de programmation qui peut contenir d’autres éléments.</span><span class="sxs-lookup"><span data-stu-id="6e4df-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="6e4df-141">Les éléments de conteneur incluent des classes, des structures, des modules, des interfaces et des énumérations.</span><span class="sxs-lookup"><span data-stu-id="6e4df-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>

<span data-ttu-id="6e4df-142">La portée des éléments rendus disponibles par une instruction `Imports` varie selon que vous spécifiez `element`.</span><span class="sxs-lookup"><span data-stu-id="6e4df-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="6e4df-143">Si vous spécifiez uniquement `namespace`, tous les membres nommés de manière unique de cet espace de noms, et les membres des éléments de conteneur dans cet espace de noms, sont disponibles sans qualification.</span><span class="sxs-lookup"><span data-stu-id="6e4df-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="6e4df-144">Si vous spécifiez à la fois `namespace` et `element`, seuls les membres de cet élément sont disponibles sans qualification.</span><span class="sxs-lookup"><span data-stu-id="6e4df-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>

## <a name="example"></a><span data-ttu-id="6e4df-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e4df-145">Example</span></span>

<span data-ttu-id="6e4df-146">L’exemple suivant retourne tous les dossiers dans le répertoire *C :\\* à l’aide de la classe <xref:System.IO.DirectoryInfo> :</span><span class="sxs-lookup"><span data-stu-id="6e4df-146">The following example returns all the folders in the *C:\\* directory by using the <xref:System.IO.DirectoryInfo> class:</span></span>

<span data-ttu-id="6e4df-147">Le code n’a aucune instruction `Imports` en haut du fichier.</span><span class="sxs-lookup"><span data-stu-id="6e4df-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="6e4df-148">Par conséquent, les références <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>et <xref:Microsoft.VisualBasic.ControlChars.CrLf> sont toutes qualifiées complètes avec les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="6e4df-148">Therefore, the <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]

## <a name="example"></a><span data-ttu-id="6e4df-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e4df-149">Example</span></span>

<span data-ttu-id="6e4df-150">L’exemple suivant comprend des instructions `Imports` pour les espaces de noms référencés.</span><span class="sxs-lookup"><span data-stu-id="6e4df-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="6e4df-151">Par conséquent, il n’est pas nécessaire que les types soient entièrement qualifiés avec les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="6e4df-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]

[!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]
  
## <a name="example"></a><span data-ttu-id="6e4df-152">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e4df-152">Example</span></span>

<span data-ttu-id="6e4df-153">L’exemple suivant comprend des instructions `Imports` qui créent des alias pour les espaces de noms référencés.</span><span class="sxs-lookup"><span data-stu-id="6e4df-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="6e4df-154">Les types sont qualifiés avec les alias.</span><span class="sxs-lookup"><span data-stu-id="6e4df-154">The types are qualified with the aliases.</span></span>

[!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]

[!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]

## <a name="example"></a><span data-ttu-id="6e4df-155">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e4df-155">Example</span></span>

<span data-ttu-id="6e4df-156">L’exemple suivant comprend des instructions `Imports` qui créent des alias pour les types référencés.</span><span class="sxs-lookup"><span data-stu-id="6e4df-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="6e4df-157">Les alias sont utilisés pour spécifier les types.</span><span class="sxs-lookup"><span data-stu-id="6e4df-157">Aliases are used to specify the types.</span></span>

[!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]

[!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]
  
## <a name="see-also"></a><span data-ttu-id="6e4df-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e4df-158">See also</span></span>

- [<span data-ttu-id="6e4df-159">Namespace (instruction)</span><span class="sxs-lookup"><span data-stu-id="6e4df-159">Namespace Statement</span></span>](namespace-statement.md)
- [<span data-ttu-id="6e4df-160">Espaces de noms dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e4df-160">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="6e4df-161">Références et l’instruction Imports</span><span class="sxs-lookup"><span data-stu-id="6e4df-161">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="6e4df-162">Imports (instruction) (espace de noms XML)</span><span class="sxs-lookup"><span data-stu-id="6e4df-162">Imports Statement (XML Namespace)</span></span>](imports-statement-xml-namespace.md)
- [<span data-ttu-id="6e4df-163">Références aux éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="6e4df-163">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
