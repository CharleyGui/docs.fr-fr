---
title: System.DateTime, méthodes
ms.date: 03/30/2017
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
ms.openlocfilehash: e3bffb1f47c19ccf7ea59151cd3545a15d59f1f2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203486"
---
# <a name="systemdatetime-methods"></a><span data-ttu-id="db60a-102">System.DateTime, méthodes</span><span class="sxs-lookup"><span data-stu-id="db60a-102">System.DateTime Methods</span></span>

<span data-ttu-id="db60a-103">Les méthodes, propriétés et opérateurs pris en charge par LINQ to SQL suivants peuvent être utilisés dans les requêtes LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="db60a-103">The following LINQ to SQL-supported methods, operators, and properties are available to use in LINQ to SQL queries.</span></span> <span data-ttu-id="db60a-104">Lorsqu'une méthode, une propriété ou un opérateur n'est pas pris en charge, LINQ to SQL ne peut pas traduire le membre à des fins d'exécution sur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="db60a-104">When a method, operator or property is unsupported, LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="db60a-105">Vous pouvez utiliser ces membres dans votre code, ceux-ci devant toutefois être évalués avant la traduction de la requête en données Transact-SQL ou après l'extraction des résultats de la base de données.</span><span class="sxs-lookup"><span data-stu-id="db60a-105">You may use these members in your code, however, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="supported-systemdatetime-members"></a><span data-ttu-id="db60a-106">Membres System.DateTime pris en charge</span><span class="sxs-lookup"><span data-stu-id="db60a-106">Supported System.DateTime Members</span></span>  

 <span data-ttu-id="db60a-107">Une fois mappés dans le modèle objet ou le fichier de mappage externe, LINQ to SQL vous permet d'appeler les membres <xref:System.DateTime?displayProperty=nameWithType> suivants à l'intérieur des requêtes LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="db60a-107">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call the following <xref:System.DateTime?displayProperty=nameWithType> members inside LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="db60a-108">Méthodes <xref:System.DateTime> prises en charge</span><span class="sxs-lookup"><span data-stu-id="db60a-108">Supported <xref:System.DateTime> Methods</span></span>|<span data-ttu-id="db60a-109">Opérateurs <xref:System.DateTime> pris en charge</span><span class="sxs-lookup"><span data-stu-id="db60a-109">Supported <xref:System.DateTime> Operators</span></span>|<span data-ttu-id="db60a-110">Propriétés <xref:System.DateTime> prises en charge</span><span class="sxs-lookup"><span data-stu-id="db60a-110">Supported <xref:System.DateTime> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Add%2A>|<xref:System.DateTime.op_Addition%2A>|<xref:System.DateTime.Date%2A>|  
|<xref:System.DateTime.AddDays%2A>|<xref:System.DateTime.op_Equality%2A>|<xref:System.DateTime.Day%2A>|  
|<xref:System.DateTime.AddHours%2A>|<xref:System.DateTime.op_GreaterThan%2A>|<xref:System.DateTime.DayOfWeek%2A>|  
|<xref:System.DateTime.AddMilliseconds%2A>|<xref:System.DateTime.op_GreaterThanOrEqual%2A>|<xref:System.DateTime.DayOfYear%2A>|  
|<xref:System.DateTime.AddMinutes%2A>|<xref:System.DateTime.op_Inequality%2A>|<xref:System.DateTime.Hour%2A>|  
|<xref:System.DateTime.AddMonths%2A>|<xref:System.DateTime.op_LessThan%2A>|<xref:System.DateTime.Millisecond%2A>|  
|<xref:System.DateTime.AddSeconds%2A>|<xref:System.DateTime.op_LessThanOrEqual%2A>|<xref:System.DateTime.Minute%2A>|  
|<xref:System.DateTime.AddTicks%2A>|<xref:System.DateTime.op_Subtraction%2A>|<xref:System.DateTime.Month%2A>|  
|<xref:System.DateTime.AddYears%2A>||<xref:System.DateTime.Now%2A>|  
|<xref:System.DateTime.Compare%2A>||<xref:System.DateTime.Second%2A>|  
|<xref:System.DateTime.CompareTo%28System.DateTime%29>||<xref:System.DateTime.TimeOfDay%2A>|  
|<xref:System.DateTime.Equals%28System.DateTime%29>||<xref:System.DateTime.Today%2A>|  
|||<xref:System.DateTime.Year%2A>|  
  
