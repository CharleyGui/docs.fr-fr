---
title: Concepts de base des chaînes
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 44736f4db9977d9f69a0571cc80fa327dcf96581
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072507"
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="d86a0-102">Concepts de base des chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d86a0-102">String Basics in Visual Basic</span></span>

<span data-ttu-id="d86a0-103">Le type de données `String` représente une série de caractères (chacun représentant à son tour une instance du type de données `Char`).</span><span class="sxs-lookup"><span data-stu-id="d86a0-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="d86a0-104">Cette rubrique présente les concepts de base des chaînes dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d86a0-104">This topic introduces the basic concepts of strings in Visual Basic.</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="d86a0-105">Variables de chaîne</span><span class="sxs-lookup"><span data-stu-id="d86a0-105">String Variables</span></span>  

 <span data-ttu-id="d86a0-106">Il est possible d'assigner à une instance de chaîne une valeur littérale représentant une série de caractères.</span><span class="sxs-lookup"><span data-stu-id="d86a0-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="d86a0-107">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d86a0-107">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 <span data-ttu-id="d86a0-108">Une variable `String` peut également accepter une expression quelconque qui prend la valeur d'une chaîne.</span><span class="sxs-lookup"><span data-stu-id="d86a0-108">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="d86a0-109">En voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="d86a0-109">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 <span data-ttu-id="d86a0-110">Tout littéral assigné à une variable `String` doit être placé entre guillemets ("").</span><span class="sxs-lookup"><span data-stu-id="d86a0-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="d86a0-111">Cela signifie que des guillemets dans une chaîne ne peuvent pas être représentés par des guillemets.</span><span class="sxs-lookup"><span data-stu-id="d86a0-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="d86a0-112">Par exemple, le code suivant génère une erreur du compilateur :</span><span class="sxs-lookup"><span data-stu-id="d86a0-112">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 <span data-ttu-id="d86a0-113">Ce code entraîne une erreur car le compilateur arrête la chaîne après les deuxièmes guillemets, et le reste de la chaîne est interprété comme du code.</span><span class="sxs-lookup"><span data-stu-id="d86a0-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="d86a0-114">Pour résoudre ce problème, Visual Basic interprète deux guillemets dans un littéral de chaîne comme un guillemet dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="d86a0-114">To solve this problem, Visual Basic interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="d86a0-115">L'exemple suivant illustre comment inclure correctement des guillemets dans une chaîne :</span><span class="sxs-lookup"><span data-stu-id="d86a0-115">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 <span data-ttu-id="d86a0-116">Dans l'exemple précédent, les deux guillemets qui précèdent le mot `Look` deviennent des guillemets simples dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="d86a0-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="d86a0-117">Les trois guillemets à la fin de la ligne correspondent aux guillemets simples dans la chaîne et au caractère de fin de chaîne.</span><span class="sxs-lookup"><span data-stu-id="d86a0-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="d86a0-118">Les littéraux de chaîne peuvent contenir plusieurs lignes :</span><span class="sxs-lookup"><span data-stu-id="d86a0-118">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="d86a0-119">La chaîne obtenue contient les séquences de saut de ligne que vous utilisiez dans votre littéral de chaîne (vbcr, vbcrlf, etc.).</span><span class="sxs-lookup"><span data-stu-id="d86a0-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="d86a0-120">Vous n'avez plus besoin d'utiliser l'ancienne solution de contournement :</span><span class="sxs-lookup"><span data-stu-id="d86a0-120">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="d86a0-121">Caractères dans des chaînes</span><span class="sxs-lookup"><span data-stu-id="d86a0-121">Characters in Strings</span></span>  

 <span data-ttu-id="d86a0-122">Une chaîne peut être considérée comme une série de valeurs `Char` et le type `String` possède des fonctions intégrées qui vous permettent d'exécuter de nombreuses manipulations sur une chaîne qui ressemblent aux manipulations autorisées par les tableaux.</span><span class="sxs-lookup"><span data-stu-id="d86a0-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="d86a0-123">Comme tous les tableaux dans .NET Framework, il s’agit de tableaux de base zéro.</span><span class="sxs-lookup"><span data-stu-id="d86a0-123">Like all array in .NET Framework, these are zero-based arrays.</span></span> <span data-ttu-id="d86a0-124">Vous pouvez vous référer à un caractère spécifique dans une chaîne via la propriété `Chars`, ce qui permet d'accéder à un caractère à la position où il apparaît dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="d86a0-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="d86a0-125">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d86a0-125">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 <span data-ttu-id="d86a0-126">Dans l'exemple ci-dessus, la propriété `Chars` de la chaîne retourne le quatrième caractère de la chaîne, qui est `D`, et l'assigne à `myChar`.</span><span class="sxs-lookup"><span data-stu-id="d86a0-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="d86a0-127">Vous pouvez également obtenir la longueur d'une chaîne particulière via la propriété `Length`.</span><span class="sxs-lookup"><span data-stu-id="d86a0-127">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="d86a0-128">Si vous devez exécuter plusieurs manipulations de type tableau sur une chaîne, vous pouvez la convertir en tableau d'instances `Char` à l'aide de la fonction `ToCharArray` de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="d86a0-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="d86a0-129">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d86a0-129">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 <span data-ttu-id="d86a0-130">La variable `myArray` contient à présent un tableau de valeurs `Char`, dont chacune représente un caractère issu de `myString`.</span><span class="sxs-lookup"><span data-stu-id="d86a0-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="d86a0-131">Immuabilité des chaînes</span><span class="sxs-lookup"><span data-stu-id="d86a0-131">The Immutability of Strings</span></span>  

 <span data-ttu-id="d86a0-132">Une chaîne est *immuable*, ce qui signifie que sa valeur ne peut pas être modifiée une fois qu’elle a été créée.</span><span class="sxs-lookup"><span data-stu-id="d86a0-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="d86a0-133">Toutefois, cela ne vous empêche pas d'assigner plusieurs valeurs à une variable de chaîne.</span><span class="sxs-lookup"><span data-stu-id="d86a0-133">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="d86a0-134">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d86a0-134">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 <span data-ttu-id="d86a0-135">Ici, une variable de chaîne est créée, une valeur lui est attribuée, puis sa valeur est modifiée.</span><span class="sxs-lookup"><span data-stu-id="d86a0-135">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="d86a0-136">Plus spécifiquement, dans la première ligne, une instance de type `String` est créée et la valeur `This string is immutable` lui est attribuée.</span><span class="sxs-lookup"><span data-stu-id="d86a0-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="d86a0-137">Dans la seconde ligne de l'exemple, une nouvelle instance est créée et la valeur `Or is it?` lui est attribuée. La variable de chaîne ignore sa référence à la première instance et stocke une référence à la nouvelle instance.</span><span class="sxs-lookup"><span data-stu-id="d86a0-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="d86a0-138">Contrairement à d'autres types de données intrinsèques, `String` est un type référence.</span><span class="sxs-lookup"><span data-stu-id="d86a0-138">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="d86a0-139">Quand une variable de type référence est passée en tant qu'argument à une fonction ou à une sous-routine, une référence à l'adresse mémoire où sont stockées les données est passée à la place de la valeur réelle de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="d86a0-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="d86a0-140">Ainsi, dans l'exemple précédent, le nom de la variable reste le même, mais il pointe vers une instance nouvelle et différente de la classe `String`, qui contient la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="d86a0-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d86a0-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d86a0-141">See also</span></span>

- [<span data-ttu-id="d86a0-142">Introduction aux chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d86a0-142">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="d86a0-143">String, type de données</span><span class="sxs-lookup"><span data-stu-id="d86a0-143">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="d86a0-144">Caractères (type de données)</span><span class="sxs-lookup"><span data-stu-id="d86a0-144">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="d86a0-145">Opérations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="d86a0-145">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
