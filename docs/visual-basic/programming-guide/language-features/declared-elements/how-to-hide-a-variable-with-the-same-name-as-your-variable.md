---
title: 'Comment : masquer une variable portant le même nom que votre variable'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: c1f4c2fbf339358be77e76468b1db94616bf04a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357230"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="f70f2-102">Comment : masquer une variable portant le même nom que votre variable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f70f2-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>

<span data-ttu-id="f70f2-103">Vous pouvez masquer une variable en l' *occultant* , c’est-à-dire en la redéfinissant avec une variable du même nom.</span><span class="sxs-lookup"><span data-stu-id="f70f2-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="f70f2-104">Vous pouvez occulter la variable que vous souhaitez masquer de deux manières :</span><span class="sxs-lookup"><span data-stu-id="f70f2-104">You can shadow the variable you want to hide in two ways:</span></span>

- <span data-ttu-id="f70f2-105">**Occultation par le biais de l’étendue.**</span><span class="sxs-lookup"><span data-stu-id="f70f2-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="f70f2-106">Vous pouvez l’occulter par le biais de la portée en le redéclarant dans une sous-région de la région contenant la variable que vous souhaitez masquer.</span><span class="sxs-lookup"><span data-stu-id="f70f2-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>

- <span data-ttu-id="f70f2-107">**Occultation par héritage.**</span><span class="sxs-lookup"><span data-stu-id="f70f2-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="f70f2-108">Si la variable que vous souhaitez masquer est définie au niveau de la classe, vous pouvez l’occulter via l’héritage en la redéclarant avec le mot clé [Shadows](../../../language-reference/modifiers/shadows.md) dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="f70f2-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>

## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="f70f2-109">Deux façons de masquer une variable</span><span class="sxs-lookup"><span data-stu-id="f70f2-109">Two Ways to Hide a Variable</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="f70f2-110">Pour masquer une variable en l’occultant par l’intermédiaire de la portée</span><span class="sxs-lookup"><span data-stu-id="f70f2-110">To hide a variable by shadowing it through scope</span></span>

1. <span data-ttu-id="f70f2-111">Déterminez la région définissant la variable que vous souhaitez masquer et déterminez une sous-région dans laquelle la redéfinir avec votre variable.</span><span class="sxs-lookup"><span data-stu-id="f70f2-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>

    |<span data-ttu-id="f70f2-112">Région de la variable</span><span class="sxs-lookup"><span data-stu-id="f70f2-112">Variable's region</span></span>|<span data-ttu-id="f70f2-113">Sous-région autorisée pour la redéfinition</span><span class="sxs-lookup"><span data-stu-id="f70f2-113">Allowable subregion for redefining it</span></span>|
    |-----------------------|-------------------------------------------|
    |<span data-ttu-id="f70f2-114">Module</span><span class="sxs-lookup"><span data-stu-id="f70f2-114">Module</span></span>|<span data-ttu-id="f70f2-115">Une classe dans le module</span><span class="sxs-lookup"><span data-stu-id="f70f2-115">A class within the module</span></span>|
    |<span data-ttu-id="f70f2-116">Class</span><span class="sxs-lookup"><span data-stu-id="f70f2-116">Class</span></span>|<span data-ttu-id="f70f2-117">Une sous-classe dans la classe</span><span class="sxs-lookup"><span data-stu-id="f70f2-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="f70f2-118">Une procédure dans la classe</span><span class="sxs-lookup"><span data-stu-id="f70f2-118">A procedure within the class</span></span>|

    <span data-ttu-id="f70f2-119">Vous ne pouvez pas redéfinir une variable de procédure dans un bloc au sein de cette procédure, par exemple dans une `If` construction... `End If` ou une `For` boucle.</span><span class="sxs-lookup"><span data-stu-id="f70f2-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>

2. <span data-ttu-id="f70f2-120">Créez la sous-région si elle n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="f70f2-120">Create the subregion if it does not already exist.</span></span>

3. <span data-ttu-id="f70f2-121">Dans la sous-région, écrivez une [instruction Dim](../../../language-reference/statements/dim-statement.md) qui déclare la variable d’occultation.</span><span class="sxs-lookup"><span data-stu-id="f70f2-121">Within the subregion, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>

    <span data-ttu-id="f70f2-122">Lorsque le code à l’intérieur de la sous-région fait référence au nom de la variable, le compilateur résout la référence à la variable d’occultation.</span><span class="sxs-lookup"><span data-stu-id="f70f2-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>

    <span data-ttu-id="f70f2-123">L’exemple suivant illustre l’occultation par le biais de l’étendue, ainsi qu’une référence qui contourne l’occultation.</span><span class="sxs-lookup"><span data-stu-id="f70f2-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>

    ```vb
    Module shadowByScope
        ' The following statement declares num as a module-level variable.
        Public num As Integer
        Sub show()
            ' The following statement declares num as a local variable.
            Dim num As Integer
            ' The following statement sets the value of the local variable.
            num = 2
            ' The following statement displays the module-level variable.
            MsgBox(CStr(shadowByScope.num))
        End Sub
        Sub useModuleLevelNum()
            ' The following statement sets the value of the module-level variable.
            num = 1
            show()
        End Sub
    End Module
    ```

    <span data-ttu-id="f70f2-124">L’exemple précédent déclare la variable `num` à la fois au niveau du module et au niveau de la procédure (dans la procédure `show` ).</span><span class="sxs-lookup"><span data-stu-id="f70f2-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="f70f2-125">La variable locale `num` occulte la variable au niveau du module `num` dans `show` , donc la variable locale a la valeur 2.</span><span class="sxs-lookup"><span data-stu-id="f70f2-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="f70f2-126">Toutefois, il n’y a aucune variable locale à occulter `num` dans la `useModuleLevelNum` procédure.</span><span class="sxs-lookup"><span data-stu-id="f70f2-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="f70f2-127">Par conséquent, `useModuleLevelNum` affecte la valeur 1 à la variable au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="f70f2-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>

    <span data-ttu-id="f70f2-128">L' `MsgBox` appel à l’intérieur `show` contourne le mécanisme d’occultation en qualifiant `num` le nom du module.</span><span class="sxs-lookup"><span data-stu-id="f70f2-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="f70f2-129">Par conséquent, elle affiche la variable au niveau du module au lieu de la variable locale.</span><span class="sxs-lookup"><span data-stu-id="f70f2-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="f70f2-130">Pour masquer une variable en l’occultant à l’aide de l’héritage</span><span class="sxs-lookup"><span data-stu-id="f70f2-130">To hide a variable by shadowing it through inheritance</span></span>

