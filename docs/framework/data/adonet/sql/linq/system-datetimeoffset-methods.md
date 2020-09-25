---
title: System.DateTimeOffset, méthodes
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: ae588b88ca592ce422202d5231b34060ccc22024
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203473"
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="03347-102">System.DateTimeOffset, méthodes</span><span class="sxs-lookup"><span data-stu-id="03347-102">System.DateTimeOffset Methods</span></span>

<span data-ttu-id="03347-103">Une fois mappés dans le modèle objet ou le fichier de mappage externe, LINQ to SQL vous permet d'appeler la plupart des méthodes, opérateurs et propriétés <xref:System.DateTimeOffset?displayProperty=nameWithType> à partir des requêtes LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="03347-103">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="03347-104">Les seules méthodes non prises en charge sont celles héritées de <xref:System.Object?displayProperty=nameWithType> qui n'ont pas de sens dans le contexte des requêtes LINQ to SQL, telles que `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span><span class="sxs-lookup"><span data-stu-id="03347-104">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="03347-105">Ces méthodes ne sont pas prises en charge car LINQ to SQL ne peut pas les traduire à des fins d'exécution sur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="03347-105">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03347-106">La structure <xref:System.DateTimeOffset?displayProperty=nameWithType> CLR (Common Language Runtime), ainsi que la capacité à la mapper à une colonne `DATETIMEOFFSET` SQL à l'aide de LINQ to SQL, requiert le .NET Framework 3.5 SP1 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="03347-106">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="03347-107">La colonne `DATETIMEOFFSET` SQL est uniquement disponible à partir de Microsoft SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="03347-107">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="03347-108">Méthodes de date et d'heure SQLMethods</span><span class="sxs-lookup"><span data-stu-id="03347-108">SQLMethods Date and Time Methods</span></span>  

 <span data-ttu-id="03347-109">Outre les méthodes proposées par la structure <xref:System.DateTimeOffset>, LINQ to SQL fournit également celles répertoriées dans le tableau suivant à partir de la classe <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> pour l'utilisation des données de date et d'heure.</span><span class="sxs-lookup"><span data-stu-id="03347-109">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="03347-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03347-110">See also</span></span>

- [<span data-ttu-id="03347-111">Concepts relatifs aux requêtes</span><span class="sxs-lookup"><span data-stu-id="03347-111">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="03347-112">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="03347-112">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="03347-113">Mappage de type SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="03347-113">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
