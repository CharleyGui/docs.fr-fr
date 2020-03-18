---
title: Surcharges d'opérateurs
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 0999e94c8d77396b237522e89c51206ce1226718
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400567"
---
# <a name="operator-overloads"></a><span data-ttu-id="21d2a-102">Surcharges d'opérateurs</span><span class="sxs-lookup"><span data-stu-id="21d2a-102">Operator Overloads</span></span>
<span data-ttu-id="21d2a-103">Les surcharges de l’opérateur permettent aux types de cadres d’apparaître comme s’ils étaient des primitifs en langue intégrée.</span><span class="sxs-lookup"><span data-stu-id="21d2a-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="21d2a-104">Bien qu’elles soient autorisées et utiles dans certaines situations, les surcharges de l’opérateur doivent être utilisées avec prudence.</span><span class="sxs-lookup"><span data-stu-id="21d2a-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="21d2a-105">Il y a beaucoup de cas dans lesquels la surcharge d’opérateur a été abusée, telle que quand les concepteurs de cadre ont commencé à employer des opérateurs pour des opérations qui devraient être des méthodes simples.</span><span class="sxs-lookup"><span data-stu-id="21d2a-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="21d2a-106">Les lignes directrices suivantes devraient vous aider à décider quand et comment utiliser la surcharge de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="21d2a-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="21d2a-107">❌AVOID définissant les surcharges de l’opérateur, sauf dans les types qui devraient se sentir comme des types primitifs (intégrés).</span><span class="sxs-lookup"><span data-stu-id="21d2a-107">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="21d2a-108">✔️ CONSIDER définissant les surcharges de l’opérateur dans un type qui devrait se sentir comme un type primitif.</span><span class="sxs-lookup"><span data-stu-id="21d2a-108">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="21d2a-109">Par <xref:System.String?displayProperty=nameWithType> exemple, `operator==` `operator!=` a et défini.</span><span class="sxs-lookup"><span data-stu-id="21d2a-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="21d2a-110">✔️ NE définissez les surcharges d’opérateur dans les <xref:System.Decimal?displayProperty=nameWithType>structs qui représentent des nombres (tels que ).</span><span class="sxs-lookup"><span data-stu-id="21d2a-110">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="21d2a-111">❌NE pas être mignon lors de la définition des surcharges de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="21d2a-111">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="21d2a-112">La surcharge de l’opérateur est utile dans les cas où il est immédiatement évident quel sera le résultat de l’opération.</span><span class="sxs-lookup"><span data-stu-id="21d2a-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="21d2a-113">Par exemple, il est logique d’être `DateTime` en mesure <xref:System.TimeSpan>de soustraire l’un de l’autre <xref:System.DateTime> et d’obtenir un .</span><span class="sxs-lookup"><span data-stu-id="21d2a-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="21d2a-114">Toutefois, il n’est pas approprié d’utiliser l’exploitant syndical logique pour syndiquer deux requêtes de base de données ou d’utiliser l’opérateur de quart pour écrire à un flux.</span><span class="sxs-lookup"><span data-stu-id="21d2a-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="21d2a-115">❌NE PAS fournir des surcharges d’opérateur à moins qu’au moins un des opérandes soit du type définissant la surcharge.</span><span class="sxs-lookup"><span data-stu-id="21d2a-115">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="21d2a-116">✔️ les opérateurs de surcharge DO d’une manière symétrique.</span><span class="sxs-lookup"><span data-stu-id="21d2a-116">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="21d2a-117">Par exemple, si vous `operator==`surchargez le , `operator!=`vous devriez également surcharger le .</span><span class="sxs-lookup"><span data-stu-id="21d2a-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="21d2a-118">De même, si `operator<`vous surchargez le `operator>`, vous devriez également surcharger le , et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="21d2a-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="21d2a-119">✔️ CONSIDER fournissant des méthodes avec des noms amicaux qui correspondent à chaque opérateur surchargé.</span><span class="sxs-lookup"><span data-stu-id="21d2a-119">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="21d2a-120">De nombreuses langues ne prennent pas en charge la surcharge des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="21d2a-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="21d2a-121">Pour cette raison, il est recommandé que les types qui surchargent les opérateurs comprennent une méthode secondaire avec un nom spécifique au domaine approprié qui fournit des fonctionnalités équivalentes.</span><span class="sxs-lookup"><span data-stu-id="21d2a-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="21d2a-122">Le tableau suivant contient une liste d’opérateurs et les noms de méthode amicale correspondants.</span><span class="sxs-lookup"><span data-stu-id="21d2a-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="21d2a-123">Symbole de l’opérateur CMD</span><span class="sxs-lookup"><span data-stu-id="21d2a-123">C# Operator Symbol</span></span>|<span data-ttu-id="21d2a-124">Nom des métadonnées</span><span class="sxs-lookup"><span data-stu-id="21d2a-124">Metadata Name</span></span>|<span data-ttu-id="21d2a-125">Nom convivial</span><span class="sxs-lookup"><span data-stu-id="21d2a-125">Friendly Name</span></span>|
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

