---
title: Constantes et types de données littérales
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 03d693653cd166bbf1096031f1a864b492e2e896
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086294"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="efdd6-102">Constantes et types de données littérales (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efdd6-102">Constant and Literal Data Types (Visual Basic)</span></span>

<span data-ttu-id="efdd6-103">Un littéral est une valeur qui est exprimée comme étant elle-même plutôt que comme une valeur de variable ou le résultat d’une expression, tel que le numéro 3 ou la chaîne « Hello ».</span><span class="sxs-lookup"><span data-stu-id="efdd6-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="efdd6-104">Une constante est un nom explicite qui prend la place d’un littéral et conserve cette même valeur dans tout le programme, par opposition à une variable, dont la valeur peut changer.</span><span class="sxs-lookup"><span data-stu-id="efdd6-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="efdd6-105">Quand [Option Infer](../../../language-reference/statements/option-infer-statement.md) est `Off` et [option strict](../../../language-reference/statements/option-strict-statement.md) est `On` , vous devez déclarer toutes les constantes explicitement avec un type de données.</span><span class="sxs-lookup"><span data-stu-id="efdd6-105">When [Option Infer](../../../language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="efdd6-106">Dans l’exemple suivant, le type de données de `MyByte` est déclaré explicitement comme type de données `Byte` :</span><span class="sxs-lookup"><span data-stu-id="efdd6-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 <span data-ttu-id="efdd6-107">Lorsque `Option Infer` est `On` ou `Option Strict` a `Off` la clause, vous pouvez déclarer une constante sans spécifier de type de données avec une `As` clause.</span><span class="sxs-lookup"><span data-stu-id="efdd6-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="efdd6-108">Le compilateur détermine le type de la constante à partir du type de l’expression.</span><span class="sxs-lookup"><span data-stu-id="efdd6-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="efdd6-109">Un littéral d’entier numérique est converti par défaut en `Integer` type de données.</span><span class="sxs-lookup"><span data-stu-id="efdd6-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="efdd6-110">Le type de données par défaut pour les nombres à virgule flottante est `Double` , et les mots clés `True` et `False` spécifient une `Boolean` constante.</span><span class="sxs-lookup"><span data-stu-id="efdd6-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="efdd6-111">Littéraux et forçage de type</span><span class="sxs-lookup"><span data-stu-id="efdd6-111">Literals and Type Coercion</span></span>  

 <span data-ttu-id="efdd6-112">Dans certains cas, vous souhaiterez peut-être forcer un littéral à un type de données particulier ; par exemple, lors de l’assignation d’une valeur littérale intégrale particulièrement importante à une variable de type `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="efdd6-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="efdd6-113">L’exemple suivant génère une erreur :</span><span class="sxs-lookup"><span data-stu-id="efdd6-113">The following example produces an error:</span></span>  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="efdd6-114">L’erreur résulte de la représentation du littéral.</span><span class="sxs-lookup"><span data-stu-id="efdd6-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="efdd6-115">Le `Decimal` type de données peut contenir une valeur de cette taille, mais le littéral est implicitement représenté sous la forme d’un `Long` , ce qui ne peut pas.</span><span class="sxs-lookup"><span data-stu-id="efdd6-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="efdd6-116">Vous pouvez forcer un littéral à un type de données particulier de deux manières : en y ajoutant un caractère de type ou en le plaçant dans des caractères englobants.</span><span class="sxs-lookup"><span data-stu-id="efdd6-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="efdd6-117">Un caractère de type ou des caractères englobants doit immédiatement précéder et/ou suivre le littéral, sans aucun espace ou caractère intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="efdd6-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="efdd6-118">Pour que l’exemple précédent fonctionne, vous pouvez ajouter le `D` caractère de type au littéral, ce qui a pour effet de le représenter en tant que `Decimal` :</span><span class="sxs-lookup"><span data-stu-id="efdd6-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 <span data-ttu-id="efdd6-119">L’exemple suivant illustre l’utilisation correcte des caractères de type et des caractères englobants :</span><span class="sxs-lookup"><span data-stu-id="efdd6-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 <span data-ttu-id="efdd6-120">Le tableau suivant présente les caractères englobants et les caractères de type disponibles dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="efdd6-120">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="efdd6-121">Type de données</span><span class="sxs-lookup"><span data-stu-id="efdd6-121">Data type</span></span>|<span data-ttu-id="efdd6-122">Caractère englobant</span><span class="sxs-lookup"><span data-stu-id="efdd6-122">Enclosing character</span></span>|<span data-ttu-id="efdd6-123">Caractère de type ajouté</span><span class="sxs-lookup"><span data-stu-id="efdd6-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="efdd6-124">(aucun)</span><span class="sxs-lookup"><span data-stu-id="efdd6-124">(none)</span></span>|<span data-ttu-id="efdd6-125">(aucun)</span><span class="sxs-lookup"><span data-stu-id="efdd6-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="efdd6-126">(aucun)</span><span class="sxs-lookup"><span data-stu-id="efdd6-126">(none)</span></span>|<span data-ttu-id="efdd6-127">(aucun)</span><span class="sxs-lookup"><span data-stu-id="efdd6-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="efdd6-128">"</span><span class="sxs-lookup"><span data-stu-id="efdd6-128">"</span></span>|<span data-ttu-id="efdd6-129">C</span><span class="sxs-lookup"><span data-stu-id="efdd6-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="efdd6-130">(aucun)</span><span class="sxs-lookup"><span data-stu-id="efdd6-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="efdd6-131">(aucun)</span><span class="sxs-lookup"><span data-stu-id="efdd6-131">(none)</span></span>|<span data-ttu-id="efdd6-132">D ou @</span><span class="sxs-lookup"><span data-stu-id="efdd6-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="efdd6-133">(aucun)</span><span class="sxs-lookup"><span data-stu-id="efdd6-133">(none)</span></span>|<span data-ttu-id="efdd6-134">R ou #</span><span class="sxs-lookup"><span data-stu-id="efdd6-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="efdd6-135">(aucun)</span><span class="sxs-lookup"><span data-stu-id="efdd6-135">(none)</span></span>|<span data-ttu-id="efdd6-136">I ou%</span><span class="sxs-lookup"><span data-stu-id="efdd6-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="efdd6-137">(aucun)</span><span class="sxs-lookup"><span data-stu-id="efdd6-137">(none)</span></span>|<span data-ttu-id="efdd6-138">L ou &</span><span class="sxs-lookup"><span data-stu-id="efdd6-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="efdd6-139">(aucun)</span><span class="sxs-lookup"><span data-stu-id="efdd6-139">(none)</span></span>|<span data-ttu-id="efdd6-140">S</span><span class="sxs-lookup"><span data-stu-id="efdd6-140">S</span></span>|  
|`Single`|<span data-ttu-id="efdd6-141">(aucun)</span><span class="sxs-lookup"><span data-stu-id="efdd6-141">(none)</span></span>|<span data-ttu-id="efdd6-142">F ou !</span><span class="sxs-lookup"><span data-stu-id="efdd6-142">F or !</span></span>|  
|`String`|<span data-ttu-id="efdd6-143">"</span><span class="sxs-lookup"><span data-stu-id="efdd6-143">"</span></span>|<span data-ttu-id="efdd6-144">(aucun)</span><span class="sxs-lookup"><span data-stu-id="efdd6-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efdd6-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efdd6-145">See also</span></span>

- [<span data-ttu-id="efdd6-146">Constantes définies par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="efdd6-146">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="efdd6-147">Comment : déclarer une constante</span><span class="sxs-lookup"><span data-stu-id="efdd6-147">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="efdd6-148">Vue d'ensemble des constantes</span><span class="sxs-lookup"><span data-stu-id="efdd6-148">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="efdd6-149">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="efdd6-149">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="efdd6-150">Option Explicit (instruction)</span><span class="sxs-lookup"><span data-stu-id="efdd6-150">Option Explicit Statement</span></span>](../../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="efdd6-151">Vue d'ensemble des énumérations</span><span class="sxs-lookup"><span data-stu-id="efdd6-151">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="efdd6-152">How to: Declare an, énumération</span><span class="sxs-lookup"><span data-stu-id="efdd6-152">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="efdd6-153">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="efdd6-153">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="efdd6-154">Data types</span><span class="sxs-lookup"><span data-stu-id="efdd6-154">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="efdd6-155">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="efdd6-155">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
