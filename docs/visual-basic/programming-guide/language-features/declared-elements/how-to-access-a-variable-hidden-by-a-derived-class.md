---
title: 'Procédure : Accéder à une variable masquée par une classe dérivée (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 68f92142cdc435ebd82101eea83035e1d09dcf25
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630013"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="29f49-102">Procédure : Accéder à une variable masquée par une classe dérivée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29f49-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>

<span data-ttu-id="29f49-103">Lorsque le code d’une classe dérivée accède à une variable, le compilateur résout normalement la référence à la version accessible la plus proche, autrement dit, la version accessible, le plus petit des étapes de dérivation, en arrière de la classe d’accès.</span><span class="sxs-lookup"><span data-stu-id="29f49-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="29f49-104">Si la variable est définie dans la classe dérivée, le code accède normalement à cette définition.</span><span class="sxs-lookup"><span data-stu-id="29f49-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>

<span data-ttu-id="29f49-105">Si la variable de classe dérivée occulte une variable de la classe de base, elle masque la version de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="29f49-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="29f49-106">Toutefois, vous pouvez accéder à la variable de classe de base en la `MyBase` qualifiant avec le mot clé.</span><span class="sxs-lookup"><span data-stu-id="29f49-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="29f49-107">Pour accéder à une variable de classe de base masquée par une classe dérivée</span><span class="sxs-lookup"><span data-stu-id="29f49-107">To access a base class variable hidden by a derived class</span></span>

- <span data-ttu-id="29f49-108">Dans une expression ou une instruction d’assignation, faites précéder le `MyBase` nom de la variable du`.`mot clé et d’un point ().</span><span class="sxs-lookup"><span data-stu-id="29f49-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>

    <span data-ttu-id="29f49-109">Le compilateur résout la référence à la version de la classe de base de la variable.</span><span class="sxs-lookup"><span data-stu-id="29f49-109">The compiler resolves the reference to the base class version of the variable.</span></span>

    <span data-ttu-id="29f49-110">L’exemple suivant illustre l’occultation par héritage.</span><span class="sxs-lookup"><span data-stu-id="29f49-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="29f49-111">Il crée deux références, une qui accède à la variable de masquage et une qui ignore l’occultation.</span><span class="sxs-lookup"><span data-stu-id="29f49-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

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

    <span data-ttu-id="29f49-112">L’exemple précédent déclare la variable `shadowString` dans la classe de base et l’occulte dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="29f49-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="29f49-113">La procédure `showStrings` dans la classe dérivée affiche la version de l’occultation de la chaîne `shadowString` lorsque le nom n’est pas qualifié.</span><span class="sxs-lookup"><span data-stu-id="29f49-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="29f49-114">Il affiche ensuite la version occultée lorsque `shadowString` est qualifié avec le `MyBase` mot clé.</span><span class="sxs-lookup"><span data-stu-id="29f49-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="29f49-115">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="29f49-115">Robust Programming</span></span>

<span data-ttu-id="29f49-116">Pour réduire le risque de faire référence à une version inattendue d’une variable masquée, vous pouvez qualifier entièrement toutes les références à une variable ombrée.</span><span class="sxs-lookup"><span data-stu-id="29f49-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="29f49-117">L’occultation introduit plusieurs versions d’une variable portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="29f49-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="29f49-118">Lorsqu’une instruction de code fait référence au nom de la variable, la version vers laquelle le compilateur résout la référence dépend de facteurs tels que l’emplacement de l’instruction de code et la présence d’une chaîne qualifiante.</span><span class="sxs-lookup"><span data-stu-id="29f49-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="29f49-119">Cela peut augmenter le risque de faire référence à la mauvaise version de la variable.</span><span class="sxs-lookup"><span data-stu-id="29f49-119">This can increase the risk of referring to the wrong version of the variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="29f49-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29f49-120">See also</span></span>

- [<span data-ttu-id="29f49-121">Références aux éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="29f49-121">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="29f49-122">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29f49-122">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="29f49-123">Différences entre l'occultation et la substitution</span><span class="sxs-lookup"><span data-stu-id="29f49-123">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="29f49-124">Guide pratique : Masquer une variable portant le même nom que votre variable</span><span class="sxs-lookup"><span data-stu-id="29f49-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="29f49-125">Guide pratique pour Masquer une variable héritée</span><span class="sxs-lookup"><span data-stu-id="29f49-125">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="29f49-126">Shadows</span><span class="sxs-lookup"><span data-stu-id="29f49-126">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="29f49-127">Overrides</span><span class="sxs-lookup"><span data-stu-id="29f49-127">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="29f49-128">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="29f49-128">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="29f49-129">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="29f49-129">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
