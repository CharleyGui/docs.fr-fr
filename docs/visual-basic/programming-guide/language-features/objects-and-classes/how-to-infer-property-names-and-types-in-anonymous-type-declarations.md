---
title: 'Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 9ebbbe9d2e6d36f5ab2bc7f7c916d18c9240a06d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404886"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="5a3b7-102">Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a3b7-102">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>

<span data-ttu-id="5a3b7-103">Les types anonymes ne fournissent pas de mécanisme permettant de spécifier directement les types de données des propriétés.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-103">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="5a3b7-104">Les types de toutes les propriétés sont déduits.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-104">Types of all properties are inferred.</span></span> <span data-ttu-id="5a3b7-105">Dans l’exemple suivant, les types de `Name` et de `Price` sont déduits directement des valeurs utilisées pour les initialiser.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-105">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>

[!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]

<span data-ttu-id="5a3b7-106">Les types anonymes peuvent également déduire les types et les noms de propriété à partir d’autres sources.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-106">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="5a3b7-107">Les sections qui suivent décrivent les cas où l’inférence est possible et des cas où elle ne l’est pas.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-107">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>

## <a name="successful-inference"></a><span data-ttu-id="5a3b7-108">Inférence possible</span><span class="sxs-lookup"><span data-stu-id="5a3b7-108">Successful Inference</span></span>

#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="5a3b7-109">Les types anonymes peuvent déduire les types et les noms de propriété à partir des sources suivantes :</span><span class="sxs-lookup"><span data-stu-id="5a3b7-109">Anonymous types can infer property names and types from the following sources:</span></span>

- <span data-ttu-id="5a3b7-110">Noms de variable.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-110">From variable names.</span></span> <span data-ttu-id="5a3b7-111">Le type anonyme `anonProduct` a deux propriétés : `productName` et `productPrice`.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-111">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="5a3b7-112">Leurs types de données sont ceux des variables initiales, `String` et `Double`respectivement.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-112">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]

- <span data-ttu-id="5a3b7-113">Noms de propriété ou de champ d’autres objets.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-113">From property or field names of other objects.</span></span> <span data-ttu-id="5a3b7-114">Prenez l’exemple d’un objet `car` de type `CarClass` qui a les propriétés `Name` et `ID` .</span><span class="sxs-lookup"><span data-stu-id="5a3b7-114">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="5a3b7-115">Pour créer une instance de type anonyme `car1`avec les propriétés `Name` et `ID` initialisées avec les valeurs de l’objet `car` , vous pouvez écrire ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="5a3b7-115">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]

  <span data-ttu-id="5a3b7-116">La déclaration qui précède équivaut à la plus longue ligne de code qui définit le type anonyme `car2`.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-116">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]

- <span data-ttu-id="5a3b7-117">Noms de membre XML.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-117">From XML member names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]

  <span data-ttu-id="5a3b7-118">Le type résultant pour `anon` a alors une seule propriété, `Book`, de type <xref:System.Collections.IEnumerable>(Of XElement).</span><span class="sxs-lookup"><span data-stu-id="5a3b7-118">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>

- <span data-ttu-id="5a3b7-119">Fonction n’ayant aucun paramètre, telle que `SomeFunction` (voir l’exemple suivant).</span><span class="sxs-lookup"><span data-stu-id="5a3b7-119">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>

  ```vb
  Dim sc As New SomeClass
  Dim anon1 = New With {Key sc.SomeFunction()}
  ```

  <span data-ttu-id="5a3b7-120">La variable `anon2` présente dans le code suivant est un type anonyme qui a une seule propriété, un caractère nommé `First`.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-120">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="5a3b7-121">Ce code affiche la lettre « E », qui est la lettre retournée par la fonction <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-121">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]

## <a name="inference-failures"></a><span data-ttu-id="5a3b7-122">Inférence impossible</span><span class="sxs-lookup"><span data-stu-id="5a3b7-122">Inference Failures</span></span>

