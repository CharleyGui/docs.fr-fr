---
title: System.String, méthodes
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: 44d32ed1000ca49d9fc29ffcde4506b44fc975b6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155664"
---
# <a name="systemstring-methods"></a><span data-ttu-id="65a64-102">System.String, méthodes</span><span class="sxs-lookup"><span data-stu-id="65a64-102">System.String Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="65a64-103">ne prend pas en charge les méthodes <xref:System.String> suivantes.</span><span class="sxs-lookup"><span data-stu-id="65a64-103">does not support the following <xref:System.String> methods.</span></span>  
  
## <a name="unsupported-systemstring-methods-in-general"></a><span data-ttu-id="65a64-104">Méthodes System.String non prises en charge en général</span><span class="sxs-lookup"><span data-stu-id="65a64-104">Unsupported System.String Methods in General</span></span>  

 <span data-ttu-id="65a64-105">Méthodes <xref:System.String> non prises en charge en général :</span><span class="sxs-lookup"><span data-stu-id="65a64-105">Unsupported <xref:System.String> methods in general:</span></span>  
  
- <span data-ttu-id="65a64-106">Surcharges prenant en charge la culture (méthodes qui acceptent un `CultureInfo`  /  `StringComparison`  /  `IFormatProvider` ).</span><span class="sxs-lookup"><span data-stu-id="65a64-106">Culture-aware overloads (methods that take a `CultureInfo` / `StringComparison` / `IFormatProvider`).</span></span>  
  
- <span data-ttu-id="65a64-107">Méthodes qui acceptent ou génèrent un tableau de `char`.</span><span class="sxs-lookup"><span data-stu-id="65a64-107">Methods that take or produce a `char` array.</span></span>  
  
## <a name="unsupported-systemstring-static-methods"></a><span data-ttu-id="65a64-108">Méthodes statiques System.String non prises en charge</span><span class="sxs-lookup"><span data-stu-id="65a64-108">Unsupported System.String Static Methods</span></span>  
  
|<span data-ttu-id="65a64-109">Méthodes statiques System.String non prises en charge</span><span class="sxs-lookup"><span data-stu-id="65a64-109">Unsupported System.String Static Methods</span></span>|  
|----------------------------------------------|  
|<xref:System.String.Copy%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.String%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|  
  
## <a name="unsupported-systemstring-non-static-methods"></a><span data-ttu-id="65a64-110">Méthodes non statiques System.String non prises en charge</span><span class="sxs-lookup"><span data-stu-id="65a64-110">Unsupported System.String Non-static Methods</span></span>  
  
|<span data-ttu-id="65a64-111">Méthodes non statiques System.String non prises en charge</span><span class="sxs-lookup"><span data-stu-id="65a64-111">Unsupported System.String Non-static Methods</span></span>|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="65a64-112">Différences par rapport à .NET</span><span class="sxs-lookup"><span data-stu-id="65a64-112">Differences from .NET</span></span>  
  
- <span data-ttu-id="65a64-113">Les requêtes n'expliquent pas les classements SQL Server qui peuvent être appliqués sur le serveur, et par conséquent, fournissent par défaut des comparaisons dépendantes de la culture qui ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="65a64-113">Queries do not account for SQL Server collations that might be in effect on the server, and therefore will provide culture-sensitive, case-insensitive comparisons by default.</span></span> <span data-ttu-id="65a64-114">Ce comportement diffère de la sémantique par défaut sensible à la casse du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65a64-114">This behavior differs from the default, case-sensitive semantics of the .NET Framework.</span></span>  
  
- <span data-ttu-id="65a64-115">Lorsque `LastIndexOf` retourne 0, la chaîne est `NULL` ou la position trouvée est 0.</span><span class="sxs-lookup"><span data-stu-id="65a64-115">When `LastIndexOf` returns 0, either the string is `NULL` or the found position is 0.</span></span>  
  
- <span data-ttu-id="65a64-116">Des résultats inattendus peuvent être retournés de la concaténation ou d'autres opérations sur les chaînes de longueur fixe (`CHAR`, `NCHAR`), car le remplissage de ces types s'effectue automatiquement dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="65a64-116">Unexpected results might be returned from concatenation or other operations on fixed-length strings (`CHAR`, `NCHAR`), because these types automatically have padding applied in the database.</span></span>  
  
- <span data-ttu-id="65a64-117">Comme de nombreuses méthodes, telles que `Replace`, `ToLower`, `ToUpper` et l'indexeur de caractère, n'ont aucune traduction valide pour les colonnes `TEXT` ou `NTEXT` et XML, `SqlExceptions` se produit si la traduction se produit normalement.</span><span class="sxs-lookup"><span data-stu-id="65a64-117">Because many methods, such as `Replace`, `ToLower`, `ToUpper`, and the character indexer, have no valid translation for `TEXT` or `NTEXT` columns and XML, `SqlExceptions` occur if translated normally.</span></span> <span data-ttu-id="65a64-118">Ce comportement est considéré comme acceptable pour ces types.</span><span class="sxs-lookup"><span data-stu-id="65a64-118">This behavior is considered acceptable for these types.</span></span> <span data-ttu-id="65a64-119">Toutefois, toutes les opérations de chaînes doivent correspondre à la sémantique Common Language Runtime (CLR) pour `VARCHAR`, `NVARCHAR`, `VARCHAR(max)` et `NVARCHAR(max)`.</span><span class="sxs-lookup"><span data-stu-id="65a64-119">However, all string operations must match common language runtime (CLR) semantics for `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, and `NVARCHAR(max)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65a64-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65a64-120">See also</span></span>

- [<span data-ttu-id="65a64-121">Fonctions et types de données</span><span class="sxs-lookup"><span data-stu-id="65a64-121">Data Types and Functions</span></span>](data-types-and-functions.md)
