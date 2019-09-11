---
title: Problèmes connus et éléments à prendre en compte dans LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 4fb7d574fdb9bd6bd9465cffaf0fda5069b2c0ee
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854387"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="b39d8-102">Problèmes connus et éléments à prendre en compte dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b39d8-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="b39d8-103">Cette section fournit des informations sur les problèmes connus liés aux requêtes LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="b39d8-103">This section provides information about known issues with LINQ to Entities queries.</span></span>  
  
- [<span data-ttu-id="b39d8-104">Requêtes LINQ qui ne peuvent pas être mises en cache</span><span class="sxs-lookup"><span data-stu-id="b39d8-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="b39d8-105">Informations de classement perdues</span><span class="sxs-lookup"><span data-stu-id="b39d8-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="b39d8-106">Entiers non signés non pris en charge</span><span class="sxs-lookup"><span data-stu-id="b39d8-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="b39d8-107">Erreurs de conversion de type</span><span class="sxs-lookup"><span data-stu-id="b39d8-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="b39d8-108">Référencement de variables non scalaires non prises en charge</span><span class="sxs-lookup"><span data-stu-id="b39d8-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="b39d8-109">Les requêtes imbriquées peuvent échouer avec SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="b39d8-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="b39d8-110">Projection dans un type anonyme</span><span class="sxs-lookup"><span data-stu-id="b39d8-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="b39d8-111">Requêtes LINQ qui ne peuvent pas être mises en cache</span><span class="sxs-lookup"><span data-stu-id="b39d8-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="b39d8-112">Depuis le .NET Framework 4.5, les requêtes LINQ to Entities sont automatiquement mises en cache.</span><span class="sxs-lookup"><span data-stu-id="b39d8-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="b39d8-113">Cependant, les requêtes LINQ to Entities qui appliquent l’opérateur `Enumerable.Contains` aux collections en mémoire ne sont pas automatiquement mises en cache.</span><span class="sxs-lookup"><span data-stu-id="b39d8-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="b39d8-114">Le paramétrage des collections en mémoire dans les requêtes LINQ compilées n’est pas autorisé.</span><span class="sxs-lookup"><span data-stu-id="b39d8-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a><span data-ttu-id="b39d8-115">Perte des informations de tri</span><span class="sxs-lookup"><span data-stu-id="b39d8-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="b39d8-116">La projection de colonnes dans un type anonyme entraîne la perte des informations de classement dans certaines requêtes exécutées sur une base de données SQL Server 2005 définie à un niveau de compatibilité de « 80 ».</span><span class="sxs-lookup"><span data-stu-id="b39d8-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a SQL Server 2005 database set to a compatibility level of "80".</span></span>  <span data-ttu-id="b39d8-117">Cela se produit lorsqu'un nom de colonne figurant dans la liste Order by correspond à un nom de colonne dans le sélecteur, comme l'illustre l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b39d8-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="b39d8-118">Entiers non signés non pris en charge</span><span class="sxs-lookup"><span data-stu-id="b39d8-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="b39d8-119">La spécification d’un type d’entier non signé dans une requête LINQ to Entities n’est pas prise en charge, car le Entity Framework ne prend pas en charge les entiers non signés.</span><span class="sxs-lookup"><span data-stu-id="b39d8-119">Specifying an unsigned integer type in a LINQ to Entities query is not supported because the Entity Framework does not support unsigned integers.</span></span> <span data-ttu-id="b39d8-120">Si vous spécifiez un entier non signé, une <xref:System.ArgumentException> exception est levée pendant la traduction de l’expression de requête, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b39d8-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="b39d8-121">Dans cet exemple, la requête vise à extraire une commande dont le numéro est 48000.</span><span class="sxs-lookup"><span data-stu-id="b39d8-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a><span data-ttu-id="b39d8-122">Erreurs de conversion de type</span><span class="sxs-lookup"><span data-stu-id="b39d8-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="b39d8-123">En Visual Basic, lorsqu'une propriété est mappée à une colonne de type bit SQL Server avec une valeur de 1 à l'aide de la fonction `CByte`, une exception <xref:System.Data.SqlClient.SqlException> est levée avec un message « Erreur de dépassement arithmétique ».</span><span class="sxs-lookup"><span data-stu-id="b39d8-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="b39d8-124">L'exemple suivant interroge la colonne `Product.MakeFlag` dans l'exemple de base de données AdventureWorks et une exception est levée lorsque les résultats de la requête sont itérés.</span><span class="sxs-lookup"><span data-stu-id="b39d8-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="b39d8-125">Référencement de variables non scalaires non pris en charge</span><span class="sxs-lookup"><span data-stu-id="b39d8-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="b39d8-126">Le référencement d'une variable non scalaire, telle qu'une entité, dans une requête n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b39d8-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="b39d8-127">Lorsqu'une telle requête s'exécute, une exception <xref:System.NotSupportedException> est levée avec un message indiquant « Impossible de créer une valeur constante de type «`EntityType`.</span><span class="sxs-lookup"><span data-stu-id="b39d8-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="b39d8-128">Seuls les types primitifs (« Int32, String et Guid ») sont pris en charge dans ce contexte. »</span><span class="sxs-lookup"><span data-stu-id="b39d8-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b39d8-129">Le référencement d’une collection de variables scalaires est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b39d8-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="b39d8-130">Les requêtes imbriquées peuvent échouer avec SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="b39d8-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="b39d8-131">Avec SQL Server 2000, les requêtes LINQ to Entities peuvent échouer si elles produisent des requêtes Transact-SQL imbriquées qui ont trois niveaux ou plus de profondeur.</span><span class="sxs-lookup"><span data-stu-id="b39d8-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="b39d8-132">Projection dans un type anonyme</span><span class="sxs-lookup"><span data-stu-id="b39d8-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="b39d8-133">Si vous définissez le chemin d’accès de votre requête initiale pour inclure des objets connexes à l’aide de la méthode <xref:System.Data.Objects.ObjectQuery%601.Include%2A> sur <xref:System.Data.Objects.ObjectQuery%601> et si vous utilisez LINQ pour projeter les objets retournés dans un type anonyme, les objets spécifiés dans la méthode d’inclusion ne sont pas inclus dans les résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="b39d8-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="b39d8-134">Pour obtenir des objets connexes, ne projetez pas les types retournés dans un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="b39d8-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="b39d8-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b39d8-135">See also</span></span>

- [<span data-ttu-id="b39d8-136">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b39d8-136">LINQ to Entities</span></span>](linq-to-entities.md)
