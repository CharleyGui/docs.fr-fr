---
title: Propriétés et méthodes surchargées
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: a5017d371f8a01436020443b2e3466c78fc35d21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346090"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="d3a9c-102">Propriétés et méthodes surchargées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3a9c-102">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="d3a9c-103">La surcharge est la création de plusieurs procédures, constructeur d’instance ou propriété dans une classe portant le même nom mais avec des types d’arguments différents.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>

## <a name="overloading-usage"></a><span data-ttu-id="d3a9c-104">Surcharge de l’utilisation</span><span class="sxs-lookup"><span data-stu-id="d3a9c-104">Overloading usage</span></span>

<span data-ttu-id="d3a9c-105">La surcharge est particulièrement utile lorsque votre modèle objet impose que vous utilisiez des noms identiques pour les procédures qui opèrent sur des types de données différents.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="d3a9c-106">Par exemple, une classe qui peut afficher plusieurs types de données différents peut avoir `Display` procédures qui ressemblent à ceci :</span><span class="sxs-lookup"><span data-stu-id="d3a9c-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

<span data-ttu-id="d3a9c-107">Sans surcharge, vous devez créer des noms distincts pour chaque procédure, même s’ils font la même chose, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="d3a9c-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

<span data-ttu-id="d3a9c-108">La surcharge facilite l’utilisation des propriétés ou des méthodes, car elle permet de choisir les types de données qui peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="d3a9c-109">Par exemple, la méthode surchargée `Display` présentée précédemment peut être appelée avec l’une des lignes de code suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3a9c-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

<span data-ttu-id="d3a9c-110">Au moment de l’exécution, Visual Basic appelle la procédure appropriée en fonction des types de données des paramètres que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-110">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="d3a9c-111">Surcharge des règles</span><span class="sxs-lookup"><span data-stu-id="d3a9c-111">Overloading rules</span></span>

 <span data-ttu-id="d3a9c-112">Pour créer un membre surchargé pour une classe, vous devez ajouter au moins deux propriétés ou méthodes portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="d3a9c-113">À l’exception des membres dérivés surchargés, chaque membre surchargé doit avoir des listes de paramètres différentes, et les éléments suivants ne peuvent pas être utilisés en tant que fonctionnalité de différenciation lors de la surcharge d’une propriété ou d’une procédure :</span><span class="sxs-lookup"><span data-stu-id="d3a9c-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>

- <span data-ttu-id="d3a9c-114">Les modificateurs, tels que `ByVal` ou `ByRef`, qui s’appliquent à un membre, ou à des paramètres du membre.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>

- <span data-ttu-id="d3a9c-115">Noms des paramètres</span><span class="sxs-lookup"><span data-stu-id="d3a9c-115">Names of parameters</span></span>

- <span data-ttu-id="d3a9c-116">Types de retour des procédures</span><span class="sxs-lookup"><span data-stu-id="d3a9c-116">Return types of procedures</span></span>

<span data-ttu-id="d3a9c-117">Le mot clé `Overloads` est facultatif lors de la surcharge, mais si un membre surchargé utilise le mot clé `Overloads`, tous les autres membres surchargés portant le même nom doivent également spécifier ce mot clé.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>

<span data-ttu-id="d3a9c-118">Les classes dérivées peuvent surcharger les membres hérités avec des membres qui ont des paramètres et des types de paramètres identiques, un processus appelé *occultation par nom et signature*.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="d3a9c-119">Si le mot clé `Overloads` est utilisé lors de l’occultation par nom et signature, l’implémentation du membre de la classe dérivée est utilisée à la place de l’implémentation dans la classe de base, et toutes les autres surcharges pour ce membre sont disponibles pour les instances de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>

<span data-ttu-id="d3a9c-120">Si le mot clé `Overloads` est omis lors de la surcharge d’un membre hérité avec un membre ayant des paramètres et des types de paramètres identiques, la surcharge est appelée *occultation par nom*.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="d3a9c-121">L’occultation par nom remplace l’implémentation héritée d’un membre, et rend toutes les autres surcharges indisponibles pour les instances de la classe dérivée et son decedents.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>

<span data-ttu-id="d3a9c-122">Les modificateurs `Overloads` et `Shadows` ne peuvent pas être utilisés à la fois avec la même propriété ou méthode.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>

### <a name="example"></a><span data-ttu-id="d3a9c-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3a9c-123">Example</span></span>

<span data-ttu-id="d3a9c-124">L’exemple suivant crée des méthodes surchargées qui acceptent une représentation `String` ou `Decimal` d’un montant en dollars et retournent une chaîne contenant les taxes de vente.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="d3a9c-125">Pour utiliser cet exemple afin de créer une méthode surchargée</span><span class="sxs-lookup"><span data-stu-id="d3a9c-125">To use this example to create an overloaded method</span></span>

1. <span data-ttu-id="d3a9c-126">Ouvrez un nouveau projet et ajoutez une classe nommée `TaxClass`.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-126">Open a new project and add a class named `TaxClass`.</span></span>

2. <span data-ttu-id="d3a9c-127">Ajoutez le code suivant à la classe `TaxClass` .</span><span class="sxs-lookup"><span data-stu-id="d3a9c-127">Add the following code to the `TaxClass` class.</span></span>

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. <span data-ttu-id="d3a9c-128">Ajoutez la procédure suivante à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-128">Add the following procedure to your form.</span></span>

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. <span data-ttu-id="d3a9c-129">Ajoutez un bouton à votre formulaire et appelez la procédure `ShowTax` à partir de l’événement `Button1_Click` du bouton.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>

5. <span data-ttu-id="d3a9c-130">Exécutez le projet et cliquez sur le bouton du formulaire pour tester la procédure de `ShowTax` surchargée.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>

<span data-ttu-id="d3a9c-131">Au moment de l’exécution, le compilateur choisit la fonction surchargée appropriée qui correspond aux paramètres utilisés.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="d3a9c-132">Lorsque vous cliquez sur le bouton, la méthode surchargée est appelée en premier avec un paramètre `Price` qui est une chaîne et le message «Price est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="d3a9c-133">La taxe est $5,12» s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="d3a9c-134">`TaxAmount` est appelé avec une valeur `Decimal` la deuxième fois et le message «Price est un nombre décimal.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="d3a9c-135">La taxe est $5,12» s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d3a9c-135">Tax is $5.12" is displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3a9c-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3a9c-136">See also</span></span>

- [<span data-ttu-id="d3a9c-137">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="d3a9c-137">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="d3a9c-138">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3a9c-138">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="d3a9c-139">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="d3a9c-139">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d3a9c-140">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="d3a9c-140">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="d3a9c-141">Shadows</span><span class="sxs-lookup"><span data-stu-id="d3a9c-141">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="d3a9c-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="d3a9c-142">ByVal</span></span>](../../../../visual-basic/language-reference/modifiers/byval.md)
- [<span data-ttu-id="d3a9c-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="d3a9c-143">ByRef</span></span>](../../../../visual-basic/language-reference/modifiers/byref.md)
- [<span data-ttu-id="d3a9c-144">Overloads</span><span class="sxs-lookup"><span data-stu-id="d3a9c-144">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="d3a9c-145">Shadows</span><span class="sxs-lookup"><span data-stu-id="d3a9c-145">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
