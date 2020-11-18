---
title: Surcharges d'opérateurs
ms.date: 10/22/2008
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 40e1c6a4a65bfc20c94223e4012e34928b25a2ab
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830036"
---
# <a name="operator-overloads"></a><span data-ttu-id="c8105-102">Surcharges d'opérateurs</span><span class="sxs-lookup"><span data-stu-id="c8105-102">Operator Overloads</span></span>
<span data-ttu-id="c8105-103">Les surcharges d’opérateur permettent d’afficher les types de Framework comme s’ils étaient des primitives de langage intégrées.</span><span class="sxs-lookup"><span data-stu-id="c8105-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="c8105-104">Bien qu’elles soient autorisées et utiles dans certains cas, les surcharges d’opérateur doivent être utilisées avec prudence.</span><span class="sxs-lookup"><span data-stu-id="c8105-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="c8105-105">Il existe de nombreux cas dans lesquels la surcharge d’opérateur a été abusée, par exemple quand les concepteurs de Framework ont commencé à utiliser des opérateurs pour les opérations qui doivent être des méthodes simples.</span><span class="sxs-lookup"><span data-stu-id="c8105-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="c8105-106">Les instructions suivantes doivent vous aider à déterminer quand et comment utiliser la surcharge d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="c8105-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="c8105-107">❌ Évitez de définir des surcharges d’opérateur, sauf dans les types qui doivent ressembler à des types primitifs (intégrés).</span><span class="sxs-lookup"><span data-stu-id="c8105-107">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="c8105-108">✔️ envisagez de définir des surcharges d’opérateur dans un type qui doit ressembler à un type primitif.</span><span class="sxs-lookup"><span data-stu-id="c8105-108">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="c8105-109">Par exemple, <xref:System.String?displayProperty=nameWithType> a `operator==` et `operator!=` défini.</span><span class="sxs-lookup"><span data-stu-id="c8105-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="c8105-110">✔️ définir des surcharges d’opérateur dans des structs qui représentent des nombres (tels que <xref:System.Decimal?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="c8105-110">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="c8105-111">❌ NE soyez pas au fait de définir des surcharges d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="c8105-111">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="c8105-112">La surcharge d’opérateur est utile dans les cas où il est immédiatement évident de savoir ce que sera le résultat de l’opération.</span><span class="sxs-lookup"><span data-stu-id="c8105-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="c8105-113">Par exemple, il est logique de pouvoir soustraire l’un <xref:System.DateTime> d’un autre `DateTime` et d’obtenir un <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="c8105-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="c8105-114">Toutefois, il n’est pas approprié d’utiliser l’opérateur d’Union logique pour unir deux requêtes de base de données, ou pour utiliser l’opérateur Shift pour écrire dans un flux.</span><span class="sxs-lookup"><span data-stu-id="c8105-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="c8105-115">❌ NE fournissez pas de surcharges d’opérateur sauf si au moins l’un des opérandes est du type définissant la surcharge.</span><span class="sxs-lookup"><span data-stu-id="c8105-115">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="c8105-116">✔️ surchargent les opérateurs de manière symétrique.</span><span class="sxs-lookup"><span data-stu-id="c8105-116">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="c8105-117">Par exemple, si vous surchargez le `operator==` , vous devez également surcharger `operator!=` .</span><span class="sxs-lookup"><span data-stu-id="c8105-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="c8105-118">De même, si vous surchargez le `operator<` , vous devez également surcharger `operator>` , et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="c8105-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="c8105-119">✔️ envisagez de fournir des méthodes avec des noms conviviaux qui correspondent à chaque opérateur surchargé.</span><span class="sxs-lookup"><span data-stu-id="c8105-119">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="c8105-120">De nombreux langages ne prennent pas en charge la surcharge d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="c8105-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="c8105-121">Pour cette raison, il est recommandé que les types qui surchargent les opérateurs incluent une méthode secondaire avec un nom spécifique au domaine approprié qui fournit des fonctionnalités équivalentes.</span><span class="sxs-lookup"><span data-stu-id="c8105-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="c8105-122">Le tableau suivant contient une liste d’opérateurs et les noms de méthode conviviaux correspondants.</span><span class="sxs-lookup"><span data-stu-id="c8105-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="c8105-123">Symbole d’opérateur C#</span><span class="sxs-lookup"><span data-stu-id="c8105-123">C# Operator Symbol</span></span>|<span data-ttu-id="c8105-124">Nom des métadonnées</span><span class="sxs-lookup"><span data-stu-id="c8105-124">Metadata Name</span></span>|<span data-ttu-id="c8105-125">Nom convivial</span><span class="sxs-lookup"><span data-stu-id="c8105-125">Friendly Name</span></span>|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a><span data-ttu-id="c8105-126">Surcharge de l’opérateur = =</span><span class="sxs-lookup"><span data-stu-id="c8105-126">Overloading Operator ==</span></span>
 <span data-ttu-id="c8105-127">La surcharge `operator ==` est assez complexe.</span><span class="sxs-lookup"><span data-stu-id="c8105-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="c8105-128">La sémantique de l’opérateur doit être compatible avec plusieurs autres membres, tels que <xref:System.Object.Equals%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c8105-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="c8105-129">Opérateurs de conversion</span><span class="sxs-lookup"><span data-stu-id="c8105-129">Conversion Operators</span></span>
 <span data-ttu-id="c8105-130">Les opérateurs de conversion sont des opérateurs unaires qui autorisent la conversion d’un type en un autre.</span><span class="sxs-lookup"><span data-stu-id="c8105-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="c8105-131">Les opérateurs doivent être définis en tant que membres statiques sur l’opérande ou le type de retour.</span><span class="sxs-lookup"><span data-stu-id="c8105-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="c8105-132">Il existe deux types d’opérateurs de conversion : implicites et explicites.</span><span class="sxs-lookup"><span data-stu-id="c8105-132">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="c8105-133">❌ NE fournissez pas d’opérateur de conversion si une telle conversion n’est pas clairement attendue par les utilisateurs finaux.</span><span class="sxs-lookup"><span data-stu-id="c8105-133">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="c8105-134">❌ NE définissez pas d’opérateurs de conversion en dehors du domaine d’un type.</span><span class="sxs-lookup"><span data-stu-id="c8105-134">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="c8105-135">Par exemple, <xref:System.Int32> , <xref:System.Double> et <xref:System.Decimal> sont tous des types numériques, alors que <xref:System.DateTime> n’est pas.</span><span class="sxs-lookup"><span data-stu-id="c8105-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="c8105-136">Par conséquent, il ne doit y avoir aucun opérateur de conversion pour convertir un `Double(long)` en `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="c8105-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="c8105-137">Un constructeur est préféré dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="c8105-137">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="c8105-138">❌ NE fournissez pas d’opérateur de conversion implicite si la conversion est potentiellement perdue.</span><span class="sxs-lookup"><span data-stu-id="c8105-138">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="c8105-139">Par exemple, il ne doit pas y avoir de conversion implicite de `Double` en `Int32` , car `Double` a une plage plus large que `Int32` .</span><span class="sxs-lookup"><span data-stu-id="c8105-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="c8105-140">Un opérateur de conversion explicite peut être fourni même si la conversion est potentiellement perdue.</span><span class="sxs-lookup"><span data-stu-id="c8105-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="c8105-141">❌ NE levez pas d’exceptions à partir de casts implicites.</span><span class="sxs-lookup"><span data-stu-id="c8105-141">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="c8105-142">Il est très difficile pour les utilisateurs finaux de comprendre ce qui se passe, car ils n’ont peut-être pas conscience qu’une conversion a lieu.</span><span class="sxs-lookup"><span data-stu-id="c8105-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="c8105-143">✔️ Levez une exception <xref:System.InvalidCastException?displayProperty=nameWithType> si un appel à un opérateur de cast entraîne une conversion avec perte et que le contrat de l’opérateur n’autorise pas les conversions avec perte de résultats.</span><span class="sxs-lookup"><span data-stu-id="c8105-143">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="c8105-144">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="c8105-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="c8105-145">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c8105-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c8105-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8105-146">See also</span></span>

- [<span data-ttu-id="c8105-147">Recommandations en matière de conception de membres</span><span class="sxs-lookup"><span data-stu-id="c8105-147">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="c8105-148">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="c8105-148">Framework Design Guidelines</span></span>](index.md)
