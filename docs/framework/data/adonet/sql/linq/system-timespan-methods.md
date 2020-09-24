---
title: System.TimeSpan, méthodes
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: 15b6c8bd5c9cce8e6d1bac030c6b7f6b40df6cd4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155586"
---
# <a name="systemtimespan-methods"></a><span data-ttu-id="dab85-102">System.TimeSpan, méthodes</span><span class="sxs-lookup"><span data-stu-id="dab85-102">System.TimeSpan Methods</span></span>

<span data-ttu-id="dab85-103">La prise en charge des membres pour <xref:System.TimeSpan?displayProperty=nameWithType> dépend beaucoup des versions du .NET Framework et de Microsoft SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="dab85-103">Member support for <xref:System.TimeSpan?displayProperty=nameWithType> greatly depends on the versions of the .NET Framework and Microsoft SQL Server that you are using.</span></span>  
  
 <span data-ttu-id="dab85-104">Lorsqu'une méthode, une propriété ou un opérateur n'est pas pris en charge, cela implique que LINQ to SQL ne peut pas traduire le membre à des fins d'exécution sur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dab85-104">When a method, operator, or property is unsupported; it means that LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="dab85-105">Vous pouvez toujours utiliser ces membres dans votre code,</span><span class="sxs-lookup"><span data-stu-id="dab85-105">You may still be able to use these members in your code.</span></span> <span data-ttu-id="dab85-106">ceux-ci devant toutefois être évalués avant la traduction de la requête en données Transact-SQL ou après l'extraction des résultats de la base de données.</span><span class="sxs-lookup"><span data-stu-id="dab85-106">However, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="previous-limitations"></a><span data-ttu-id="dab85-107">Limites précédentes</span><span class="sxs-lookup"><span data-stu-id="dab85-107">Previous Limitations</span></span>  

 <span data-ttu-id="dab85-108">Lorsque vous utilisez LINQ to SQL avec des versions du .NET Framework antérieures au .NET Framework 3.5 SP1, vous ne pouvez pas mapper les champs de base de données SQL Server à <xref:System.TimeSpan?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dab85-108">When using LINQ to SQL with versions of the .NET Framework prior to .NET Framework 3.5 SP1, you cannot map SQL Server database fields to <xref:System.TimeSpan?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dab85-109">Toutefois, les opérations sur <xref:System.TimeSpan> sont prises en charge car des valeurs <xref:System.TimeSpan> peuvent être retournées par la soustraction <xref:System.DateTime> ou introduites dans une expression sous forme de variable littérale ou liée.</span><span class="sxs-lookup"><span data-stu-id="dab85-109">However, operations on <xref:System.TimeSpan> are supported because <xref:System.TimeSpan> values can be returned from <xref:System.DateTime> subtraction or introduced into an expression as a literal or bound variable.</span></span>  
  
## <a name="supported-systemtimespan-member-support"></a><span data-ttu-id="dab85-110">Prise en charge des membres System. TimeSpan pris en charge</span><span class="sxs-lookup"><span data-stu-id="dab85-110">Supported System.TimeSpan member support</span></span>

 <span data-ttu-id="dab85-111">Les méthodes, propriétés et opérateurs pris en charge par LINQ to SQL suivants peuvent être utilisés dans les requêtes LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="dab85-111">The following LINQ to SQL-supported methods, operators, and properties are available for you to use in your LINQ to SQL queries.</span></span> <span data-ttu-id="dab85-112">Une fois mappés dans le modèle objet ou le fichier de mappage externe, LINQ to SQL vous permet d'appeler un grand nombre des membres <xref:System.TimeSpan?displayProperty=nameWithType> à l'intérieur des requêtes LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="dab85-112">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call many of the <xref:System.TimeSpan?displayProperty=nameWithType> members inside your LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="dab85-113">Méthodes <xref:System.TimeSpan> prises en charge</span><span class="sxs-lookup"><span data-stu-id="dab85-113">Supported <xref:System.TimeSpan> Methods</span></span>|<span data-ttu-id="dab85-114">Opérateurs <xref:System.TimeSpan> pris en charge</span><span class="sxs-lookup"><span data-stu-id="dab85-114">Supported <xref:System.TimeSpan> Operators</span></span>|<span data-ttu-id="dab85-115">Propriétés <xref:System.TimeSpan> prises en charge</span><span class="sxs-lookup"><span data-stu-id="dab85-115">Supported <xref:System.TimeSpan> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<xref:System.TimeSpan.MinValue>|  
  
> [!NOTE]
> <span data-ttu-id="dab85-116">La capacité à mapper <xref:System.TimeSpan?displayProperty=nameWithType> à une colonne `TIME` SQL à l'aide de LINQ to SQL requiert .NET Framework 3.5 SP1 et version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="dab85-116">The ability to map <xref:System.TimeSpan?displayProperty=nameWithType> to a SQL `TIME` column with LINQ to SQL requires the .NET Framework 3.5 SP1 and beyond.</span></span> <span data-ttu-id="dab85-117">Le type de données `TIME` SQL est uniquement disponible à partir de Microsoft SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="dab85-117">The SQL `TIME` data type is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
### <a name="addition-and-subtraction"></a><span data-ttu-id="dab85-118">Addition et soustraction</span><span class="sxs-lookup"><span data-stu-id="dab85-118">Addition and Subtraction</span></span>  

 <span data-ttu-id="dab85-119">Contrairement au type <xref:System.TimeSpan?displayProperty=nameWithType> SQL, le type `TIME` CLR prend en charge l'addition et la soustraction.</span><span class="sxs-lookup"><span data-stu-id="dab85-119">Although the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type does support addition and subtraction, the SQL `TIME` type does not.</span></span> <span data-ttu-id="dab85-120">De ce fait, les requêtes LINQ to SQL génèrent des erreurs en cas de tentative d'addition et de soustraction lorsqu'elles sont mappées au type `TIME` SQL.</span><span class="sxs-lookup"><span data-stu-id="dab85-120">Because of this, your LINQ to SQL queries will generate errors if they attempt addition and subtraction when they are mapped to the SQL `TIME` type.</span></span> <span data-ttu-id="dab85-121">Vous pouvez trouver d’autres considérations relatives à l’utilisation des types de date et d’heure SQL dans [le mappage de type SQL-CLR](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="dab85-121">You can find other considerations for working with SQL date and time types in [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dab85-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dab85-122">See also</span></span>

- [<span data-ttu-id="dab85-123">Concepts relatifs aux requêtes</span><span class="sxs-lookup"><span data-stu-id="dab85-123">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="dab85-124">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="dab85-124">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="dab85-125">Mappage de type SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="dab85-125">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="dab85-126">Fonctions et types de données</span><span class="sxs-lookup"><span data-stu-id="dab85-126">Data Types and Functions</span></span>](data-types-and-functions.md)