## <a name="members-not-supported-by-linq-to-sql"></a><span data-ttu-id="db60a-111">Membres non pris en charge par LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="db60a-111">Members Not Supported by LINQ to SQL</span></span>  

 <span data-ttu-id="db60a-112">Les membres suivants ne sont pas pris en charge à l'intérieur des requêtes LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="db60a-112">The following members are not supported inside LINQ to SQL queries.</span></span>  
  
|||  
|-|-|  
|<xref:System.DateTime.IsDaylightSavingTime%2A>|<xref:System.DateTime.IsLeapYear%2A>|  
|<xref:System.DateTime.DaysInMonth%2A>|<xref:System.DateTime.ToBinary%2A>|  
|<xref:System.DateTime.ToFileTime%2A>|<xref:System.DateTime.ToFileTimeUtc%2A>|  
|<xref:System.DateTime.ToLongDateString%2A>|<xref:System.DateTime.ToLongTimeString%2A>|  
|<xref:System.DateTime.ToOADate%2A>|<xref:System.DateTime.ToShortDateString%2A>|  
|<xref:System.DateTime.ToShortTimeString%2A>|<xref:System.DateTime.ToUniversalTime%2A>|  
|<xref:System.DateTime.FromBinary%2A>|<xref:System.DateTime.UtcNow%2A>|  
|<xref:System.DateTime.FromFileTime%2A>|<xref:System.DateTime.FromFileTimeUtc%2A>|  
|<xref:System.DateTime.FromOADate%2A>|<xref:System.DateTime.GetDateTimeFormats%2A>|  
  
## <a name="method-translation-example"></a><span data-ttu-id="db60a-113">Exemple de traduction de méthode</span><span class="sxs-lookup"><span data-stu-id="db60a-113">Method Translation Example</span></span>  

 <span data-ttu-id="db60a-114">Toutes les méthodes prises en charge par LINQ to SQL sont traduites en données Transact-SQL avant d'être envoyées à SQL Server.</span><span class="sxs-lookup"><span data-stu-id="db60a-114">All methods supported by LINQ to SQL are translated to Transact-SQL before they are sent to   SQL Server.</span></span> <span data-ttu-id="db60a-115">Prenons l'exemple du modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="db60a-115">For example, consider the following pattern.</span></span>  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 <span data-ttu-id="db60a-116">Lorsqu'il est reconnu, il est traduit en appel direct à la fonction `DATEDIFF` SQL Server, comme suit :</span><span class="sxs-lookup"><span data-stu-id="db60a-116">When it is recognized, it is translated into a direct call to the SQL Server `DATEDIFF` function, as follows:</span></span>  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="db60a-117">Méthodes de date et d'heure SQLMethods</span><span class="sxs-lookup"><span data-stu-id="db60a-117">SQLMethods Date and Time Methods</span></span>  

 <span data-ttu-id="db60a-118">Outre les méthodes proposées par la structure <xref:System.DateTime>, LINQ to SQL fournit également celles répertoriées dans le tableau suivant à partir de la classe <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> pour l'utilisation des données de date et d'heure.</span><span class="sxs-lookup"><span data-stu-id="db60a-118">In addition to the methods offered by the <xref:System.DateTime> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="db60a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db60a-119">See also</span></span>

- [<span data-ttu-id="db60a-120">Concepts relatifs aux requêtes</span><span class="sxs-lookup"><span data-stu-id="db60a-120">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="db60a-121">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="db60a-121">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="db60a-122">Mappage de type SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="db60a-122">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="db60a-123">Fonctions et types de données</span><span class="sxs-lookup"><span data-stu-id="db60a-123">Data Types and Functions</span></span>](data-types-and-functions.md)
