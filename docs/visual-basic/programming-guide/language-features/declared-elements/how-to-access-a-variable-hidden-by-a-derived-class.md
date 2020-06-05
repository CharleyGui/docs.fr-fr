---
title: 'Comment : accéder à une variable masquée par une classe dérivée'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: c5ff802a0f6e081acd00d7cdfab4a8296b4daad9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392855"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="6d45f-102">Comment : accéder à une variable masquée par une classe dérivée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d45f-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>

<span data-ttu-id="6d45f-103">Lorsque le code d’une classe dérivée accède à une variable, le compilateur résout normalement la référence à la version accessible la plus proche, autrement dit, la version accessible, le plus petit des étapes de dérivation, en arrière de la classe d’accès.</span><span class="sxs-lookup"><span data-stu-id="6d45f-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="6d45f-104">Si la variable est définie dans la classe dérivée, le code accède normalement à cette définition.</span><span class="sxs-lookup"><span data-stu-id="6d45f-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>

<span data-ttu-id="6d45f-105">Si la variable de classe dérivée occulte une variable de la classe de base, elle masque la version de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="6d45f-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="6d45f-106">Toutefois, vous pouvez accéder à la variable de classe de base en la qualifiant avec le `MyBase` mot clé.</span><span class="sxs-lookup"><span data-stu-id="6d45f-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="6d45f-107">Pour accéder à une variable de classe de base masquée par une classe dérivée</span><span class="sxs-lookup"><span data-stu-id="6d45f-107">To access a base class variable hidden by a derived class</span></span>

- <span data-ttu-id="6d45f-108">Dans une expression ou une instruction d’assignation, faites précéder le nom de la variable du `MyBase` mot clé et d’un point ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="6d45f-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>

    <span data-ttu-id="6d45f-109">Le compilateur résout la référence à la version de la classe de base de la variable.</span><span class="sxs-lookup"><span data-stu-id="6d45f-109">The compiler resolves the reference to the base class version of the variable.</span></span>

    <span data-ttu-id="6d45f-110">L’exemple suivant illustre l’occultation par héritage.</span><span class="sxs-lookup"><span data-stu-id="6d45f-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="6d45f-111">Il crée deux références, une qui accède à la variable de masquage et une qui ignore l’occultation.</span><span class="sxs-lookup"><span data-stu-id="6d45f-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

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

    <span data-ttu-id="6d45f-112">L’exemple précédent déclare la variable `shadowString` dans la classe de base et l’occulte dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="6d45f-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="6d45f-113">La procédure `showStrings` dans la classe dérivée affiche la version de l’occultation de la chaîne lorsque le nom `shadowString` n’est pas qualifié.</span><span class="sxs-lookup"><span data-stu-id="6d45f-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="6d45f-114">Il affiche ensuite la version occultée lorsque `shadowString` est qualifié avec le `MyBase` mot clé.</span><span class="sxs-lookup"><span data-stu-id="6d45f-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="6d45f-115">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="6d45f-115">Robust Programming</span></span>

<span data-ttu-id="6d45f-116">Pour réduire le risque de faire référence à une version inattendue d’une variable masquée, vous pouvez qualifier entièrement toutes les références à une variable ombrée.</span><span class="sxs-lookup"><span data-stu-id="6d45f-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="6d45f-117">L’occultation introduit plusieurs versions d’une variable portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="6d45f-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="6d45f-118">Lorsqu’une instruction de code fait référence au nom de la variable, la version vers laquelle le compilateur résout la référence dépend de facteurs tels que l’emplacement de l’instruction de code et la présence d’une chaîne qualifiante.</span><span class="sxs-lookup"><span data-stu-id="6d45f-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="6d45f-119">Cela peut augmenter le risque de faire référence à la mauvaise version de la variable.</span><span class="sxs-lookup"><span data-stu-id="6d45f-119">This can increase the risk of referring to the wrong version of the variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d45f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d45f-120">See also</span></span>

- [<span data-ttu-id="6d45f-121">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="6d45f-121">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="6d45f-122">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6d45f-122">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="6d45f-123">Différences entre l'occultation et la substitution</span><span class="sxs-lookup"><span data-stu-id="6d45f-123">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="6d45f-124">Comment : masquer une variable portant le même nom que votre variable</span><span class="sxs-lookup"><span data-stu-id="6d45f-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="6d45f-125">Comment : masquer une variable héritée</span><span class="sxs-lookup"><span data-stu-id="6d45f-125">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="6d45f-126">Shadows</span><span class="sxs-lookup"><span data-stu-id="6d45f-126">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="6d45f-127">Remplacements</span><span class="sxs-lookup"><span data-stu-id="6d45f-127">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="6d45f-128">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="6d45f-128">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="6d45f-129">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="6d45f-129">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