#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="5a3b7-123">L’inférence de nom échoue dans de nombreux cas, notamment les suivants :</span><span class="sxs-lookup"><span data-stu-id="5a3b7-123">Name inference will fail in many circumstances, including the following:</span></span>

- <span data-ttu-id="5a3b7-124">L’inférence dérive de l’appel d’une méthode, d’un constructeur ou d’une propriété paramétrable qui nécessite des arguments.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-124">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="5a3b7-125">La déclaration précédente de `anon1` échoue si `someFunction` a un ou plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-125">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon3 = New With {Key sc.someFunction(someArg)}
  ```

  <span data-ttu-id="5a3b7-126">L’assignation à un nouveau nom de propriété résout le problème.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-126">Assignment to a new property name solves the problem.</span></span>

  ```vb
  ' Valid.
  Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}
  ```

- <span data-ttu-id="5a3b7-127">L’inférence dérive d’une expression complexe.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-127">The inference derives from a complex expression.</span></span>

  ```vb
  Dim aString As String = "Act "
  ' Not valid.
  ' Dim label = New With {Key aString & "IV"}
  ```

  <span data-ttu-id="5a3b7-128">L’erreur peut être résolue en assignant le résultat de l’expression à un nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-128">The error can be resolved by assigning the result of the expression to a property name.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]

- <span data-ttu-id="5a3b7-129">L’inférence pour plusieurs propriétés produit deux propriétés ou plus, qui portent le même nom.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-129">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="5a3b7-130">Dans les déclarations des exemples précédents, vous ne pouvez pas spécifier `product.Name` et `car1.Name` en tant que propriétés du même type anonyme.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-130">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="5a3b7-131">Sinon, l’identificateur déduit pour chaque propriété serait `Name`.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-131">This is because the inferred identifier for each of these would be `Name`.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon5 = New With {Key product.Name, Key car1.Name}
  ```

  <span data-ttu-id="5a3b7-132">Le problème peut être résolu en assignant les valeurs à des noms de propriété distincts.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-132">The problem can be solved by assigning the values to distinct property names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]

  <span data-ttu-id="5a3b7-133">Notez que les changements de casse (majuscules et minuscules) ne produisent pas deux noms distincts.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-133">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>

  ```vb
  Dim price = 0
  ' Not valid, because Price and price are the same name.
  ' Dim anon7 = New With {Key product.Price, Key price}
  ```

- <span data-ttu-id="5a3b7-134">Le type et la valeur d’origine d’une propriété dépendent d’une autre propriété qui n’est pas encore établie.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-134">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="5a3b7-135">Par exemple, `.IDName = .LastName` n’est pas valide dans une déclaration de type anonyme, sauf si `.LastName` est déjà initialisé.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-135">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}
  ```

  <span data-ttu-id="5a3b7-136">Dans cet exemple, vous pouvez résoudre le problème en inversant l’ordre de déclaration des propriétés.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-136">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]

- <span data-ttu-id="5a3b7-137">Un nom de propriété de type anonyme est identique au nom d’un membre de la méthode <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-137">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="5a3b7-138">Par exemple, la déclaration suivante échoue, car `Equals` est une méthode <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="5a3b7-138">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>

  ```vb
  ' Not valid.
  ' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _
  '                       "greater than", Key .Less = "less than"}
  ```

  <span data-ttu-id="5a3b7-139">Vous pouvez résoudre le problème en modifiant le nom de la propriété :</span><span class="sxs-lookup"><span data-stu-id="5a3b7-139">You can fix the problem by changing the property name:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]

## <a name="see-also"></a><span data-ttu-id="5a3b7-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a3b7-140">See also</span></span>

- [<span data-ttu-id="5a3b7-141">Initialiseurs d'objets : types nommés et anonymes</span><span class="sxs-lookup"><span data-stu-id="5a3b7-141">Object Initializers: Named and Anonymous Types</span></span>](object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="5a3b7-142">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="5a3b7-142">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="5a3b7-143">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="5a3b7-143">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="5a3b7-144">Clé</span><span class="sxs-lookup"><span data-stu-id="5a3b7-144">Key</span></span>](../../../language-reference/modifiers/key.md)
