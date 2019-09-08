---
title: Incompatibilité entre types SQL-CLR
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 27708f4bb8e191156f578132602570bc4a6337b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781202"
---
# <a name="sql-clr-type-mismatches"></a><span data-ttu-id="eb117-102">Incompatibilité entre types SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="eb117-102">SQL-CLR Type Mismatches</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="eb117-103">automatise en grande partie la traduction entre le modèle objet et SQL Server.</span><span class="sxs-lookup"><span data-stu-id="eb117-103">automates much of the translation between the object model and SQL Server.</span></span> <span data-ttu-id="eb117-104">Certaines situations ne permettent toutefois pas une traduction exacte.</span><span class="sxs-lookup"><span data-stu-id="eb117-104">Nevertheless, some situations prevent exact translation.</span></span> <span data-ttu-id="eb117-105">Cette incompatibilité majeure entre les types CLR (Common Language Runtime) et les types de base de données SQL Server est résumée dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="eb117-105">These key mismatches between the common language runtime (CLR) types and the SQL Server database types are summarized in the following sections.</span></span> <span data-ttu-id="eb117-106">Vous trouverez plus d’informations sur les mappages de types spécifiques et la traduction de fonction au niveau du [mappage de type CLR SQL](sql-clr-type-mapping.md) et des [types de données et des fonctions](data-types-and-functions.md).</span><span class="sxs-lookup"><span data-stu-id="eb117-106">You can find more details about specific type mappings and function translation at [SQL-CLR Type Mapping](sql-clr-type-mapping.md) and [Data Types and Functions](data-types-and-functions.md).</span></span>

## <a name="data-types"></a><span data-ttu-id="eb117-107">Types de données</span><span class="sxs-lookup"><span data-stu-id="eb117-107">Data Types</span></span>

<span data-ttu-id="eb117-108">La traduction entre CLR et SQL Server se produit lorsqu'une requête est envoyée à la base de données, et lorsque les résultats sont renvoyés au modèle objet.</span><span class="sxs-lookup"><span data-stu-id="eb117-108">Translation between the CLR and SQL Server occurs when a query is being sent to the database, and when the results are sent back to your object model.</span></span> <span data-ttu-id="eb117-109">Par exemple, la requête Transact-SQL suivante requiert deux conversions de valeurs :</span><span class="sxs-lookup"><span data-stu-id="eb117-109">For example, the following Transact-SQL query requires two value conversions:</span></span>

```sql
Select DateOfBirth From Customer Where CustomerId = @id
```

<span data-ttu-id="eb117-110">Pour que la requête soit exécutée sur SQL Server, vous devez spécifier la valeur du paramètre Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="eb117-110">Before the query can be executed on SQL Server, the value for the Transact-SQL parameter must be specified.</span></span> <span data-ttu-id="eb117-111">Dans cet exemple, la valeur du paramètre `id` doit d'abord être traduite d'un type <xref:System.Int32?displayProperty=nameWithType> CLR en un type `INT` SQL Server afin que la base de données puisse comprendre en quoi consiste cette valeur.</span><span class="sxs-lookup"><span data-stu-id="eb117-111">In this example, the `id` parameter value must first be translated from a CLR <xref:System.Int32?displayProperty=nameWithType> type to a SQL Server `INT` type so that the database can understand what the value is.</span></span> <span data-ttu-id="eb117-112">Puis pour récupérer les résultats, la colonne `DateOfBirth` SQL Server doit être traduite d'un type `DATETIME` SQL Server en un type <xref:System.DateTime?displayProperty=nameWithType> CLR à des fins d'utilisation dans le modèle objet.</span><span class="sxs-lookup"><span data-stu-id="eb117-112">Then to retrieve the results, the SQL Server `DateOfBirth` column must be translated from a SQL Server `DATETIME` type to a CLR <xref:System.DateTime?displayProperty=nameWithType> type for use in the object model.</span></span> <span data-ttu-id="eb117-113">Dans cet exemple, les types du modèle objet CLR et de la base de données SQL Server ont des mappages naturels.</span><span class="sxs-lookup"><span data-stu-id="eb117-113">In this example, the types in the CLR object model and SQL Server database have natural mappings.</span></span> <span data-ttu-id="eb117-114">Mais ce n'est pas toujours le cas.</span><span class="sxs-lookup"><span data-stu-id="eb117-114">But, this is not always the case.</span></span>

### <a name="missing-counterparts"></a><span data-ttu-id="eb117-115">Équivalents manquants</span><span class="sxs-lookup"><span data-stu-id="eb117-115">Missing Counterparts</span></span>

<span data-ttu-id="eb117-116">Les types suivants n'ont pas d'équivalents raisonnables.</span><span class="sxs-lookup"><span data-stu-id="eb117-116">The following types do not have reasonable counterparts.</span></span>

