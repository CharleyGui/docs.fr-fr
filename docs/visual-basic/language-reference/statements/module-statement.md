---
title: Module, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 73d4a5cc8fd4bad41ead1fda830504b19877a8d8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625469"
---
# <a name="module-statement"></a><span data-ttu-id="43944-102">Module, instruction</span><span class="sxs-lookup"><span data-stu-id="43944-102">Module Statement</span></span>
<span data-ttu-id="43944-103">Déclare le nom d’un module et introduit la définition des variables, propriétés, événements et procédures contenus dans le module.</span><span class="sxs-lookup"><span data-stu-id="43944-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43944-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43944-104">Syntax</span></span>  
  
```vb 
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a><span data-ttu-id="43944-105">Composants</span><span class="sxs-lookup"><span data-stu-id="43944-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="43944-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="43944-106">Optional.</span></span> <span data-ttu-id="43944-107">Consultez [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="43944-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="43944-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="43944-108">Optional.</span></span> <span data-ttu-id="43944-109">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="43944-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="43944-110">Public</span><span class="sxs-lookup"><span data-stu-id="43944-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
- [<span data-ttu-id="43944-111">Friend</span><span class="sxs-lookup"><span data-stu-id="43944-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 <span data-ttu-id="43944-112">Consultez [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="43944-112">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `name`  
 <span data-ttu-id="43944-113">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="43944-113">Required.</span></span> <span data-ttu-id="43944-114">Nom de ce module.</span><span class="sxs-lookup"><span data-stu-id="43944-114">Name of this module.</span></span> <span data-ttu-id="43944-115">Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="43944-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `statements`  
 <span data-ttu-id="43944-116">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="43944-116">Optional.</span></span> <span data-ttu-id="43944-117">Instructions qui définissent des variables, propriétés, événements, procédures et les types imbriqués de ce module.</span><span class="sxs-lookup"><span data-stu-id="43944-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>  
  
 `End Module`  
 <span data-ttu-id="43944-118">Met fin à la `Module` définition.</span><span class="sxs-lookup"><span data-stu-id="43944-118">Terminates the `Module` definition.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43944-119">Notes</span><span class="sxs-lookup"><span data-stu-id="43944-119">Remarks</span></span>  
 <span data-ttu-id="43944-120">Un `Module` instruction définit un type de référence disponible tout au long de son espace de noms.</span><span class="sxs-lookup"><span data-stu-id="43944-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="43944-121">Un *module* (parfois appelé un *module standard*) est similaire à une classe, mais avec certaines des différences importantes.</span><span class="sxs-lookup"><span data-stu-id="43944-121">A *module* (sometimes called a *standard module*)is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="43944-122">Chaque module possède exactement une instance et pas nécessairement être créées ou assignées à une variable.</span><span class="sxs-lookup"><span data-stu-id="43944-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="43944-123">Les modules ne prennent en charge l’héritage ou implémenter des interfaces.</span><span class="sxs-lookup"><span data-stu-id="43944-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="43944-124">Notez qu’un module n’est pas un *type* en ce sens qu’une classe ou structure est — vous ne pouvez pas déclarer un élément de programmation comme ayant le type de données d’un module.</span><span class="sxs-lookup"><span data-stu-id="43944-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>  
  
 <span data-ttu-id="43944-125">Vous pouvez utiliser `Module` uniquement au niveau de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="43944-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="43944-126">Cela signifie que le *contexte de déclaration* pour un module doit être un fichier source ou un espace de noms et ne peut pas être une classe, structure, module, interface, procédure ou bloc.</span><span class="sxs-lookup"><span data-stu-id="43944-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="43944-127">Vous ne pouvez pas imbriquer un module dans un autre module, ou dans n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="43944-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="43944-128">Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="43944-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="43944-129">Un module a la même durée de vie en tant que votre programme.</span><span class="sxs-lookup"><span data-stu-id="43944-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="43944-130">Étant donné que ses membres sont tous `Shared`, ils ont également des durées de vie égales à celle du programme.</span><span class="sxs-lookup"><span data-stu-id="43944-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>  
  
 <span data-ttu-id="43944-131">Modules par défaut à [Friend](../../../visual-basic/language-reference/modifiers/friend.md) accès.</span><span class="sxs-lookup"><span data-stu-id="43944-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span></span> <span data-ttu-id="43944-132">Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès.</span><span class="sxs-lookup"><span data-stu-id="43944-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="43944-133">Pour plus d’informations, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="43944-133">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="43944-134">Tous les membres d’un module sont implicitement `Shared`.</span><span class="sxs-lookup"><span data-stu-id="43944-134">All members of a module are implicitly `Shared`.</span></span>  
  
## <a name="classes-and-modules"></a><span data-ttu-id="43944-135">Classes et les Modules</span><span class="sxs-lookup"><span data-stu-id="43944-135">Classes and Modules</span></span>  
 <span data-ttu-id="43944-136">Ces éléments présentent beaucoup de similitudes, mais il existe également des différences importantes.</span><span class="sxs-lookup"><span data-stu-id="43944-136">These elements have many similarities, but there are some important differences as well.</span></span>  
  
- <span data-ttu-id="43944-137">**Terminologie.**</span><span class="sxs-lookup"><span data-stu-id="43944-137">**Terminology.**</span></span> <span data-ttu-id="43944-138">Les versions précédentes de Visual Basic reconnaissent deux types de modules : *modules de classe* (fichiers .cls) et *modules standard* (fichiers .bas).</span><span class="sxs-lookup"><span data-stu-id="43944-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="43944-139">La version actuelle appelle ces *classes* et *modules*, respectivement.</span><span class="sxs-lookup"><span data-stu-id="43944-139">The current version calls these *classes* and *modules*, respectively.</span></span>  
  
- <span data-ttu-id="43944-140">**Membres partagés.**</span><span class="sxs-lookup"><span data-stu-id="43944-140">**Shared Members.**</span></span> <span data-ttu-id="43944-141">Vous pouvez contrôler si un membre d’une classe est une connexion partagée ou membre d’instance.</span><span class="sxs-lookup"><span data-stu-id="43944-141">You can control whether a member of a class is a shared or instance member.</span></span>  
  
- <span data-ttu-id="43944-142">**Orientation de l’objet.**</span><span class="sxs-lookup"><span data-stu-id="43944-142">**Object Orientation.**</span></span> <span data-ttu-id="43944-143">Les classes sont orientés objet, mais les modules ne sont pas.</span><span class="sxs-lookup"><span data-stu-id="43944-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="43944-144">Par conséquent, seules les classes peuvent être instanciés en tant qu’objets.</span><span class="sxs-lookup"><span data-stu-id="43944-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="43944-145">Pour plus d’informations, consultez [objets et Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="43944-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="43944-146">Règles</span><span class="sxs-lookup"><span data-stu-id="43944-146">Rules</span></span>  
  
- <span data-ttu-id="43944-147">**Modificateurs.**</span><span class="sxs-lookup"><span data-stu-id="43944-147">**Modifiers.**</span></span> <span data-ttu-id="43944-148">Tous les membres de module sont implicitement [partagé](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="43944-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="43944-149">Vous ne pouvez pas utiliser le `Shared` mot clé lors de la déclaration d’un membre et vous ne pouvez pas modifier l’état partagé d’un membre.</span><span class="sxs-lookup"><span data-stu-id="43944-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>  
  
- <span data-ttu-id="43944-150">**Héritage.**</span><span class="sxs-lookup"><span data-stu-id="43944-150">**Inheritance.**</span></span> <span data-ttu-id="43944-151">Un module ne peut pas hériter d’un type autre que <xref:System.Object>, à partir de quels tous les modules hériter.</span><span class="sxs-lookup"><span data-stu-id="43944-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="43944-152">En particulier, un module ne peut pas hériter d’un autre.</span><span class="sxs-lookup"><span data-stu-id="43944-152">In particular, one module cannot inherit from another.</span></span>  
  
     <span data-ttu-id="43944-153">Vous ne pouvez pas utiliser le [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) dans une définition de module, même pour spécifier <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="43944-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="43944-154">**Propriété par défaut.**</span><span class="sxs-lookup"><span data-stu-id="43944-154">**Default Property.**</span></span> <span data-ttu-id="43944-155">Vous ne pouvez pas définir les propriétés par défaut dans un module.</span><span class="sxs-lookup"><span data-stu-id="43944-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="43944-156">Pour plus d’informations, consultez [par défaut](../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="43944-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="43944-157">Comportement</span><span class="sxs-lookup"><span data-stu-id="43944-157">Behavior</span></span>  
  
- <span data-ttu-id="43944-158">**Niveau d’accès.**</span><span class="sxs-lookup"><span data-stu-id="43944-158">**Access Level.**</span></span> <span data-ttu-id="43944-159">Dans un module, vous pouvez déclarer chaque membre avec son propre niveau d’accès.</span><span class="sxs-lookup"><span data-stu-id="43944-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="43944-160">Membres de module par défaut à [Public](../../../visual-basic/language-reference/modifiers/public.md) accéder, à l’exception des variables et des constantes, qui par défaut à [privé](../../../visual-basic/language-reference/modifiers/private.md) accès.</span><span class="sxs-lookup"><span data-stu-id="43944-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span></span> <span data-ttu-id="43944-161">Lorsqu’un module a accès plus limité qu’un de ses membres, le niveau d’accès de module spécifié est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="43944-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>  
  
- <span data-ttu-id="43944-162">**Étendue.**</span><span class="sxs-lookup"><span data-stu-id="43944-162">**Scope.**</span></span> <span data-ttu-id="43944-163">Un module est dans l’étendue tout au long de son espace de noms.</span><span class="sxs-lookup"><span data-stu-id="43944-163">A module is in scope throughout its namespace.</span></span>  
  
     <span data-ttu-id="43944-164">La portée de chaque membre de module est l’ensemble du module.</span><span class="sxs-lookup"><span data-stu-id="43944-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="43944-165">Notez que tous les membres subissent *promotion de type*, ce qui entraîne leur étendue de la promotion de l’espace de noms contenant le module.</span><span class="sxs-lookup"><span data-stu-id="43944-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="43944-166">Pour plus d’informations, consultez [Promotion de Type](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="43944-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
- <span data-ttu-id="43944-167">**Qualification.**</span><span class="sxs-lookup"><span data-stu-id="43944-167">**Qualification.**</span></span> <span data-ttu-id="43944-168">Vous pouvez avoir plusieurs modules dans un projet, et vous pouvez déclarer des membres portant le même nom dans deux ou plusieurs modules.</span><span class="sxs-lookup"><span data-stu-id="43944-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="43944-169">Toutefois, vous devez qualifier toute référence à ce membre avec le nom de module approprié si la référence est externe à ce module.</span><span class="sxs-lookup"><span data-stu-id="43944-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="43944-170">Pour plus d'informations, consultez [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="43944-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43944-171">Exemple</span><span class="sxs-lookup"><span data-stu-id="43944-171">Example</span></span>  
 [!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]  
  
## <a name="see-also"></a><span data-ttu-id="43944-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43944-172">See also</span></span>

- [<span data-ttu-id="43944-173">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="43944-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="43944-174">Namespace (instruction)</span><span class="sxs-lookup"><span data-stu-id="43944-174">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="43944-175">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="43944-175">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="43944-176">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="43944-176">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="43944-177">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="43944-177">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="43944-178">Promotion de type</span><span class="sxs-lookup"><span data-stu-id="43944-178">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