1. <span data-ttu-id="f70f2-131">Assurez-vous que la variable que vous souhaitez masquer est déclarée dans une classe et au niveau de la classe (en dehors de toute procédure).</span><span class="sxs-lookup"><span data-stu-id="f70f2-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="f70f2-132">Dans le cas contraire, vous ne pouvez pas l’occulter via l’héritage.</span><span class="sxs-lookup"><span data-stu-id="f70f2-132">Otherwise you cannot shadow it through inheritance.</span></span>

2. <span data-ttu-id="f70f2-133">Définissez une classe dérivée de la classe de la variable si celle-ci n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="f70f2-133">Define a class derived from the variable's class if one does not already exist.</span></span>

3. <span data-ttu-id="f70f2-134">À l’intérieur de la classe dérivée, écrivez une `Dim` instruction qui déclare votre variable.</span><span class="sxs-lookup"><span data-stu-id="f70f2-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="f70f2-135">Incluez le mot clé [Shadows](../../../language-reference/modifiers/shadows.md) dans la déclaration.</span><span class="sxs-lookup"><span data-stu-id="f70f2-135">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

    <span data-ttu-id="f70f2-136">Lorsque le code dans la classe dérivée fait référence au nom de la variable, le compilateur résout la référence à votre variable.</span><span class="sxs-lookup"><span data-stu-id="f70f2-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

    <span data-ttu-id="f70f2-137">L’exemple suivant illustre l’occultation par héritage.</span><span class="sxs-lookup"><span data-stu-id="f70f2-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="f70f2-138">Il crée deux références, une qui accède à la variable de masquage et une qui ignore l’occultation.</span><span class="sxs-lookup"><span data-stu-id="f70f2-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

    ```vb
    Public Class shadowBaseClass
        Public shadowString As String = "This is the base class string."
    End Class
    Public Class shadowDerivedClass
        Inherits shadowBaseClass
        Public Shadows shadowString As String = "This is the derived class string."
        Public Sub showStrings()
            Dim s As String = "Unqualified shadowString: " & shadowString &
                 vbCrLf & "MyBase.shadowString: " & MyBase.shadowString
            MsgBox(s)
        End Sub
    End Class
    ```

    <span data-ttu-id="f70f2-139">L’exemple précédent déclare la variable `shadowString` dans la classe de base et l’occulte dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="f70f2-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="f70f2-140">La procédure `showStrings` dans la classe dérivée affiche la version de l’occultation de la chaîne lorsque le nom `shadowString` n’est pas qualifié.</span><span class="sxs-lookup"><span data-stu-id="f70f2-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="f70f2-141">Il affiche ensuite la version occultée lorsque `shadowString` est qualifié avec le `MyBase` mot clé.</span><span class="sxs-lookup"><span data-stu-id="f70f2-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="f70f2-142">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="f70f2-142">Robust Programming</span></span>

<span data-ttu-id="f70f2-143">L’occultation introduit plusieurs versions d’une variable portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="f70f2-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="f70f2-144">Lorsqu’une instruction de code fait référence au nom de la variable, la version vers laquelle le compilateur résout la référence dépend de facteurs tels que l’emplacement de l’instruction de code et la présence d’une chaîne qualifiante.</span><span class="sxs-lookup"><span data-stu-id="f70f2-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="f70f2-145">Cela peut augmenter le risque de faire référence à une version inattendue d’une variable masquée.</span><span class="sxs-lookup"><span data-stu-id="f70f2-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="f70f2-146">Vous pouvez réduire ce risque en qualifiant entièrement toutes les références à une variable ombrée.</span><span class="sxs-lookup"><span data-stu-id="f70f2-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="f70f2-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f70f2-147">See also</span></span>

- [<span data-ttu-id="f70f2-148">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="f70f2-148">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="f70f2-149">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f70f2-149">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="f70f2-150">Différences entre l'occultation et la substitution</span><span class="sxs-lookup"><span data-stu-id="f70f2-150">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="f70f2-151">Comment : masquer une variable héritée</span><span class="sxs-lookup"><span data-stu-id="f70f2-151">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="f70f2-152">Comment : accéder à une variable masquée par une classe dérivée</span><span class="sxs-lookup"><span data-stu-id="f70f2-152">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="f70f2-153">Remplacements</span><span class="sxs-lookup"><span data-stu-id="f70f2-153">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="f70f2-154">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="f70f2-154">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="f70f2-155">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="f70f2-155">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