- <span data-ttu-id="eb117-117">Incompatibilités dans l'espace de noms <xref:System> CLR :</span><span class="sxs-lookup"><span data-stu-id="eb117-117">Mismatches in the CLR <xref:System> namespace:</span></span>

  - <span data-ttu-id="eb117-118">**Entiers non signés**.</span><span class="sxs-lookup"><span data-stu-id="eb117-118">**Unsigned integers**.</span></span> <span data-ttu-id="eb117-119">Ces types sont généralement mappés à leurs équivalents signés de plus grande taille pour éviter le dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="eb117-119">These types are typically mapped to their signed counterparts of larger size to avoid overflow.</span></span> <span data-ttu-id="eb117-120">Les littéraux peuvent être convertis en numérique signé de taille équivalente ou inférieure, selon la valeur.</span><span class="sxs-lookup"><span data-stu-id="eb117-120">Literals can be converted to a signed numeric of the same or smaller size, based on value.</span></span>

  - <span data-ttu-id="eb117-121">**Valeur booléenne**.</span><span class="sxs-lookup"><span data-stu-id="eb117-121">**Boolean**.</span></span> <span data-ttu-id="eb117-122">Ces types peuvent être mappés à un bit ou à un numérique ou une chaîne de taille supérieure.</span><span class="sxs-lookup"><span data-stu-id="eb117-122">These types can be mapped to a bit or larger numeric or string.</span></span> <span data-ttu-id="eb117-123">Un littéral peut être mappé à une expression qui correspond à la même valeur (par exemple, `1=1` dans SQL pour `True` dans CLS).</span><span class="sxs-lookup"><span data-stu-id="eb117-123">A literal can be mapped to an expression that evaluates to the same value (for example, `1=1` in SQL for `True` in CLS).</span></span>

  - <span data-ttu-id="eb117-124">**TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="eb117-124">**TimeSpan**.</span></span> <span data-ttu-id="eb117-125">Ce type représente la différence entre deux valeurs `DateTime` et ne correspond pas au `timestamp` de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="eb117-125">This type represents the difference between two `DateTime` values and does not correspond to the `timestamp` of SQL Server.</span></span> <span data-ttu-id="eb117-126">Dans certains cas, le <xref:System.TimeSpan?displayProperty=nameWithType> CLR peut également mapper au type `TIME` SQL Server.</span><span class="sxs-lookup"><span data-stu-id="eb117-126">The CLR <xref:System.TimeSpan?displayProperty=nameWithType> may also map to the SQL Server `TIME` type in some cases.</span></span> <span data-ttu-id="eb117-127">Le type `TIME` SQL Server a pour but de représenter les valeurs positives inférieures à 24 heures.</span><span class="sxs-lookup"><span data-stu-id="eb117-127">The SQL Server `TIME` type was only intended to represent positive values less than 24 hours.</span></span> <span data-ttu-id="eb117-128">Le <xref:System.TimeSpan> CLR offre une plage beaucoup plus étendue.</span><span class="sxs-lookup"><span data-stu-id="eb117-128">The CLR <xref:System.TimeSpan> has a much larger range.</span></span>

  > [!NOTE]
  > <span data-ttu-id="eb117-129">Les types de .NET Framework spécifiques à <xref:System.Data.SqlTypes> SQL Server dans ne sont pas inclus dans cette comparaison.</span><span class="sxs-lookup"><span data-stu-id="eb117-129">SQL Server-specific .NET Framework types in <xref:System.Data.SqlTypes> are not included in this comparison.</span></span>

- <span data-ttu-id="eb117-130">Incompatibilités dans SQL Server :</span><span class="sxs-lookup"><span data-stu-id="eb117-130">Mismatches in SQL Server:</span></span>

  - <span data-ttu-id="eb117-131">**Types de caractères de longueur fixe**.</span><span class="sxs-lookup"><span data-stu-id="eb117-131">**Fixed length character types**.</span></span> <span data-ttu-id="eb117-132">Transact-SQL fait la distinction entre les catégories Unicode et non-Unicode et possède trois types distincts dans chaque catégorie : `nchar`longueur `varchar` / `char`fixe, `nvarchar`longueur /variable et plus grande taille `ntext`. / `text`</span><span class="sxs-lookup"><span data-stu-id="eb117-132">Transact-SQL distinguishes between Unicode and non-Unicode categories and has three distinct types in each category: fixed length `nchar`/`char`, variable length `nvarchar`/`varchar`, and larger-sized `ntext`/`text`.</span></span> <span data-ttu-id="eb117-133">Les types de caractères de longueur fixe peuvent être mappés au type <xref:System.Char?displayProperty=nameWithType> CLR pour récupérer des caractères, mais ils ne correspondent pas vraiment au même type dans les conversions et le comportement.</span><span class="sxs-lookup"><span data-stu-id="eb117-133">The fixed length character types could be mapped to the CLR <xref:System.Char?displayProperty=nameWithType> type for retrieving characters, but they do not really correspond to the same type in conversions and behavior.</span></span>

  - <span data-ttu-id="eb117-134">**Bit**.</span><span class="sxs-lookup"><span data-stu-id="eb117-134">**Bit**.</span></span> <span data-ttu-id="eb117-135">Bien que le domaine `bit` présente le même nombre de valeurs que `Nullable<Boolean>`, il s'agit de deux types différents.</span><span class="sxs-lookup"><span data-stu-id="eb117-135">Although the `bit` domain has the same number of values as `Nullable<Boolean>`, the two are different types.</span></span> <span data-ttu-id="eb117-136">`Bit`prend les `1` valeurs `0` et au `true`lieu de /,etne peutpasêtreutilisécommeéquivalentauxexpressionsbooléennes.`false`</span><span class="sxs-lookup"><span data-stu-id="eb117-136">`Bit` takes values `1` and `0` instead of `true`/`false`, and cannot be used as an equivalent to Boolean expressions.</span></span>

  - <span data-ttu-id="eb117-137">**Horodateur**.</span><span class="sxs-lookup"><span data-stu-id="eb117-137">**Timestamp**.</span></span> <span data-ttu-id="eb117-138">Contrairement au type <xref:System.TimeSpan?displayProperty=nameWithType> CLR, le type `TIMESTAMP` SQL Server représente un nombre de 8 octets généré par la base de données qui est unique pour chaque mise à jour et n'est pas basé sur la différence entre des valeurs <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="eb117-138">Unlike the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type, the SQL Server `TIMESTAMP` type represents an 8-byte number generated by the database that is unique for each update and is not based on the difference between <xref:System.DateTime> values.</span></span>

  - <span data-ttu-id="eb117-139">**Money** et **smallmoney**.</span><span class="sxs-lookup"><span data-stu-id="eb117-139">**Money** and **SmallMoney**.</span></span> <span data-ttu-id="eb117-140">Ces types peuvent être mappés à <xref:System.Decimal> mais ils sont fondamentalement différents et sont traités comme tels par les fonctions et les conversions serveur.</span><span class="sxs-lookup"><span data-stu-id="eb117-140">These types can be mapped to <xref:System.Decimal> but are basically different types and are treated as such by server-based functions and conversions.</span></span>

