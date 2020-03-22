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
ms.openlocfilehash: 20a33478f622fca6d3183772f53dcb3e72f79409
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266883"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="d3336-102">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3336-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="d3336-103">Lorsque deux éléments de programmation partagent le même nom, l’un d’eux peut se cacher, ou *l’ombre*, l’autre.</span><span class="sxs-lookup"><span data-stu-id="d3336-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="d3336-104">Dans une telle situation, l’élément ombragé n’est pas disponible pour référence; au lieu de cela, lorsque votre code utilise le nom de l’élément, le compilateur Visual Basic le résout à l’élément d’observation.</span><span class="sxs-lookup"><span data-stu-id="d3336-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="d3336-105">Objectif</span><span class="sxs-lookup"><span data-stu-id="d3336-105">Purpose</span></span>  
 <span data-ttu-id="d3336-106">Le but principal de l’ombre est de protéger la définition des membres de votre classe.</span><span class="sxs-lookup"><span data-stu-id="d3336-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="d3336-107">La classe de base peut subir un changement qui crée un élément avec le même nom que celui que vous avez déjà défini.</span><span class="sxs-lookup"><span data-stu-id="d3336-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="d3336-108">Si cela se `Shadows` produit, le modificateur force les références à travers votre classe à être résolues au membre que vous avez défini, au lieu du nouvel élément de classe de base.</span><span class="sxs-lookup"><span data-stu-id="d3336-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="d3336-109">Types d’ombre</span><span class="sxs-lookup"><span data-stu-id="d3336-109">Types of Shadowing</span></span>  
 <span data-ttu-id="d3336-110">Un élément peut ombrer un autre élément de deux façons différentes.</span><span class="sxs-lookup"><span data-stu-id="d3336-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="d3336-111">L’élément d’ombre peut être déclaré à l’intérieur d’une sous-région de la région contenant l’élément ombragé, auquel cas l’ombre est accomplie *par la portée*.</span><span class="sxs-lookup"><span data-stu-id="d3336-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="d3336-112">Ou une classe de dériving peut redéfinir un membre d’une classe de base, auquel cas l’ombre se fait *par l’héritage*.</span><span class="sxs-lookup"><span data-stu-id="d3336-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="d3336-113">Ombre à travers la portée</span><span class="sxs-lookup"><span data-stu-id="d3336-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="d3336-114">Il est possible que les éléments de programmation d’un même module, d’une même classe ou d’une même structure aient le même nom mais une portée différente.</span><span class="sxs-lookup"><span data-stu-id="d3336-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="d3336-115">Lorsque deux éléments sont déclarés de cette manière et que le code fait référence au nom qu’ils partagent, l’élément avec la portée plus étroite ombre l’autre élément (la portée de bloc est la plus étroite).</span><span class="sxs-lookup"><span data-stu-id="d3336-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="d3336-116">Par exemple, un module `Public` peut `temp`définir une variable nommée , et une `temp`procédure au sein du module peut déclarer une variable locale également nommée .</span><span class="sxs-lookup"><span data-stu-id="d3336-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="d3336-117">Les `temp` références à partir de l’intérieur `temp` de la procédure `Public` accèdent à la variable locale, tandis que les références à partir de l’extérieur de la procédure accèdent à la variable.</span><span class="sxs-lookup"><span data-stu-id="d3336-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="d3336-118">Dans ce cas, `temp` la variable de `temp`procédure ombres de la variable du module .</span><span class="sxs-lookup"><span data-stu-id="d3336-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="d3336-119">L’illustration suivante montre deux `temp`variables, toutes deux nommées .</span><span class="sxs-lookup"><span data-stu-id="d3336-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="d3336-120">La variable `temp` locale ombre `temp` la variable du membre `p`lorsqu’elle est accessible à partir de sa propre procédure .</span><span class="sxs-lookup"><span data-stu-id="d3336-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="d3336-121">Cependant, `MyClass` le mot clé contourne l’ombre et accède à la variable du membre.</span><span class="sxs-lookup"><span data-stu-id="d3336-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![Graphique qui montre l’ombre à travers la portée.](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="d3336-123">Pour un exemple d’ombre à travers la portée, voir [Comment: Cacher une variable avec le même nom que votre variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="d3336-123">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="d3336-124">Ombre par l’héritage</span><span class="sxs-lookup"><span data-stu-id="d3336-124">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="d3336-125">Si une classe dérivée redéfinit un élément de programmation hérité d’une classe de base, l’élément de redéfinition ombre l’élément original.</span><span class="sxs-lookup"><span data-stu-id="d3336-125">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="d3336-126">Vous pouvez suivre n’importe quel type d’élément déclaré, ou ensemble d’éléments surchargés, avec n’importe quel autre type.</span><span class="sxs-lookup"><span data-stu-id="d3336-126">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="d3336-127">Par exemple, `Integer` une variable `Function` peut ombrer une procédure.</span><span class="sxs-lookup"><span data-stu-id="d3336-127">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="d3336-128">Si vous faites de l’ombre à une procédure avec une autre procédure, vous pouvez utiliser une liste de paramètres différente et un type de retour différent.</span><span class="sxs-lookup"><span data-stu-id="d3336-128">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="d3336-129">L’illustration suivante montre `b` une classe `d` de base `b`et une classe dérivée qui hérite de .</span><span class="sxs-lookup"><span data-stu-id="d3336-129">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="d3336-130">La classe de base `proc`définit une procédure nommée , et la classe dérivée l’ombre avec une autre procédure du même nom.</span><span class="sxs-lookup"><span data-stu-id="d3336-130">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="d3336-131">La `Call` première déclaration accède `proc` à l’ombre dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="d3336-131">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="d3336-132">Cependant, `MyBase` le mot clé contourne l’ombre et accède à la procédure ombragée dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="d3336-132">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![Diagramme graphique d'une occultation par héritage](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="d3336-134">Par exemple de l’ombre à travers l’héritage, voir [Comment: Cacher une variable avec le même nom que votre variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) et [comment: Cacher une variable héritée](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="d3336-134">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="d3336-135">Niveau d’ombre et d’accès</span><span class="sxs-lookup"><span data-stu-id="d3336-135">Shadowing and Access Level</span></span>  
 <span data-ttu-id="d3336-136">L’élément d’ombre n’est pas toujours accessible à partir du code à l’aide de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="d3336-136">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="d3336-137">Par exemple, il `Private`peut être déclaré .</span><span class="sxs-lookup"><span data-stu-id="d3336-137">For example, it might be declared `Private`.</span></span> <span data-ttu-id="d3336-138">Dans un tel cas, l’ombre est vaincue et le compilateur résout toute référence au même élément qu’il aurait si il n’y avait pas eu d’ombre.</span><span class="sxs-lookup"><span data-stu-id="d3336-138">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="d3336-139">Cet élément est l’élément accessible le moins de pas dérivationnels en arrière de la classe d’ombre.</span><span class="sxs-lookup"><span data-stu-id="d3336-139">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="d3336-140">Si l’élément ombragé est une procédure, la résolution est à la version la plus proche accessible avec le même nom, la liste de paramètres, et le type de retour.</span><span class="sxs-lookup"><span data-stu-id="d3336-140">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="d3336-141">L’exemple suivant montre une hiérarchie successorale de trois classes.</span><span class="sxs-lookup"><span data-stu-id="d3336-141">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="d3336-142">Chaque classe définit `Sub` `display`une procédure, et chaque `display` classe dérivée ombre la procédure dans sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="d3336-142">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
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
  
 <span data-ttu-id="d3336-143">Dans l’exemple précédent, `secondClass` la `display` classe `Private` dérivée s’ombre à une procédure.</span><span class="sxs-lookup"><span data-stu-id="d3336-143">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="d3336-144">Lorsque `callDisplay` le `display` `secondClass`module appelle, le `secondClass` code d’appel `display` est à l’extérieur et ne peut donc pas accéder à la procédure privée.</span><span class="sxs-lookup"><span data-stu-id="d3336-144">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="d3336-145">L’ombre est vaincue, et le compilateur `display` résout la référence à la procédure de classe de base.</span><span class="sxs-lookup"><span data-stu-id="d3336-145">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="d3336-146">Cependant, la classe `thirdClass` dérivée `Public`plus loin `callDisplay` déclare `display` comme , de sorte que le code dans peut y accéder.</span><span class="sxs-lookup"><span data-stu-id="d3336-146">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="d3336-147">Ombre et prépondérer</span><span class="sxs-lookup"><span data-stu-id="d3336-147">Shadowing and Overriding</span></span>  
 <span data-ttu-id="d3336-148">Ne confondez pas l’ombre avec le prépondérer.</span><span class="sxs-lookup"><span data-stu-id="d3336-148">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="d3336-149">Les deux sont utilisés lorsqu’une classe dérivée d’une classe de base, et les deux redéfinissent un élément déclaré avec un autre.</span><span class="sxs-lookup"><span data-stu-id="d3336-149">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="d3336-150">Mais il y a des différences significatives entre les deux.</span><span class="sxs-lookup"><span data-stu-id="d3336-150">But there are significant differences between the two.</span></span> <span data-ttu-id="d3336-151">Pour une comparaison, voir [Différences entre l’ombre et l’avant](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="d3336-151">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="d3336-152">Ombre et surcharge</span><span class="sxs-lookup"><span data-stu-id="d3336-152">Shadowing and Overloading</span></span>  
 <span data-ttu-id="d3336-153">Si vous ombrez le même élément de classe de base avec plus d’un élément dans votre classe dérivée, les éléments d’ombre deviennent des versions surchargées de cet élément.</span><span class="sxs-lookup"><span data-stu-id="d3336-153">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="d3336-154">Pour plus d'informations, consultez [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="d3336-154">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="d3336-155">Accès à un élément ombragé</span><span class="sxs-lookup"><span data-stu-id="d3336-155">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="d3336-156">Lorsque vous accédez à un élément d’une classe dérivée, vous le faites normalement `Me` à travers l’instance actuelle de cette catégorie dérivée, en qualifiant le nom de l’élément avec le mot clé.</span><span class="sxs-lookup"><span data-stu-id="d3336-156">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="d3336-157">Si votre classe dérivée ombre l’élément dans la classe de base, `MyBase` vous pouvez accéder à l’élément de classe de base en le qualifiant avec le mot clé.</span><span class="sxs-lookup"><span data-stu-id="d3336-157">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="d3336-158">Par exemple d’accès à un élément ombragé, voir [Comment : Accéder à une variable cachée par une classe dérivée](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="d3336-158">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="d3336-159">Déclaration de la variable d’objet</span><span class="sxs-lookup"><span data-stu-id="d3336-159">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="d3336-160">La façon dont vous créez la variable d’objet peut également affecter si la classe dérivée accède à un élément d’ombre ou à l’élément ombragé.</span><span class="sxs-lookup"><span data-stu-id="d3336-160">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="d3336-161">L’exemple suivant crée deux objets d’une classe dérivée, mais un objet est déclaré comme la classe de base et l’autre comme la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="d3336-161">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
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
  
 <span data-ttu-id="d3336-162">Dans l’exemple précédent, la variable `basObj` est déclarée classe de base.</span><span class="sxs-lookup"><span data-stu-id="d3336-162">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="d3336-163">L’attribution `dervCls` d’un objet constitue une conversion croissante et est donc valide.</span><span class="sxs-lookup"><span data-stu-id="d3336-163">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="d3336-164">Cependant, la classe de base ne peut `z` pas accéder à la version d’ombre de la variable dans la classe dérivée, de sorte que le compilateur se résout `basObj.z` à la valeur de la classe de base d’origine.</span><span class="sxs-lookup"><span data-stu-id="d3336-164">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3336-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3336-165">See also</span></span>

- [<span data-ttu-id="d3336-166">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="d3336-166">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="d3336-167">Portée dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3336-167">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="d3336-168">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="d3336-168">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="d3336-169">Shadows</span><span class="sxs-lookup"><span data-stu-id="d3336-169">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="d3336-170">Remplace</span><span class="sxs-lookup"><span data-stu-id="d3336-170">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="d3336-171">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="d3336-171">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="d3336-172">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="d3336-172">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