### <a name="overloading-operator-"></a><span data-ttu-id="21d2a-126">Opérateur de surcharge</span><span class="sxs-lookup"><span data-stu-id="21d2a-126">Overloading Operator ==</span></span>
 <span data-ttu-id="21d2a-127">La surcharge `operator ==` est assez compliquée.</span><span class="sxs-lookup"><span data-stu-id="21d2a-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="21d2a-128">La sémantique de l’opérateur doit être compatible <xref:System.Object.Equals%2A?displayProperty=nameWithType>avec plusieurs autres membres, tels que .</span><span class="sxs-lookup"><span data-stu-id="21d2a-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="21d2a-129">Opérateurs de conversion</span><span class="sxs-lookup"><span data-stu-id="21d2a-129">Conversion Operators</span></span>
 <span data-ttu-id="21d2a-130">Les opérateurs de conversion sont des opérateurs non intentionnaires qui permettent la conversion d’un type à l’autre.</span><span class="sxs-lookup"><span data-stu-id="21d2a-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="21d2a-131">Les opérateurs doivent être définis comme des membres statiques sur l’opéra ou le type de retour.</span><span class="sxs-lookup"><span data-stu-id="21d2a-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="21d2a-132">Il existe deux types d’opérateurs de conversion : implicite et explicite.</span><span class="sxs-lookup"><span data-stu-id="21d2a-132">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="21d2a-133">❌NE PAS fournir un opérateur de conversion si cette conversion n’est pas clairement attendue par les utilisateurs finaux.</span><span class="sxs-lookup"><span data-stu-id="21d2a-133">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="21d2a-134">❌NE DÉFINIssez PAS les opérateurs de conversion en dehors du domaine d’un type.</span><span class="sxs-lookup"><span data-stu-id="21d2a-134">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="21d2a-135">Par <xref:System.Int32>exemple, <xref:System.Double>, <xref:System.Decimal> , et sont <xref:System.DateTime> tous les types numériques, alors que n’est pas.</span><span class="sxs-lookup"><span data-stu-id="21d2a-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="21d2a-136">Par conséquent, il ne devrait `Double(long)` pas `DateTime`y avoir d’opérateur de conversion pour convertir un .</span><span class="sxs-lookup"><span data-stu-id="21d2a-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="21d2a-137">Un constructeur est préféré dans un tel cas.</span><span class="sxs-lookup"><span data-stu-id="21d2a-137">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="21d2a-138">❌NE PAS fournir un opérateur de conversion implicite si la conversion est potentiellement déficiteuse.</span><span class="sxs-lookup"><span data-stu-id="21d2a-138">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="21d2a-139">Par exemple, il ne devrait `Double` pas `Int32` `Double` y avoir une `Int32`conversion implicite de parce que a une gamme plus large que .</span><span class="sxs-lookup"><span data-stu-id="21d2a-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="21d2a-140">Un opérateur de conversion explicite peut être fourni même si la conversion est potentiellement déficiteuse.</span><span class="sxs-lookup"><span data-stu-id="21d2a-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="21d2a-141">❌NE PAS jeter des exceptions des moulages implicites.</span><span class="sxs-lookup"><span data-stu-id="21d2a-141">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="21d2a-142">Il est très difficile pour les utilisateurs finaux de comprendre ce qui se passe, car ils pourraient ne pas être conscients qu’une conversion a lieu.</span><span class="sxs-lookup"><span data-stu-id="21d2a-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="21d2a-143">✔️ NE jeter <xref:System.InvalidCastException?displayProperty=nameWithType> si un appel à un opérateur de casting entraîne une conversion déficit et le contrat de l’opérateur ne permet pas des conversions déficitaires.</span><span class="sxs-lookup"><span data-stu-id="21d2a-143">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="21d2a-144">*Parts © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="21d2a-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="21d2a-145">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="21d2a-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="21d2a-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21d2a-146">See also</span></span>

- [<span data-ttu-id="21d2a-147">Instructions de conception des membres</span><span class="sxs-lookup"><span data-stu-id="21d2a-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="21d2a-148">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="21d2a-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