### <a name="multiple-mappings"></a><span data-ttu-id="eb117-141">Mappages multiples</span><span class="sxs-lookup"><span data-stu-id="eb117-141">Multiple Mappings</span></span>

<span data-ttu-id="eb117-142">Il existe également de nombreux types de données SQL Server que vous pouvez mapper à un ou plusieurs types de données CLR.</span><span class="sxs-lookup"><span data-stu-id="eb117-142">There are many SQL Server data types that you can map to one or more CLR data types.</span></span> <span data-ttu-id="eb117-143">Il existe également de nombreux types CLR que vous pouvez mapper à un ou plusieurs types SQL Server.</span><span class="sxs-lookup"><span data-stu-id="eb117-143">There are also many CLR types that you can map to one or more SQL Server types.</span></span> <span data-ttu-id="eb117-144">Même si un mappage est pris en charge par LINQ to SQL, cela n'implique pas nécessairement que deux types mappés entre CLR et SQL Server présenteront une précision, une plage et une sémantique identiques.</span><span class="sxs-lookup"><span data-stu-id="eb117-144">Although a mapping may be supported by LINQ to SQL, it does not mean that the two types mapped between the CLR and SQL Server are a perfect match in precision, range, and semantics.</span></span> <span data-ttu-id="eb117-145">Certains mappages peuvent inclure des différences au niveau de tout ou partie de ces trois aspects.</span><span class="sxs-lookup"><span data-stu-id="eb117-145">Some mappings may include differences in any or all of these dimensions.</span></span> <span data-ttu-id="eb117-146">Vous trouverez plus d’informations sur ces différences potentielles pour les différentes possibilités de mappage au niveau du [mappage de type SQL-CLR](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="eb117-146">You can find details about these potential differences for the various mapping possibilities at [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>

### <a name="user-defined-types"></a><span data-ttu-id="eb117-147">Types définis par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="eb117-147">User-defined Types</span></span>

<span data-ttu-id="eb117-148">Les types CLR définis par l'utilisateur sont conçus pour aider à combler le fossé entre les systèmes de types.</span><span class="sxs-lookup"><span data-stu-id="eb117-148">User-defined CLR types are designed to help bridge the type system gap.</span></span> <span data-ttu-id="eb117-149">Ils présentent néanmoins des problèmes intéressants concernant le versioning de type.</span><span class="sxs-lookup"><span data-stu-id="eb117-149">Nevertheless they surface interesting issues about type versioning.</span></span> <span data-ttu-id="eb117-150">Une modification de la version du client peut ne pas avoir de modification correspondante dans le type stocké sur le serveur de base de données.</span><span class="sxs-lookup"><span data-stu-id="eb117-150">A change in the version on the client might not be matched by a change in the type stored on the database server.</span></span> <span data-ttu-id="eb117-151">Toute modification de ce type entraîne une autre incompatibilité de type où la sémantique de type risque de ne pas correspondre et la différence de version peut devenir visible.</span><span class="sxs-lookup"><span data-stu-id="eb117-151">Any such change causes another type mismatch where the type semantics might not match and the version gap is likely to become visible.</span></span> <span data-ttu-id="eb117-152">D'autres complications interviennent puisque les hiérarchies d'héritage sont refactorisées dans les versions successives.</span><span class="sxs-lookup"><span data-stu-id="eb117-152">Further complications occur as inheritance hierarchies are refactored in successive versions.</span></span>

## <a name="expression-semantics"></a><span data-ttu-id="eb117-153">Sémantique d'expression</span><span class="sxs-lookup"><span data-stu-id="eb117-153">Expression Semantics</span></span>

<span data-ttu-id="eb117-154">Outre l'incompatibilité par paire entre les types CLR et de base de données, les expressions compliquent l'incompatibilité.</span><span class="sxs-lookup"><span data-stu-id="eb117-154">In addition to the pairwise mismatch between CLR and database types, expressions add complexity to the mismatch.</span></span> <span data-ttu-id="eb117-155">Les incompatibilités dans la sémantique d'opérateur, la sémantique de fonction, la conversion de type implicite et les règles de priorité doivent être prises en compte.</span><span class="sxs-lookup"><span data-stu-id="eb117-155">Mismatches in operator semantics, function semantics, implicit type conversion, and precedence rules must be considered.</span></span>

<span data-ttu-id="eb117-156">Les sous-sections suivantes illustrent l'incompatibilité entre des expressions apparemment similaires.</span><span class="sxs-lookup"><span data-stu-id="eb117-156">The following subsections illustrate the mismatch between apparently similar expressions.</span></span> <span data-ttu-id="eb117-157">Il est possible de générer des expressions SQL qui sont sémantiquement équivalentes à une expression CLR donnée.</span><span class="sxs-lookup"><span data-stu-id="eb117-157">It might be possible to generate SQL expressions that are semantically equivalent to a given CLR expression.</span></span> <span data-ttu-id="eb117-158">Toutefois, on ne peut pas déterminer avec précision si les différences sémantiques entre des expressions apparemment similaires sont évidentes pour un utilisateur CLR, et par conséquent si les modifications requises pour l'équivalence sémantique sont prévues ou non.</span><span class="sxs-lookup"><span data-stu-id="eb117-158">However, it is not clear whether the semantic differences between apparently similar expressions are evident to a CLR user, and therefore whether the changes that are required for semantic equivalence are intended or not.</span></span> <span data-ttu-id="eb117-159">Un problème particulièrement critique se pose lors de l'évaluation d'une expression pour un ensemble de valeurs.</span><span class="sxs-lookup"><span data-stu-id="eb117-159">This is an especially critical issue when an expression is evaluated for a set of values.</span></span> <span data-ttu-id="eb117-160">La visibilité de la différence peut dépendre des données et être difficile à identifier pendant le codage et le débogage.</span><span class="sxs-lookup"><span data-stu-id="eb117-160">The visibility of the difference might depend on data- and be hard to identify during coding and debugging.</span></span>

