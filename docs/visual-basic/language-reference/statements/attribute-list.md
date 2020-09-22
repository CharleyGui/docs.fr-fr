---
title: Liste d’attributs
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: e566239c56efa8ca8e83bff92486fec4c434e92b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874739"
---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="def37-102">Liste d'attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="def37-102">Attribute List (Visual Basic)</span></span>

<span data-ttu-id="def37-103">Spécifie les attributs à appliquer à un élément de programmation déclaré.</span><span class="sxs-lookup"><span data-stu-id="def37-103">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="def37-104">Les attributs multiples sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="def37-104">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="def37-105">Voici la syntaxe d’un attribut.</span><span class="sxs-lookup"><span data-stu-id="def37-105">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="def37-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="def37-106">Syntax</span></span>  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="def37-107">Éléments</span><span class="sxs-lookup"><span data-stu-id="def37-107">Parts</span></span>  

|||
|---|---|
|`attributemodifier`|<span data-ttu-id="def37-108">Obligatoire pour les attributs appliqués au début d’un fichier source.</span><span class="sxs-lookup"><span data-stu-id="def37-108">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="def37-109">Il peut s’agir d’un [assembly](../modifiers/assembly.md) ou d’un [module](../modifiers/module-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="def37-109">Can be [Assembly](../modifiers/assembly.md) or [Module](../modifiers/module-keyword.md).</span></span>|
|`attributename`| <span data-ttu-id="def37-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="def37-110">Required.</span></span> <span data-ttu-id="def37-111">Nom de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="def37-111">Name of the attribute.</span></span>|
|`attributearguments`|<span data-ttu-id="def37-112">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="def37-112">Optional.</span></span> <span data-ttu-id="def37-113">Liste des arguments positionnels pour cet attribut.</span><span class="sxs-lookup"><span data-stu-id="def37-113">List of positional arguments for this attribute.</span></span> <span data-ttu-id="def37-114">Les arguments multiples sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="def37-114">Multiple arguments are separated by commas.</span></span>|
|`attributeinitializer`|<span data-ttu-id="def37-115">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="def37-115">Optional.</span></span> <span data-ttu-id="def37-116">Liste d’initialiseurs de variable ou de propriété pour cet attribut.</span><span class="sxs-lookup"><span data-stu-id="def37-116">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="def37-117">Plusieurs initialiseurs sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="def37-117">Multiple initializers are separated by commas.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="def37-118">Notes</span><span class="sxs-lookup"><span data-stu-id="def37-118">Remarks</span></span>  

 <span data-ttu-id="def37-119">Vous pouvez appliquer un ou plusieurs attributs à presque n’importe quel élément de programmation (types, procédures, propriétés, etc.).</span><span class="sxs-lookup"><span data-stu-id="def37-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="def37-120">Les attributs apparaissent dans les métadonnées de votre assembly. ils peuvent vous aider à annoter votre code ou à spécifier comment utiliser un élément de programmation particulier.</span><span class="sxs-lookup"><span data-stu-id="def37-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="def37-121">Vous pouvez appliquer des attributs définis par Visual Basic et le .NET Framework, et vous pouvez définir vos propres attributs.</span><span class="sxs-lookup"><span data-stu-id="def37-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="def37-122">Pour plus d’informations sur l’utilisation des attributs, consultez [vue d’ensemble des attributs](../../programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="def37-122">For more information on when to use attributes, see [Attributes overview](../../programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="def37-123">Pour plus d’informations sur les noms d’attributs, consultez [noms d’éléments déclarés](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="def37-123">For information on attribute names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="def37-124">Règles</span><span class="sxs-lookup"><span data-stu-id="def37-124">Rules</span></span>  
  
- <span data-ttu-id="def37-125">**Importation.**</span><span class="sxs-lookup"><span data-stu-id="def37-125">**Placement.**</span></span> <span data-ttu-id="def37-126">Vous pouvez appliquer des attributs aux éléments de programmation les plus déclarés.</span><span class="sxs-lookup"><span data-stu-id="def37-126">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="def37-127">Pour appliquer un ou plusieurs attributs, vous placez un *bloc d’attributs* au début de la déclaration de l’élément.</span><span class="sxs-lookup"><span data-stu-id="def37-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="def37-128">Chaque entrée de la liste d’attributs spécifie un attribut que vous souhaitez appliquer, ainsi que le modificateur et les arguments que vous utilisez pour cet appel de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="def37-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
- <span data-ttu-id="def37-129">**Chevrons.**</span><span class="sxs-lookup"><span data-stu-id="def37-129">**Angle Brackets.**</span></span> <span data-ttu-id="def37-130">Si vous fournissez une liste d’attributs, vous devez la placer entre crochets pointus (« `<` » et «» `>` ).</span><span class="sxs-lookup"><span data-stu-id="def37-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
- <span data-ttu-id="def37-131">**Partie de la déclaration.**</span><span class="sxs-lookup"><span data-stu-id="def37-131">**Part of the Declaration.**</span></span> <span data-ttu-id="def37-132">L’attribut doit faire partie de la déclaration de l’élément, et non d’une instruction distincte.</span><span class="sxs-lookup"><span data-stu-id="def37-132">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="def37-133">Vous pouvez utiliser la séquence de continuation de ligne (« `_` ») pour étendre l’instruction de déclaration sur plusieurs lignes de code source.</span><span class="sxs-lookup"><span data-stu-id="def37-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
- <span data-ttu-id="def37-134">**Modificateurs.**</span><span class="sxs-lookup"><span data-stu-id="def37-134">**Modifiers.**</span></span> <span data-ttu-id="def37-135">Un modificateur d’attribut ( `Assembly` ou `Module` ) est requis sur chaque attribut appliqué à un élément de programmation au début d’un fichier source.</span><span class="sxs-lookup"><span data-stu-id="def37-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="def37-136">Les modificateurs d’attribut ne sont pas autorisés sur les attributs appliqués aux éléments qui ne sont pas au début d’un fichier source.</span><span class="sxs-lookup"><span data-stu-id="def37-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
- <span data-ttu-id="def37-137">**Arguments.**</span><span class="sxs-lookup"><span data-stu-id="def37-137">**Arguments.**</span></span> <span data-ttu-id="def37-138">Tous les arguments positionnels d’un attribut doivent précéder tout initialiseur de variable ou de propriété.</span><span class="sxs-lookup"><span data-stu-id="def37-138">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="def37-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="def37-139">Example</span></span>  

 <span data-ttu-id="def37-140">L’exemple suivant applique l' <xref:System.Runtime.InteropServices.DllImportAttribute> attribut à une définition squelette d’une `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="def37-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="def37-141"><xref:System.Runtime.InteropServices.DllImportAttribute> indique que la procédure avec attributs représente un point d’entrée dans une bibliothèque de liens dynamiques (DLL) non managée.</span><span class="sxs-lookup"><span data-stu-id="def37-141"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="def37-142">L’attribut fournit le nom de la DLL comme argument positionnel et les autres informations sous forme d’initialiseurs de variables.</span><span class="sxs-lookup"><span data-stu-id="def37-142">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="def37-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="def37-143">See also</span></span>

- [<span data-ttu-id="def37-144">Assembly</span><span class="sxs-lookup"><span data-stu-id="def37-144">Assembly</span></span>](../modifiers/assembly.md)
- [<span data-ttu-id="def37-145">Modules \<keyword></span><span class="sxs-lookup"><span data-stu-id="def37-145">Module \<keyword></span></span>](../modifiers/module-keyword.md)
- [<span data-ttu-id="def37-146">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="def37-146">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="def37-147">Procédure : Diviser et combiner des instructions dans le code</span><span class="sxs-lookup"><span data-stu-id="def37-147">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
