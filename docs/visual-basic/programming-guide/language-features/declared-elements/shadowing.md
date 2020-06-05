---
title: Copie shadow
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 7d76e2e7398c2f954ff4274f77ffa350efbd3617
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410745"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="2090c-102">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2090c-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="2090c-103">Lorsque deux éléments de programmation partagent le même nom, l’un d’eux peut masquer ou *occulter*l’autre.</span><span class="sxs-lookup"><span data-stu-id="2090c-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="2090c-104">Dans ce cas, l’élément occulté n’est pas disponible à des fins de référence ; au lieu de cela, lorsque votre code utilise le nom d’élément, le compilateur Visual Basic le résout en l’élément d’occultation.</span><span class="sxs-lookup"><span data-stu-id="2090c-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="2090c-105">Objectif</span><span class="sxs-lookup"><span data-stu-id="2090c-105">Purpose</span></span>  
 <span data-ttu-id="2090c-106">L’objectif principal de l’occultation est de protéger la définition de vos membres de classe.</span><span class="sxs-lookup"><span data-stu-id="2090c-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="2090c-107">La classe de base peut subir une modification qui crée un élément avec le même nom que celui que vous avez déjà défini.</span><span class="sxs-lookup"><span data-stu-id="2090c-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="2090c-108">Dans ce cas, le `Shadows` modificateur force les références via votre classe à être résolues vers le membre que vous avez défini, et non vers le nouvel élément de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="2090c-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="2090c-109">Types d’occultation</span><span class="sxs-lookup"><span data-stu-id="2090c-109">Types of Shadowing</span></span>  
 <span data-ttu-id="2090c-110">Un élément peut occulter un autre élément de deux façons différentes.</span><span class="sxs-lookup"><span data-stu-id="2090c-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="2090c-111">L’élément d’occultation peut être déclaré à l’intérieur d’une sous-région de la région contenant l’élément occulté, auquel cas l’occultation s’effectue *par le biais*de l’étendue.</span><span class="sxs-lookup"><span data-stu-id="2090c-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="2090c-112">Ou une classe dérivée peut redéfinir un membre d’une classe de base, auquel cas l’occultation s’effectue *par le biais*de l’héritage.</span><span class="sxs-lookup"><span data-stu-id="2090c-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="2090c-113">Occultation par portée</span><span class="sxs-lookup"><span data-stu-id="2090c-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="2090c-114">Il est possible que des éléments de programmation dans le même module, la même classe ou la même structure aient le même nom mais une portée différente.</span><span class="sxs-lookup"><span data-stu-id="2090c-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="2090c-115">Lorsque deux éléments sont déclarés de cette manière et que le code fait référence au nom qu’ils partagent, l’élément avec la portée plus étroite occulte l’autre élément (la portée de bloc est la plus étroite).</span><span class="sxs-lookup"><span data-stu-id="2090c-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="2090c-116">Par exemple, un module peut définir une `Public` variable nommée `temp` , et une procédure dans le module peut déclarer une variable locale également nommée `temp` .</span><span class="sxs-lookup"><span data-stu-id="2090c-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="2090c-117">Les références à à `temp` partir de la procédure accèdent à la variable locale, tandis que les références à `temp` depuis l’extérieur de la procédure accèdent à la `Public` variable.</span><span class="sxs-lookup"><span data-stu-id="2090c-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="2090c-118">Dans ce cas, la variable de procédure `temp` occulte la variable de module `temp` .</span><span class="sxs-lookup"><span data-stu-id="2090c-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="2090c-119">L’illustration suivante montre deux variables, toutes deux nommées `temp` .</span><span class="sxs-lookup"><span data-stu-id="2090c-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="2090c-120">La variable locale `temp` occulte la variable membre lorsqu’elle est `temp` accessible à partir de sa propre procédure `p` .</span><span class="sxs-lookup"><span data-stu-id="2090c-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="2090c-121">Toutefois, le `MyClass` mot clé contourne l’occultation et accède à la variable membre.</span><span class="sxs-lookup"><span data-stu-id="2090c-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![Graphique illustrant l’occultation par le biais de l’étendue.](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="2090c-123">Pour obtenir un exemple d’occultation par le biais de l’étendue, consultez [Comment : masquer une variable portant le même nom que votre variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="2090c-123">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="2090c-124">Occultation par héritage</span><span class="sxs-lookup"><span data-stu-id="2090c-124">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="2090c-125">Si une classe dérivée redéfinit un élément de programmation hérité d’une classe de base, l’élément redéfinissant occulte l’élément d’origine.</span><span class="sxs-lookup"><span data-stu-id="2090c-125">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="2090c-126">Vous pouvez occulter tout type d’élément déclaré, ou un ensemble d’éléments surchargés, avec n’importe quel autre type.</span><span class="sxs-lookup"><span data-stu-id="2090c-126">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="2090c-127">Par exemple, une `Integer` variable peut masquer une `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="2090c-127">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="2090c-128">Si vous occultez une procédure à l’aide d’une autre procédure, vous pouvez utiliser une liste de paramètres différente et un type de retour différent.</span><span class="sxs-lookup"><span data-stu-id="2090c-128">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="2090c-129">L’illustration suivante montre une classe de base `b` et une classe dérivée `d` qui hérite de `b` .</span><span class="sxs-lookup"><span data-stu-id="2090c-129">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="2090c-130">La classe de base définit une procédure nommée `proc` , et la classe dérivée l’occulte avec une autre procédure portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="2090c-130">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="2090c-131">La première `Call` instruction accède à l’occultation `proc` dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="2090c-131">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="2090c-132">Toutefois, le `MyBase` mot clé contourne l’occultation et accède à la procédure occultée dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="2090c-132">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![Diagramme graphique d'une occultation par héritage](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="2090c-134">Pour obtenir un exemple d’occultation par héritage, consultez [Comment : masquer une variable portant le même nom que votre variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) et [Comment : masquer une variable héritée](how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="2090c-134">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="2090c-135">Cliché instantané et niveau d’accès</span><span class="sxs-lookup"><span data-stu-id="2090c-135">Shadowing and Access Level</span></span>  
 <span data-ttu-id="2090c-136">L’élément d’occultation n’est pas toujours accessible à partir du code à l’aide de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="2090c-136">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="2090c-137">Par exemple, il peut être déclaré `Private` .</span><span class="sxs-lookup"><span data-stu-id="2090c-137">For example, it might be declared `Private`.</span></span> <span data-ttu-id="2090c-138">Dans ce cas, l’occultation est invalidée et le compilateur résout toute référence au même élément qu’il aurait si aucune occultation n’avait été apportée.</span><span class="sxs-lookup"><span data-stu-id="2090c-138">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="2090c-139">Cet élément est l’élément accessible le moins d’étapes de dérivation à partir de la classe d’occultation.</span><span class="sxs-lookup"><span data-stu-id="2090c-139">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="2090c-140">Si l’élément occulté est une procédure, la résolution est la version la plus proche accessible avec le même nom, la même liste de paramètres et le même type de retour.</span><span class="sxs-lookup"><span data-stu-id="2090c-140">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="2090c-141">L’exemple suivant montre une hiérarchie d’héritage de trois classes.</span><span class="sxs-lookup"><span data-stu-id="2090c-141">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="2090c-142">Chaque classe définit une `Sub` procédure `display` , et chaque classe dérivée occulte la `display` procédure dans sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="2090c-142">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
```vb  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="2090c-143">Dans l’exemple précédent, la classe dérivée `secondClass` occulte `display` avec une `Private` procédure.</span><span class="sxs-lookup"><span data-stu-id="2090c-143">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="2090c-144">Quand `callDisplay` le module appelle `display` dans `secondClass` , le code appelant est en dehors `secondClass` de et, par conséquent, ne peut pas accéder à la procédure privée `display` .</span><span class="sxs-lookup"><span data-stu-id="2090c-144">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="2090c-145">L’occultation est invalidée et le compilateur résout la référence à la procédure de classe de base `display` .</span><span class="sxs-lookup"><span data-stu-id="2090c-145">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="2090c-146">Toutefois, la classe dérivée supplémentaire `thirdClass` déclare `display` comme `Public` , donc le code de `callDisplay` peut y accéder.</span><span class="sxs-lookup"><span data-stu-id="2090c-146">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="2090c-147">Occultation et substitution</span><span class="sxs-lookup"><span data-stu-id="2090c-147">Shadowing and Overriding</span></span>  
 <span data-ttu-id="2090c-148">Ne confondez pas l’occultation et la substitution.</span><span class="sxs-lookup"><span data-stu-id="2090c-148">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="2090c-149">Les deux sont utilisés lorsqu’une classe dérivée hérite d’une classe de base, et redéfinissent tous deux un élément déclaré avec un autre.</span><span class="sxs-lookup"><span data-stu-id="2090c-149">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="2090c-150">Mais il existe des différences significatives entre les deux.</span><span class="sxs-lookup"><span data-stu-id="2090c-150">But there are significant differences between the two.</span></span> <span data-ttu-id="2090c-151">Pour obtenir une comparaison, consultez [différences entre l’occultation et la substitution](differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="2090c-151">For a comparison, see [Differences Between Shadowing and Overriding](differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="2090c-152">Occultation et surcharge</span><span class="sxs-lookup"><span data-stu-id="2090c-152">Shadowing and Overloading</span></span>  
 <span data-ttu-id="2090c-153">Si vous occultez le même élément de classe de base avec plusieurs éléments dans votre classe dérivée, les éléments d’occultation deviennent des versions surchargées de cet élément.</span><span class="sxs-lookup"><span data-stu-id="2090c-153">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="2090c-154">Pour plus d'informations, consultez [Procedure Overloading](../procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="2090c-154">For more information, see [Procedure Overloading](../procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="2090c-155">Accès à un élément occulté</span><span class="sxs-lookup"><span data-stu-id="2090c-155">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="2090c-156">Lorsque vous accédez à un élément à partir d’une classe dérivée, vous le faites normalement via l’instance actuelle de cette classe dérivée, en qualifiant le nom de l’élément avec le `Me` mot clé.</span><span class="sxs-lookup"><span data-stu-id="2090c-156">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="2090c-157">Si votre classe dérivée occulte l’élément dans la classe de base, vous pouvez accéder à l’élément de classe de base en le qualifiant avec le `MyBase` mot clé.</span><span class="sxs-lookup"><span data-stu-id="2090c-157">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="2090c-158">Pour obtenir un exemple d’accès à un élément occulté, consultez [Comment : accéder à une variable masquée par une classe dérivée](how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="2090c-158">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="2090c-159">Déclaration de la variable objet</span><span class="sxs-lookup"><span data-stu-id="2090c-159">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="2090c-160">La façon dont vous créez la variable objet peut également affecter si la classe dérivée accède à un élément occultant ou à l’élément occulté.</span><span class="sxs-lookup"><span data-stu-id="2090c-160">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="2090c-161">L’exemple suivant crée deux objets à partir d’une classe dérivée, mais un objet est déclaré comme classe de base et l’autre comme classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="2090c-161">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
```vb  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="2090c-162">Dans l’exemple précédent, la variable `basObj` est déclarée en tant que classe de base.</span><span class="sxs-lookup"><span data-stu-id="2090c-162">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="2090c-163">L’assignation `dervCls` d’un objet à celle-ci constitue une conversion étendue et est donc valide.</span><span class="sxs-lookup"><span data-stu-id="2090c-163">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="2090c-164">Toutefois, la classe de base ne peut pas accéder à la version occultante de la variable `z` dans la classe dérivée, de sorte que le compilateur se résout `basObj.z` en la valeur de la classe de base d’origine.</span><span class="sxs-lookup"><span data-stu-id="2090c-164">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2090c-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2090c-165">See also</span></span>

- [<span data-ttu-id="2090c-166">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="2090c-166">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="2090c-167">Portée dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2090c-167">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="2090c-168">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="2090c-168">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="2090c-169">Shadows</span><span class="sxs-lookup"><span data-stu-id="2090c-169">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="2090c-170">Remplacements</span><span class="sxs-lookup"><span data-stu-id="2090c-170">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="2090c-171">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="2090c-171">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="2090c-172">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="2090c-172">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