### <a name="null-semantics"></a><span data-ttu-id="eb117-161">Sémantique Null</span><span class="sxs-lookup"><span data-stu-id="eb117-161">Null Semantics</span></span>

<span data-ttu-id="eb117-162">Les expressions SQL fournissent la logique à trois valeurs pour les expressions booléennes.</span><span class="sxs-lookup"><span data-stu-id="eb117-162">SQL expressions provide three-valued logic for Boolean expressions.</span></span> <span data-ttu-id="eb117-163">Le résultat peut être true, false ou null.</span><span class="sxs-lookup"><span data-stu-id="eb117-163">The result can be true, false, or null.</span></span> <span data-ttu-id="eb117-164">CLR spécifie un résultat booléen à deux valeurs pour les comparaisons impliquant des valeurs null.</span><span class="sxs-lookup"><span data-stu-id="eb117-164">By contrast, CLR specifies two-valued Boolean result for comparisons involving null values.</span></span> <span data-ttu-id="eb117-165">Examinons le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="eb117-165">Consider the following code:</span></span>

[!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
[!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]

```sql
-- Assume col1 and col2 are integer columns with null values.
-- Assume that ANSI null behavior has not been explicitly
--  turned off.
Select …
From …
Where col1 = col2
-- Evaluates to null, not true and the corresponding row is not
--   selected.
-- To obtain matching behavior (i -> col1, j -> col2) change
--   the query to the following:
Select …
From …
Where
    col1 = col2
or (col1 is null and col2 is null)
-- (Visual Basic 'Nothing'.)
```

<span data-ttu-id="eb117-166">Un problème similaire se produit avec l'hypothèse concernant les résultats à deux valeurs.</span><span class="sxs-lookup"><span data-stu-id="eb117-166">A similar problem occurs with the assumption about two-valued results.</span></span>

[!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
[!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]

```sql
-- Assume col1 and col2 are nullable columns.
-- Assume that ANSI null behavior has not been explicitly
--   turned off.
Select …
From …
Where
    col1 = col2
or col1 != col2
-- Visual Basic: col1 <> col2.

-- Excludes the case where the boolean expression evaluates
--   to null. Therefore the where clause does not always
--   evaluate to true.
```

<span data-ttu-id="eb117-167">Dans le cas précédent, vous pouvez obtenir un comportement équivalent en générant du SQL, mais la traduction risque de ne pas refléter correctement votre intention.</span><span class="sxs-lookup"><span data-stu-id="eb117-167">In the previous case, you can get equivalent behavior in generating SQL, but the translation might not accurately reflect your intention.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="eb117-168">n’impose C# `null` pas de sémantique `nothing` de comparaison ou Visual Basic sur SQL.</span><span class="sxs-lookup"><span data-stu-id="eb117-168">does not impose C# `null` or Visual Basic `nothing` comparison semantics on SQL.</span></span> <span data-ttu-id="eb117-169">Les opérateurs de comparaison sont traduits syntaxiquement dans leurs équivalents SQL.</span><span class="sxs-lookup"><span data-stu-id="eb117-169">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="eb117-170">La sémantique reflète la sémantique SQL définie par les paramètres du serveur ou de la connexion.</span><span class="sxs-lookup"><span data-stu-id="eb117-170">The semantics reflect SQL semantics as defined by server or connection settings.</span></span> <span data-ttu-id="eb117-171">Deux valeurs null sont considérées comme différentes selon les paramètres SQL Server (bien que vous puissiez modifier les paramètres pour changer la sémantique).</span><span class="sxs-lookup"><span data-stu-id="eb117-171">Two null values are considered unequal under default SQL Server settings (although you can change the settings to change the semantics).</span></span> <span data-ttu-id="eb117-172">Quoi qu'il en soit, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne tient pas compte des paramètres du serveur lors de la traduction de requête.</span><span class="sxs-lookup"><span data-stu-id="eb117-172">Regardless, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not consider server settings in query translation.</span></span>

<span data-ttu-id="eb117-173">Une comparaison avec le littéral `null` (`nothing`) est traduite dans la version SQL appropriée (`is null` ou `is not null`).</span><span class="sxs-lookup"><span data-stu-id="eb117-173">A comparison with the literal `null` (`nothing`) is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="eb117-174">La valeur `null` (`nothing`) dans le classement est définie par SQL Server et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne change pas le classement.</span><span class="sxs-lookup"><span data-stu-id="eb117-174">The value of `null` (`nothing`) in collation is defined by SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not change the collation.</span></span>

### <a name="type-conversion-and-promotion"></a><span data-ttu-id="eb117-175">Conversion et promotion de type</span><span class="sxs-lookup"><span data-stu-id="eb117-175">Type Conversion and Promotion</span></span>

<span data-ttu-id="eb117-176">SQL prend en charge un ensemble complet de conversions implicites d'expressions.</span><span class="sxs-lookup"><span data-stu-id="eb117-176">SQL supports a rich set of implicit conversions in expressions.</span></span> <span data-ttu-id="eb117-177">Des expressions similaires en C# nécessiteraient un cast explicite.</span><span class="sxs-lookup"><span data-stu-id="eb117-177">Similar expressions in C# would require an explicit cast.</span></span> <span data-ttu-id="eb117-178">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="eb117-178">For example:</span></span>

- <span data-ttu-id="eb117-179">Les types `Nvarchar` et `DateTime` peuvent être comparés dans SQL sans cast explicite mais C# nécessite une conversion explicite.</span><span class="sxs-lookup"><span data-stu-id="eb117-179">`Nvarchar` and `DateTime` types can be compared in SQL without any explicit casts; C# requires explicit conversion.</span></span>

- <span data-ttu-id="eb117-180">`Decimal` est converti implicitement en `DateTime` dans SQL.</span><span class="sxs-lookup"><span data-stu-id="eb117-180">`Decimal` is implicitly converted to `DateTime` in SQL.</span></span> <span data-ttu-id="eb117-181">C# n'autorise pas de conversion implicite.</span><span class="sxs-lookup"><span data-stu-id="eb117-181">C# does not allow for an implicit conversion.</span></span>

<span data-ttu-id="eb117-182">De même, la priorité des types de Transact-SQL diffère de celle de C# car l'ensemble de types sous-jacent est différent.</span><span class="sxs-lookup"><span data-stu-id="eb117-182">Likewise, type precedence in Transact-SQL differs from type precedence in C# because the underlying set of types is different.</span></span> <span data-ttu-id="eb117-183">En fait, il n'existe pas de relation sous-ensemble/sur-ensemble claire entre les listes de priorités.</span><span class="sxs-lookup"><span data-stu-id="eb117-183">In fact, there is no clear subset/superset relationship between the precedence lists.</span></span> <span data-ttu-id="eb117-184">Par exemple, la comparaison d'un `nvarchar` avec un `varchar` entraîne la conversion implicite de l'expression `varchar` en `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="eb117-184">For example, comparing an `nvarchar` with a `varchar` causes the implicit conversion of the `varchar` expression to `nvarchar`.</span></span> <span data-ttu-id="eb117-185">CLR ne fournit aucune promotion équivalente.</span><span class="sxs-lookup"><span data-stu-id="eb117-185">The CLR provides no equivalent promotion.</span></span>

<span data-ttu-id="eb117-186">Dans les cas simples, ces différences soumettent les expressions CLR à des casts redondants pour une expression SQL correspondante.</span><span class="sxs-lookup"><span data-stu-id="eb117-186">In simple cases, these differences cause CLR expressions with casts to be redundant for a corresponding SQL expression.</span></span> <span data-ttu-id="eb117-187">Plus important, les résultats intermédiaires d'une expression SQL risquent de faire l'objet d'une promotion implicite en un type qui ne présente aucun équivalent exact en C# et inversement.</span><span class="sxs-lookup"><span data-stu-id="eb117-187">More importantly, the intermediate results of a SQL expression might be implicitly promoted to a type that has no accurate counterpart in C#, and vice versa.</span></span> <span data-ttu-id="eb117-188">De manière générale, le test, le débogage et la validation de ce type d'expressions représentent une charge de travail supplémentaire pour l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="eb117-188">Overall, the testing, debugging, and validation of such expressions adds significant burden on the user.</span></span>

### <a name="collation"></a><span data-ttu-id="eb117-189">Collation</span><span class="sxs-lookup"><span data-stu-id="eb117-189">Collation</span></span>

<span data-ttu-id="eb117-190">Transact-SQL prend en charge des classements explicites tels que les annotations des types de chaînes de caractères.</span><span class="sxs-lookup"><span data-stu-id="eb117-190">Transact-SQL supports explicit collations as annotations to character string types.</span></span> <span data-ttu-id="eb117-191">Ces classements déterminent la validité de certaines comparaisons.</span><span class="sxs-lookup"><span data-stu-id="eb117-191">These collations determine the validity of certain comparisons.</span></span> <span data-ttu-id="eb117-192">Par exemple, la comparaison de deux colonnes avec des classements explicites différents est une erreur.</span><span class="sxs-lookup"><span data-stu-id="eb117-192">For example, comparing two columns with different explicit collations is an error.</span></span> <span data-ttu-id="eb117-193">L'utilisation d'un type de chaîne CTS très simplifié ne provoque pas de telles erreurs.</span><span class="sxs-lookup"><span data-stu-id="eb117-193">The use of much simplified CTS string type does not cause such errors.</span></span> <span data-ttu-id="eb117-194">Prenons l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eb117-194">Consider the following example:</span></span>

```sql
create table T2 (
    Col1 nvarchar(10),
    Col2      nvarchar(10) collate Latin_general_ci_as
)
```

[!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
[!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]

```sql
Select …
From …
Where Col1 = Col2
-- Error, collation conflict.
```

<span data-ttu-id="eb117-195">En effet, la sous-clause collation crée un *type restreint* qui ne peut pas être substitué.</span><span class="sxs-lookup"><span data-stu-id="eb117-195">In effect, the collation subclause creates a *restricted type* that is not substitutable.</span></span>

<span data-ttu-id="eb117-196">De même, l'ordre de tri peut être considérablement différent selon les systèmes de type.</span><span class="sxs-lookup"><span data-stu-id="eb117-196">Similarly, the sort order can be significantly different across the type systems.</span></span> <span data-ttu-id="eb117-197">Cette différence concerne le tri des résultats.</span><span class="sxs-lookup"><span data-stu-id="eb117-197">This difference affects the sorting of results.</span></span> <span data-ttu-id="eb117-198"><xref:System.Guid> est trié sur les 16 octets dans l'ordre lexicographique (`IComparable()`), tandis que T-SQL compare les GUID dans l'ordre suivant : node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span><span class="sxs-lookup"><span data-stu-id="eb117-198"><xref:System.Guid> is sorted on all 16 bytes by lexicographic order (`IComparable()`), whereas T-SQL compares GUIDs in the following order: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span></span> <span data-ttu-id="eb117-199">Cette organisation a été définie dans SQL 7.0 lorsque les GUID générés par NT présentaient cet ordre d'octets.</span><span class="sxs-lookup"><span data-stu-id="eb117-199">This ordering was done in SQL 7.0 when NT-generated GUIDs had such an octet order.</span></span> <span data-ttu-id="eb117-200">Cette approche a permis de s'assurer que les GUID générés sur le même cluster de nœuds se présentaient dans l'ordre séquentiel en fonction de l'horodatage.</span><span class="sxs-lookup"><span data-stu-id="eb117-200">The approach ensured that GUIDs generated at the same node cluster came together in sequential order according to timestamp.</span></span> <span data-ttu-id="eb117-201">Elle s'est également avérée utile pour la génération d'index (les insertions deviennent des ajouts plutôt que des E/S aléatoires).</span><span class="sxs-lookup"><span data-stu-id="eb117-201">The approach was also useful for building indexes (inserts become appends instead of random IOs).</span></span> <span data-ttu-id="eb117-202">L'ordre a été brouillé ultérieurement dans Windows en raison de problèmes de confidentialité, mais SQL doit maintenir la compatibilité.</span><span class="sxs-lookup"><span data-stu-id="eb117-202">The order was scrambled later in Windows because of privacy concerns, but SQL must maintain compatibility.</span></span> <span data-ttu-id="eb117-203">Une solution de contournement consiste <xref:System.Data.SqlTypes.SqlGuid> à utiliser <xref:System.Guid>à la place de.</span><span class="sxs-lookup"><span data-stu-id="eb117-203">A workaround is to use <xref:System.Data.SqlTypes.SqlGuid> instead of <xref:System.Guid>.</span></span>

### <a name="operator-and-function-differences"></a><span data-ttu-id="eb117-204">Différences d'opérateur et de fonction</span><span class="sxs-lookup"><span data-stu-id="eb117-204">Operator and Function Differences</span></span>

<span data-ttu-id="eb117-205">Les opérateurs et les fonctions qui sont pour l'essentiel comparables ont une sémantique légèrement différente.</span><span class="sxs-lookup"><span data-stu-id="eb117-205">Operators and functions that are essentially comparable have subtly different semantics.</span></span> <span data-ttu-id="eb117-206">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="eb117-206">For example:</span></span>

- <span data-ttu-id="eb117-207">C# spécifie une sémantique de « court-circuit » selon l’ordre lexical des opérandes pour les opérateurs logiques `&&` et `||`.</span><span class="sxs-lookup"><span data-stu-id="eb117-207">C# specifies short circuit semantics based on lexical order of operands for logical operators `&&` and `||`.</span></span> <span data-ttu-id="eb117-208">SQL est destiné aux requêtes basées sur des ensembles et laisse par conséquent une plus grande marge de manœuvre à l'optimiseur pour décider de l'ordre d'exécution.</span><span class="sxs-lookup"><span data-stu-id="eb117-208">SQL on the other hand is targeted for set-based queries and therefore provides more freedom for the optimizer to decide the order of execution.</span></span> <span data-ttu-id="eb117-209">Les conséquences sont notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb117-209">Some of the implications include the following:</span></span>

  - <span data-ttu-id="eb117-210">Une traduction sémantiquement équivalente nécessitera «`CASE` ...</span><span class="sxs-lookup"><span data-stu-id="eb117-210">Semantically equivalent translation would require "`CASE` …</span></span> <span data-ttu-id="eb117-211">`WHEN` …</span><span class="sxs-lookup"><span data-stu-id="eb117-211">`WHEN` …</span></span> <span data-ttu-id="eb117-212">`THEN`«Construct dans SQL pour éviter la réorganisation de l’exécution des opérandes.</span><span class="sxs-lookup"><span data-stu-id="eb117-212">`THEN`" construct in SQL to avoid reordering of operand execution.</span></span>

  - <span data-ttu-id="eb117-213">`AND` Une traduction / C# faible des opérateurs peut provoquer des erreurs inattendues si l’expression repose sur l’évaluation du deuxième opérande basé sur le résultat de l’évaluation du premier opérande. `OR`</span><span class="sxs-lookup"><span data-stu-id="eb117-213">A loose translation to `AND`/`OR` operators could cause unexpected errors if the C# expression relies on evaluation the second operand being based on the result of the evaluation of the first operand.</span></span>

- <span data-ttu-id="eb117-214">`Round()`la fonction a une sémantique différente dans .NET Framework et dans T-SQL.</span><span class="sxs-lookup"><span data-stu-id="eb117-214">`Round()` function has different semantics in .NET Framework and in T-SQL.</span></span>

- <span data-ttu-id="eb117-215">L'index de départ des chaînes correspond à 0 dans CLR et à 1 dans SQL.</span><span class="sxs-lookup"><span data-stu-id="eb117-215">Starting index for strings is 0 in the CLR but 1 in SQL.</span></span> <span data-ttu-id="eb117-216">Par conséquent, toute fonction comportant des index nécessite une traduction des index.</span><span class="sxs-lookup"><span data-stu-id="eb117-216">Therefore, any function that has index needs index translation.</span></span>

- <span data-ttu-id="eb117-217">Contrairement à SQL, CLR prend en charge l'opérateur modulo (%) pour les nombres à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="eb117-217">The CLR supports modulus (‘%’) operator for floating point numbers but SQL does not.</span></span>

- <span data-ttu-id="eb117-218">L'opérateur `Like` acquiert efficacement des surcharges automatiques selon des conversions implicites.</span><span class="sxs-lookup"><span data-stu-id="eb117-218">The `Like` operator effectively acquires automatic overloads based on implicit conversions.</span></span> <span data-ttu-id="eb117-219">Bien que l'opérateur `Like` soit défini pour fonctionner sur des types de chaînes de caractères, la conversion implicite de types numériques ou types `DateTime` permet également l'utilisation de ces types non-chaînes avec `Like`.</span><span class="sxs-lookup"><span data-stu-id="eb117-219">Although the `Like` operator is defined to operate on character string types, implicit conversion from numeric types or `DateTime` types allows for those non-string types to be used with `Like` just as well.</span></span> <span data-ttu-id="eb117-220">Dans CTS, il n'existe pas de conversion implicite comparable.</span><span class="sxs-lookup"><span data-stu-id="eb117-220">In CTS, comparable implicit conversions do not exist.</span></span> <span data-ttu-id="eb117-221">Par conséquent, des surcharges supplémentaires sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="eb117-221">Therefore, additional overloads are needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="eb117-222">Ce comportement de l'opérateur `Like` s'applique uniquement à C# ; le mot clé `Like` de Visual Basic reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="eb117-222">This `Like` operator behavior applies to C# only; the Visual Basic `Like` keyword is unchanged.</span></span>

- <span data-ttu-id="eb117-223">Le dépassement de capacité est toujours vérifié dans SQL, mais il doit être C# spécifié explicitement dans (pas dans Visual Basic) pour éviter ajustable.</span><span class="sxs-lookup"><span data-stu-id="eb117-223">Overflow is always checked in SQL but it has to be explicitly specified in C# (not in Visual Basic) to avoid wraparound.</span></span> <span data-ttu-id="eb117-224">Considérons des colonnes d'entiers C1, C2 et C3, si C1+C2 est stocké dans C3 (Update T Set C3 = C1+C2).</span><span class="sxs-lookup"><span data-stu-id="eb117-224">Given integer columns C1, C2 and C3, if C1+C2 is stored in C3 (Update T Set C3 = C1 + C2).</span></span>

    ```sql
    create table T3 (
        Col1      integer,
        Col2      integer
    )
    insert into T3 (col1, col2) values (2147483647, 5)
    -- Valid values: max integer value and 5.
    select * from T3 where col1 + col2 < 0
    -- Produces arithmetic overflow error.
    ```

[!code-csharp[DLinqMismatch#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#5)]
[!code-vb[DLinqMismatch#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#5)]

- <span data-ttu-id="eb117-225">SQL effectue un arrondi arithmétique symétrique quand .NET Framework utilise l’arrondi bancaire.</span><span class="sxs-lookup"><span data-stu-id="eb117-225">SQL performs symmetric arithmetic rounding while .NET Framework uses banker’s rounding.</span></span> <span data-ttu-id="eb117-226">Pour plus d'informations, consultez l'article 196652 de la Base de connaissances.</span><span class="sxs-lookup"><span data-stu-id="eb117-226">See Knowledgebase article 196652 for additional details.</span></span>

- <span data-ttu-id="eb117-227">Par défaut, les comparaisons de chaînes de caractères ne sont pas sensibles à la casse dans SQL pour les paramètres régionaux communs.</span><span class="sxs-lookup"><span data-stu-id="eb117-227">By default, for common locales, character-string comparisons are case-insensitive in SQL.</span></span> <span data-ttu-id="eb117-228">Dans Visual Basic et C#, elles sont sensibles à la casse.</span><span class="sxs-lookup"><span data-stu-id="eb117-228">In Visual Basic and in C#, they are case-sensitive.</span></span> <span data-ttu-id="eb117-229">Par exemple, `s == "Food"` (`s = "Food"` dans Visual Basic) et `s == "Food"` peut produire des résultats différents `s` si `food`est.</span><span class="sxs-lookup"><span data-stu-id="eb117-229">For example, `s == "Food"` (`s = "Food"` in Visual Basic) and `s == "Food"` can yield different results if `s` is `food`.</span></span>

    ```sql
    -- Assume default US-English locale (case insensitive).
    create table T4 (
        Col1      nvarchar (256)
    )
    insert into T4 values (‘Food’)
    insert into T4 values (‘FOOD’)
    select * from T4 where Col1 = ‘food’
    -- Both the rows are returned because of case-insensitive matching.
    ```

[!code-csharp[DLinqMismatch#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#6)]
[!code-vb[DLinqMismatch#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#6)]

- <span data-ttu-id="eb117-230">Les opérateurs/fonctions appliqués aux arguments de type de caractères de longueur fixe dans SQL ont une sémantique sensiblement différente par rapport aux mêmes opérateurs/fonctions appliqués à un objet <xref:System.String?displayProperty=nameWithType> CLR.</span><span class="sxs-lookup"><span data-stu-id="eb117-230">Operators/ functions applied to fixed length character type arguments in SQL have significantly different semantics than the same operators/functions applied to the CLR <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="eb117-231">Cela peut également être considéré comme une extension du problème d’équivalents manquants abordé dans la section consacrée aux types.</span><span class="sxs-lookup"><span data-stu-id="eb117-231">This could also be viewed as an extension of the missing counterpart problem discussed in the section about types.</span></span>

    ```sql
    create table T4 (
        Col1      nchar(4)
    )
    Insert into T5(Col1) values ('21');
    Insert into T5(Col1) values ('1021');
    Select * from T5 where Col1 like '%1'
    -- Only the second row with Col1 = '1021' is returned.
    -- Not the first row!
    ```

     [!code-csharp[DLinqMismatch#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#7)]
     [!code-vb[DLinqMismatch#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#7)]

     <span data-ttu-id="eb117-232">La concaténation de chaînes pose le même problème.</span><span class="sxs-lookup"><span data-stu-id="eb117-232">A similar problem occurs with string concatenation.</span></span>

    ```sql
    create table T6 (
        Col1      nchar(4)
        Col2       nchar(4)
    )
    Insert into T6 values ('a', 'b');
    Select Col1+Col2 from T6
    -- Returns concatenation of padded strings "a   b   " and not "ab".
    ```

<span data-ttu-id="eb117-233">En résumé, une traduction circonvolutionnée peut être requise pour les expressions CLR et des opérateurs/fonctions supplémentaires peuvent être nécessaires pour exposer les fonctionnalités SQL.</span><span class="sxs-lookup"><span data-stu-id="eb117-233">In summary, a convoluted translation might be required for CLR expressions and additional operators/functions may be necessary to expose SQL functionality.</span></span>

### <a name="type-casting"></a><span data-ttu-id="eb117-234">Cast de type</span><span class="sxs-lookup"><span data-stu-id="eb117-234">Type Casting</span></span>

<span data-ttu-id="eb117-235">Dans C# et SQL, les utilisateurs peuvent substituer la sémantique par défaut d'expressions en utilisant des casts de types explicites (`Cast` et `Convert`).</span><span class="sxs-lookup"><span data-stu-id="eb117-235">In C# and in SQL, users can override the default semantics of expressions by using explicit type casts (`Cast` and `Convert`).</span></span> <span data-ttu-id="eb117-236">Toutefois, l'exposition de cette fonction sur la limite du système de type crée un dilemme.</span><span class="sxs-lookup"><span data-stu-id="eb117-236">However, exposing this capability across the type system boundary poses a dilemma.</span></span> <span data-ttu-id="eb117-237">Un cast SQL qui fournit la sémantique souhaitée ne peut pas être traduit facilement en cast C# correspondant.</span><span class="sxs-lookup"><span data-stu-id="eb117-237">A SQL cast that provides the desired semantics cannot be easily translated to a corresponding C# cast.</span></span> <span data-ttu-id="eb117-238">Par contre, un cast C# ne peut pas être traduit directement en cast SQL équivalent en raison des incompatibilités de type, des équivalents manquants et des hiérarchies de priorité des types.</span><span class="sxs-lookup"><span data-stu-id="eb117-238">On the other hand, a C# cast cannot be directly translated into an equivalent SQL cast because of type mismatches, missing counterparts, and different type precedence hierarchies.</span></span> <span data-ttu-id="eb117-239">Il existe un compromis entre l'exposition de l'incompatibilité du système de type et une perte importante de puissance d'expression.</span><span class="sxs-lookup"><span data-stu-id="eb117-239">There is a trade-off between exposing the type system mismatch and losing significant power of expression.</span></span>

<span data-ttu-id="eb117-240">Dans d’autres cas, le cast de type peut ne pas être nécessaire dans un domaine de validation d’une expression mais peut être requis pour s’assurer qu’un mappage non défini par défaut est appliqué correctement à l’expression.</span><span class="sxs-lookup"><span data-stu-id="eb117-240">In other cases, type casting might not be needed in either domain for validation of an expression but might be required to make sure that a non-default mapping is correctly applied to the expression.</span></span>

```sql
-- Example from "Non-default Mapping" section extended
create table T5 (
    Col1      nvarchar(10),
    Col2      nvarchar(10)
)
Insert into T5(col1, col2) values (‘3’, ‘2’);
```

[!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
[!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]

```sql
Select *
From T5
Where Col1 + Col2 > 4
-- "Col1 + Col2" expr evaluates to '32'
```

## <a name="performance-issues"></a><span data-ttu-id="eb117-241">Problèmes de performances</span><span class="sxs-lookup"><span data-stu-id="eb117-241">Performance Issues</span></span>

<span data-ttu-id="eb117-242">La prise en compte de certaines différences de type SQL Server-CLR peut entraîner une baisse des performances lors du passage entre les systèmes de type CLR et SQL Server.</span><span class="sxs-lookup"><span data-stu-id="eb117-242">Accounting for some SQL Server-CLR type differences may result in a decrease in performance when crossing between the CLR and SQL Server type systems.</span></span> <span data-ttu-id="eb117-243">Voici quelques exemples de scénarios affectant les performances :</span><span class="sxs-lookup"><span data-stu-id="eb117-243">Examples of scenarios impacting performance include the following:</span></span>

- <span data-ttu-id="eb117-244">Ordre d'évaluation de la logique et/ou des opérateurs forcé</span><span class="sxs-lookup"><span data-stu-id="eb117-244">Forced order of evaluation for logical and/or operators</span></span>

- <span data-ttu-id="eb117-245">La génération de SQL pour appliquer l'ordre d'évaluation des prédicats limite les capacités de l'optimiseur SQL.</span><span class="sxs-lookup"><span data-stu-id="eb117-245">Generating SQL to enforce order of predicate evaluation restricts the SQL optimizer’s ability.</span></span>

- <span data-ttu-id="eb117-246">Les conversions de type, qu'elles soient introduites par un compilateur CLR ou par une implémentation de requête objet-relationnel, peuvent réduire l'utilisation de l'index.</span><span class="sxs-lookup"><span data-stu-id="eb117-246">Type conversions, whether introduced by a CLR compiler or by an Object-Relational query implementation, may curtail index usage.</span></span>

     <span data-ttu-id="eb117-247">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="eb117-247">For example,</span></span>

    ```sql
    -- Table DDL
    create table T5 (
        Col1      varchar(100)
    )
    ```

     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]

     <span data-ttu-id="eb117-248">Prenons la traduction de l'expression `(s = SOME_STRING_CONSTANT)`.</span><span class="sxs-lookup"><span data-stu-id="eb117-248">Consider the translation of expression `(s = SOME_STRING_CONSTANT)`.</span></span>

    ```sql
    -- Corresponding part of SQL where clause
    Where …
    Col1 = SOME_STRING_CONSTANT
    -- This expression is of the form <varchar> = <nvarchar>.
    -- Hence SQL introduces a conversion from varchar to nvarchar,
    --   resulting in
    Where …
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT
    -- Cannot use the index for column Col1 for some implementations.
    ```

<span data-ttu-id="eb117-249">Outre les différences sémantiques, il est important de prendre en compte l'impact sur les performances lors du passage entre les systèmes de types SQL Server et CLR.</span><span class="sxs-lookup"><span data-stu-id="eb117-249">In addition to semantic differences, it is important to consider impacts to performance when crossing between the SQL Server and CLR type systems.</span></span> <span data-ttu-id="eb117-250">Pour les grands groupes de données, de tels problèmes de performances peuvent déterminer si une application est déployable.</span><span class="sxs-lookup"><span data-stu-id="eb117-250">For large data sets, such performance issues can determine whether an application is deployable.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb117-251">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb117-251">See also</span></span>

- [<span data-ttu-id="eb117-252">Informations générales</span><span class="sxs-lookup"><span data-stu-id="eb117-252">Background Information</span></span>](background-information.md)
