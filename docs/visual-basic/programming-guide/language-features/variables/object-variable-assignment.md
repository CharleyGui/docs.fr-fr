---
title: Assignation des variables objets
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: 93de17490935d6d5cad01000e9ee3e2fe55bd16c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351831"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="a55cf-102">Assignation des variables objets (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a55cf-102">Object Variable Assignment (Visual Basic)</span></span>

<span data-ttu-id="a55cf-103">Vous utilisez une instruction d’assignation normale pour assigner un objet à une variable objet.</span><span class="sxs-lookup"><span data-stu-id="a55cf-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="a55cf-104">Vous pouvez assigner une expression d’objet ou le mot clé [Nothing](../../../../visual-basic/language-reference/nothing.md) , comme l’illustre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a55cf-104">You can assign an object expression or the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, as the following example illustrates.</span></span>

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

<span data-ttu-id="a55cf-105">`Nothing` signifie qu’aucun objet n’est actuellement assigné à la variable.</span><span class="sxs-lookup"><span data-stu-id="a55cf-105">`Nothing` means there is no object currently assigned to the variable.</span></span>

## <a name="initialization"></a><span data-ttu-id="a55cf-106">Initialisation</span><span class="sxs-lookup"><span data-stu-id="a55cf-106">Initialization</span></span>

<span data-ttu-id="a55cf-107">Lorsque votre code commence à s’exécuter, vos variables objet sont initialisées avec `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="a55cf-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="a55cf-108">Ceux dont les déclarations incluent l’initialisation sont réinitialisés aux valeurs que vous spécifiez lors de l’exécution des instructions de déclaration.</span><span class="sxs-lookup"><span data-stu-id="a55cf-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>

<span data-ttu-id="a55cf-109">Vous pouvez inclure l’initialisation dans votre déclaration à l’aide du mot clé [New](../../../../visual-basic/language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="a55cf-109">You can include initialization in your declaration by using the [New](../../../../visual-basic/language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="a55cf-110">Les instructions de déclaration suivantes déclarent des variables objet `testUri` et `ver` et leur assigner des objets spécifiques.</span><span class="sxs-lookup"><span data-stu-id="a55cf-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="a55cf-111">Chacun utilise l’un des constructeurs surchargés de la classe appropriée pour initialiser l’objet.</span><span class="sxs-lookup"><span data-stu-id="a55cf-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a><span data-ttu-id="a55cf-112">Dissociation</span><span class="sxs-lookup"><span data-stu-id="a55cf-112">Disassociation</span></span>

<span data-ttu-id="a55cf-113">La définition d’une variable objet sur `Nothing` interrompt l’Association de la variable avec un objet spécifique.</span><span class="sxs-lookup"><span data-stu-id="a55cf-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="a55cf-114">Cela vous empêche de modifier accidentellement l’objet en modifiant la variable.</span><span class="sxs-lookup"><span data-stu-id="a55cf-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="a55cf-115">Elle vous permet également de tester si la variable objet pointe vers un objet valide, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a55cf-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

<span data-ttu-id="a55cf-116">Si l’objet auquel votre variable fait référence se trouve dans une autre application, ce test ne peut pas déterminer si cette application s’est arrêtée ou si elle vient d’être invalidée par l’objet.</span><span class="sxs-lookup"><span data-stu-id="a55cf-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>

<span data-ttu-id="a55cf-117">Une variable objet avec une valeur de `Nothing` est également appelée *référence null*.</span><span class="sxs-lookup"><span data-stu-id="a55cf-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>

## <a name="current-instance"></a><span data-ttu-id="a55cf-118">Instance actuelle</span><span class="sxs-lookup"><span data-stu-id="a55cf-118">Current Instance</span></span>

<span data-ttu-id="a55cf-119">L' *instance actuelle* d’un objet est celle dans laquelle le code est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a55cf-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="a55cf-120">Étant donné que tout le code s’exécute à l’intérieur d’une procédure, l’instance actuelle est celle dans laquelle la procédure a été appelée.</span><span class="sxs-lookup"><span data-stu-id="a55cf-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>

<span data-ttu-id="a55cf-121">Le mot clé `Me` agit comme une variable objet qui fait référence à l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="a55cf-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="a55cf-122">Si une procédure n’est pas [partagée](../../../../visual-basic/language-reference/modifiers/shared.md), elle peut utiliser le mot clé `Me` pour obtenir un pointeur vers l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="a55cf-122">If a procedure is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="a55cf-123">Les procédures partagées ne peuvent pas être associées à une instance spécifique d’une classe.</span><span class="sxs-lookup"><span data-stu-id="a55cf-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>

<span data-ttu-id="a55cf-124">L’utilisation de `Me` est particulièrement utile pour passer l’instance actuelle à une procédure d’un autre module.</span><span class="sxs-lookup"><span data-stu-id="a55cf-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="a55cf-125">Supposons, par exemple, que vous ayez un certain nombre de documents XML et que vous souhaitiez ajouter du texte standard à tous.</span><span class="sxs-lookup"><span data-stu-id="a55cf-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="a55cf-126">L’exemple suivant définit une procédure pour effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="a55cf-126">The following example defines a procedure to do this.</span></span>

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

<span data-ttu-id="a55cf-127">Chaque objet de document XML peut ensuite appeler la procédure et passer son instance actuelle en tant qu’argument.</span><span class="sxs-lookup"><span data-stu-id="a55cf-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="a55cf-128">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a55cf-128">The following example demonstrates this.</span></span>

```vb
addStandardText(Me)
```

## <a name="see-also"></a><span data-ttu-id="a55cf-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a55cf-129">See also</span></span>

- [<span data-ttu-id="a55cf-130">Variables objets</span><span class="sxs-lookup"><span data-stu-id="a55cf-130">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="a55cf-131">Déclaration des variables objets</span><span class="sxs-lookup"><span data-stu-id="a55cf-131">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="a55cf-132">Valeurs des variables objets</span><span class="sxs-lookup"><span data-stu-id="a55cf-132">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="a55cf-133">Comment : déclarer une variable objet et lui assigner un objet dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a55cf-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="a55cf-134">Guide pratique : faire en sorte qu'une variable objet ne fasse pas référence à une instance</span><span class="sxs-lookup"><span data-stu-id="a55cf-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [<span data-ttu-id="a55cf-135">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="a55cf-135">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
