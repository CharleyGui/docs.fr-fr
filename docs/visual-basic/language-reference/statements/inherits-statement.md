---
title: Inherits Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 6e6e9cc9210232059210862f2bda691c57b372d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353225"
---
# <a name="inherits-statement"></a><span data-ttu-id="12456-102">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="12456-102">Inherits Statement</span></span>
<span data-ttu-id="12456-103">Fait en sorte que la classe ou l’interface actuelle hérite des attributs, variables, propriétés, procédures et événements d’une autre classe ou d’un ensemble d’interfaces.</span><span class="sxs-lookup"><span data-stu-id="12456-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12456-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12456-104">Syntax</span></span>  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="12456-105">Composants</span><span class="sxs-lookup"><span data-stu-id="12456-105">Parts</span></span>  
  
|<span data-ttu-id="12456-106">Terme</span><span class="sxs-lookup"><span data-stu-id="12456-106">Term</span></span>|<span data-ttu-id="12456-107">Définition</span><span class="sxs-lookup"><span data-stu-id="12456-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="12456-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="12456-108">Required.</span></span> <span data-ttu-id="12456-109">Nom de la classe dont cette classe est dérivée.</span><span class="sxs-lookup"><span data-stu-id="12456-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="12456-110">-ou-</span><span class="sxs-lookup"><span data-stu-id="12456-110">-or-</span></span><br /><br /> <span data-ttu-id="12456-111">Noms des interfaces à partir desquelles cette interface est dérivée.</span><span class="sxs-lookup"><span data-stu-id="12456-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="12456-112">Utilisez des virgules pour séparer plusieurs noms.</span><span class="sxs-lookup"><span data-stu-id="12456-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12456-113">Notes</span><span class="sxs-lookup"><span data-stu-id="12456-113">Remarks</span></span>  
 <span data-ttu-id="12456-114">En cas d’utilisation, l’instruction `Inherits` doit être la première ligne non vide et sans commentaire dans une définition de classe ou d’interface.</span><span class="sxs-lookup"><span data-stu-id="12456-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="12456-115">Elle doit suivre immédiatement l’instruction `Class` ou `Interface`.</span><span class="sxs-lookup"><span data-stu-id="12456-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="12456-116">Vous pouvez utiliser `Inherits` uniquement dans une classe ou une interface.</span><span class="sxs-lookup"><span data-stu-id="12456-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="12456-117">Cela signifie que le contexte de déclaration pour un héritage ne peut pas être un fichier source, un espace de noms, une structure, un module, une procédure ou un bloc.</span><span class="sxs-lookup"><span data-stu-id="12456-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="12456-118">Règles</span><span class="sxs-lookup"><span data-stu-id="12456-118">Rules</span></span>  
  
- <span data-ttu-id="12456-119">**Héritage de classe.**</span><span class="sxs-lookup"><span data-stu-id="12456-119">**Class Inheritance.**</span></span> <span data-ttu-id="12456-120">Si une classe utilise l’instruction `Inherits`, vous ne pouvez spécifier qu’une seule classe de base.</span><span class="sxs-lookup"><span data-stu-id="12456-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="12456-121">Une classe ne peut pas hériter d’une classe imbriquée dans celle-ci.</span><span class="sxs-lookup"><span data-stu-id="12456-121">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="12456-122">**Héritage de l’interface.**</span><span class="sxs-lookup"><span data-stu-id="12456-122">**Interface Inheritance.**</span></span> <span data-ttu-id="12456-123">Si une interface utilise l’instruction `Inherits`, vous pouvez spécifier une ou plusieurs interfaces de base.</span><span class="sxs-lookup"><span data-stu-id="12456-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="12456-124">Vous pouvez hériter de deux interfaces, même si elles définissent un membre portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="12456-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="12456-125">Dans ce cas, le code d’implémentation doit utiliser la qualification de nom pour spécifier le membre qu’il implémente.</span><span class="sxs-lookup"><span data-stu-id="12456-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="12456-126">Une interface ne peut pas hériter d’une autre interface avec un niveau d’accès plus restrictif.</span><span class="sxs-lookup"><span data-stu-id="12456-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="12456-127">Par exemple, une interface de `Public` ne peut pas hériter d’une interface `Friend`.</span><span class="sxs-lookup"><span data-stu-id="12456-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="12456-128">Une interface ne peut pas hériter d’une interface imbriquée dans celle-ci.</span><span class="sxs-lookup"><span data-stu-id="12456-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="12456-129">Un exemple d’héritage de classe dans le .NET Framework est la classe <xref:System.ArgumentException>, qui hérite de la classe <xref:System.SystemException>.</span><span class="sxs-lookup"><span data-stu-id="12456-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="12456-130">Cela permet d' <xref:System.ArgumentException> toutes les propriétés prédéfinies et les procédures requises par les exceptions système, telles que la propriété <xref:System.Exception.Message%2A> et la méthode <xref:System.Exception.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="12456-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="12456-131">Un exemple d’héritage d’interface dans le .NET Framework est l’interface <xref:System.Collections.ICollection>, qui hérite de l’interface <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="12456-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="12456-132">En conséquence, <xref:System.Collections.ICollection> hérite de la définition de l’énumérateur requis pour traverser une collection.</span><span class="sxs-lookup"><span data-stu-id="12456-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12456-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="12456-133">Example</span></span>  
 <span data-ttu-id="12456-134">L’exemple suivant utilise l’instruction `Inherits` pour montrer comment une classe nommée `thisClass` peut hériter de tous les membres d’une classe de base nommée `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="12456-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="12456-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="12456-135">Example</span></span>  
 <span data-ttu-id="12456-136">L’exemple suivant illustre l’héritage de plusieurs interfaces.</span><span class="sxs-lookup"><span data-stu-id="12456-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 <span data-ttu-id="12456-137">L’interface nommée `thisInterface` comprend désormais toutes les définitions des interfaces <xref:System.IComparable>, <xref:System.IDisposable>et <xref:System.IFormattable> que les membres hérités fournissent respectivement pour la comparaison spécifique au type de deux objets, la libération des ressources allouées et l’expression de la valeur d’un objet en tant que `String`.</span><span class="sxs-lookup"><span data-stu-id="12456-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="12456-138">Une classe qui implémente `thisInterface` doit implémenter chaque membre de chaque interface de base.</span><span class="sxs-lookup"><span data-stu-id="12456-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12456-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12456-139">See also</span></span>

- [<span data-ttu-id="12456-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="12456-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="12456-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="12456-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="12456-142">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="12456-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="12456-143">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="12456-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="12456-144">Interfaces</span><span class="sxs-lookup"><span data-stu-id="12456-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
