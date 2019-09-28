---
title: Partial (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: acfe47f52ede289093b3554a7dd190ef3f0e2c80
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592111"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="22d66-102">Partial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22d66-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="22d66-103">Indique qu'une déclaration de type est une définition partielle du type.</span><span class="sxs-lookup"><span data-stu-id="22d66-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="22d66-104">Vous pouvez diviser la définition d'un type entre plusieurs déclarations à l'aide du mot clé `Partial`.</span><span class="sxs-lookup"><span data-stu-id="22d66-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="22d66-105">Vous pouvez utiliser autant de déclarations partielles que vous le souhaitez, dans autant de fichiers sources que vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="22d66-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="22d66-106">Toutefois, toutes les déclarations doivent être dans le même assembly et le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="22d66-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22d66-107">Visual Basic prend en charge les *méthodes partielles*, qui sont généralement implémentées dans des classes partielles.</span><span class="sxs-lookup"><span data-stu-id="22d66-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="22d66-108">Pour plus d’informations, consultez [méthodes partielles](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) et [instruction Sub](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="22d66-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d66-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22d66-109">Syntax</span></span>  
  
```vb  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="22d66-110">Composants</span><span class="sxs-lookup"><span data-stu-id="22d66-110">Parts</span></span>  
  
|<span data-ttu-id="22d66-111">Terme</span><span class="sxs-lookup"><span data-stu-id="22d66-111">Term</span></span>|<span data-ttu-id="22d66-112">Définition</span><span class="sxs-lookup"><span data-stu-id="22d66-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="22d66-113">facultatif.</span><span class="sxs-lookup"><span data-stu-id="22d66-113">Optional.</span></span> <span data-ttu-id="22d66-114">Liste des attributs qui s'appliquent à ce type.</span><span class="sxs-lookup"><span data-stu-id="22d66-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="22d66-115">Vous devez placer la [liste des attributs](../../../visual-basic/language-reference/statements/attribute-list.md) entre crochets pointus (`< >`).</span><span class="sxs-lookup"><span data-stu-id="22d66-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="22d66-116">facultatif.</span><span class="sxs-lookup"><span data-stu-id="22d66-116">Optional.</span></span> <span data-ttu-id="22d66-117">Spécifie le code pouvant accéder à ce type.</span><span class="sxs-lookup"><span data-stu-id="22d66-117">Specifies what code can access this type.</span></span> <span data-ttu-id="22d66-118">Consultez [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="22d66-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="22d66-119">facultatif.</span><span class="sxs-lookup"><span data-stu-id="22d66-119">Optional.</span></span> <span data-ttu-id="22d66-120">Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="22d66-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="22d66-121">facultatif.</span><span class="sxs-lookup"><span data-stu-id="22d66-121">Optional.</span></span> <span data-ttu-id="22d66-122">Consultez [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="22d66-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="22d66-123">facultatif.</span><span class="sxs-lookup"><span data-stu-id="22d66-123">Optional.</span></span> <span data-ttu-id="22d66-124">Voir [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="22d66-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="22d66-125">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="22d66-125">Required.</span></span> <span data-ttu-id="22d66-126">Nom de ce type.</span><span class="sxs-lookup"><span data-stu-id="22d66-126">Name of this type.</span></span> <span data-ttu-id="22d66-127">Doit correspondre au nom défini dans toutes les autres déclarations partielles du même type.</span><span class="sxs-lookup"><span data-stu-id="22d66-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="22d66-128">facultatif.</span><span class="sxs-lookup"><span data-stu-id="22d66-128">Optional.</span></span> <span data-ttu-id="22d66-129">Spécifie qu'il s'agit d'un type générique.</span><span class="sxs-lookup"><span data-stu-id="22d66-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="22d66-130">Consultez [types génériques dans Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="22d66-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="22d66-131">Obligatoire si [vous utilisez.](../../../visual-basic/language-reference/statements/of-clause.md)</span><span class="sxs-lookup"><span data-stu-id="22d66-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="22d66-132">Consultez la [liste des types](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="22d66-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="22d66-133">facultatif.</span><span class="sxs-lookup"><span data-stu-id="22d66-133">Optional.</span></span> <span data-ttu-id="22d66-134">Consultez [Inherits (instruction](../../../visual-basic/language-reference/statements/inherits-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="22d66-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="22d66-135">Requis si vous utilisez `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="22d66-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="22d66-136">Nom de la classe ou de l'interface dont cette classe dérive.</span><span class="sxs-lookup"><span data-stu-id="22d66-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="22d66-137">facultatif.</span><span class="sxs-lookup"><span data-stu-id="22d66-137">Optional.</span></span> <span data-ttu-id="22d66-138">Consultez [Implements, instruction](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="22d66-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="22d66-139">Requis si vous utilisez `Implements`.</span><span class="sxs-lookup"><span data-stu-id="22d66-139">Required if you use `Implements`.</span></span> <span data-ttu-id="22d66-140">Noms des interfaces que ce type implémente.</span><span class="sxs-lookup"><span data-stu-id="22d66-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="22d66-141">facultatif.</span><span class="sxs-lookup"><span data-stu-id="22d66-141">Optional.</span></span> <span data-ttu-id="22d66-142">Instructions qui déclarent des variables et des événements supplémentaires pour ce type.</span><span class="sxs-lookup"><span data-stu-id="22d66-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="22d66-143">facultatif.</span><span class="sxs-lookup"><span data-stu-id="22d66-143">Optional.</span></span> <span data-ttu-id="22d66-144">Instructions qui déclarent et définissent des procédures supplémentaires pour ce type.</span><span class="sxs-lookup"><span data-stu-id="22d66-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="22d66-145">`End Class` ou `End Structure`</span><span class="sxs-lookup"><span data-stu-id="22d66-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="22d66-146">Met fin à cette définition partielle de `Class` ou de `Structure`.</span><span class="sxs-lookup"><span data-stu-id="22d66-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22d66-147">Notes</span><span class="sxs-lookup"><span data-stu-id="22d66-147">Remarks</span></span>  
 <span data-ttu-id="22d66-148">Visual Basic utilise des définitions de classe partielle pour séparer le code généré du code créé par l'utilisateur dans des fichiers sources distincts.</span><span class="sxs-lookup"><span data-stu-id="22d66-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="22d66-149">Par exemple, le **Concepteur Windows Form** définit des classes partielles pour des contrôles tels que <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="22d66-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="22d66-150">Vous ne devez pas modifier le code généré dans ces contrôles.</span><span class="sxs-lookup"><span data-stu-id="22d66-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="22d66-151">Toutes les règles de création de classes, structures, interfaces et modules, telles que celles relatives à l'héritage et à l'utilisation de modificateurs, s'appliquent lors de la création d'un type partiel.</span><span class="sxs-lookup"><span data-stu-id="22d66-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="22d66-152">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="22d66-152">Best Practices</span></span>  
  
- <span data-ttu-id="22d66-153">Dans des circonstances normales, vous ne devez pas scinder le développement d'un type unique entre deux déclarations ou plus.</span><span class="sxs-lookup"><span data-stu-id="22d66-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="22d66-154">Par conséquent, dans la plupart des cas, vous n'avez pas besoin du mot clé `Partial`.</span><span class="sxs-lookup"><span data-stu-id="22d66-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="22d66-155">Pour une meilleure lisibilité, chaque déclaration partielle d'un type doit inclure le mot clé `Partial`.</span><span class="sxs-lookup"><span data-stu-id="22d66-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="22d66-156">Le compilateur permet au plus à une déclaration partielle d'omettre le mot clé. Si deux déclarations ou plus l'omettent, le compilateur signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="22d66-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="22d66-157">Comportement</span><span class="sxs-lookup"><span data-stu-id="22d66-157">Behavior</span></span>  
  
- <span data-ttu-id="22d66-158">**Union de déclarations.**</span><span class="sxs-lookup"><span data-stu-id="22d66-158">**Union of Declarations.**</span></span> <span data-ttu-id="22d66-159">Le compilateur traite ce type comme l'union de toutes ses déclarations partielles.</span><span class="sxs-lookup"><span data-stu-id="22d66-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="22d66-160">Chaque modificateur issu de chaque définition partielle s'applique à l'ensemble du type, et chaque membre issu de chaque définition partielle est disponible pour l'ensemble du type.</span><span class="sxs-lookup"><span data-stu-id="22d66-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="22d66-161">**La promotion de type n’est pas autorisée pour les types partiels dans les modules.**</span><span class="sxs-lookup"><span data-stu-id="22d66-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="22d66-162">Si une définition partielle est comprise dans un module, la promotion de type de ce type est automatiquement annulée.</span><span class="sxs-lookup"><span data-stu-id="22d66-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="22d66-163">Dans ce cas, un ensemble de définitions partielles peut provoquer des résultats inattendus, voire même des erreurs du compilateur.</span><span class="sxs-lookup"><span data-stu-id="22d66-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="22d66-164">Pour plus d’informations, consultez [promotion de type](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="22d66-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="22d66-165">Le compilateur fusionne des définitions partielles uniquement lorsque leurs chemins qualifiés complets sont identiques.</span><span class="sxs-lookup"><span data-stu-id="22d66-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="22d66-166">Le mot clé `Partial` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="22d66-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="22d66-167">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="22d66-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="22d66-168">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="22d66-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="22d66-169">Exemple</span><span class="sxs-lookup"><span data-stu-id="22d66-169">Example</span></span>  
 <span data-ttu-id="22d66-170">L'exemple suivant fractionne la définition de la classe `sampleClass` en deux déclarations, dont chacune définit une procédure `Sub` différente.</span><span class="sxs-lookup"><span data-stu-id="22d66-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="22d66-171">Les deux définitions partielles de l'exemple précédent peuvent être dans le même fichier source ou dans deux fichiers sources différents.</span><span class="sxs-lookup"><span data-stu-id="22d66-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d66-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22d66-172">See also</span></span>

- [<span data-ttu-id="22d66-173">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="22d66-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="22d66-174">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="22d66-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="22d66-175">Promotion de type</span><span class="sxs-lookup"><span data-stu-id="22d66-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="22d66-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="22d66-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="22d66-177">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="22d66-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="22d66-178">Méthodes partielles</span><span class="sxs-lookup"><span data-stu-id="22d66-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
