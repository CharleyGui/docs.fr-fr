---
title: Fonctions canoniques
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: 8949735ba4712b721460335b4579f0a268c91aea
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251276"
---
# <a name="canonical-functions"></a><span data-ttu-id="eddfe-102">Fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="eddfe-102">Canonical Functions</span></span>
<span data-ttu-id="eddfe-103">Cette section décrit les fonctions canoniques qui sont prises en charge par tous les fournisseurs de données et qui peuvent être utilisée par toutes les technologies de requête.</span><span class="sxs-lookup"><span data-stu-id="eddfe-103">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="eddfe-104">Les fonctions canoniques ne peuvent pas être étendues par un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="eddfe-104">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="eddfe-105">Ces fonctions canoniques seront traduites en fonctionnalités de source de données correspondantes pour le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="eddfe-105">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="eddfe-106">De ce fait, les appels de fonction peuvent être exprimés sous une forme commune dans toutes les sources de données.</span><span class="sxs-lookup"><span data-stu-id="eddfe-106">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="eddfe-107">Ces fonctions canoniques étant indépendantes des sources de données, les types d'arguments et de retour des fonctions canoniques sont définis par rapport aux types du modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="eddfe-107">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="eddfe-108">Toutefois, il est possible que certaines sources de données ne puissent pas prendre en charge tous les types du modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="eddfe-108">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="eddfe-109">Lorsque des fonctions canoniques sont utilisées dans une requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)], la fonction appropriée est appelée au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="eddfe-109">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="eddfe-110">Le comportement en cas d'entrée null et les conditions d'erreurs sont explicitement spécifiées pour toutes les fonctions canoniques.</span><span class="sxs-lookup"><span data-stu-id="eddfe-110">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="eddfe-111">Les fournisseurs de magasins doivent respecter ce comportement, mais [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ne l'applique pas de force.</span><span class="sxs-lookup"><span data-stu-id="eddfe-111">Store providers should comply with that behavior, but [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="eddfe-112">Pour les scénarios LINQ, les requêtes [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] sur le impliquent le mappage des méthodes CLR aux méthodes de la source de données sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="eddfe-112">For LINQ scenarios, queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="eddfe-113">Les méthodes CLR sont mappées aux fonctions canoniques, ce qui garantit qu'un ensemble spécifique de méthodes sera correctement mappé, quelle que soit la source de données.</span><span class="sxs-lookup"><span data-stu-id="eddfe-113">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="eddfe-114">Espace de noms des fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="eddfe-114">Canonical Functions Namespace</span></span>  
 <span data-ttu-id="eddfe-115">L'espace de noms des fonctions canoniques est <xref:System.Data.Metadata.Edm>.</span><span class="sxs-lookup"><span data-stu-id="eddfe-115">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="eddfe-116">L'espace de noms <xref:System.Data.Metadata.Edm> est automatiquement inclus dans toutes les requêtes.</span><span class="sxs-lookup"><span data-stu-id="eddfe-116">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="eddfe-117">Toutefois, si un autre espace de noms est importé et que celui-ci contient une fonction de même nom qu'une fonction canonique (dans l'espace de noms <xref:System.Data.Metadata.Edm>), vous devez spécifier l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="eddfe-117">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eddfe-118">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="eddfe-118">In This Section</span></span>  
 [<span data-ttu-id="eddfe-119">Fonctions canoniques d’agrégation</span><span class="sxs-lookup"><span data-stu-id="eddfe-119">Aggregate Canonical Functions</span></span>](aggregate-canonical-functions.md)  
 <span data-ttu-id="eddfe-120">Décrit les fonctions canoniques d'agrégation [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eddfe-120">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="eddfe-121">Fonctions canoniques mathématiques</span><span class="sxs-lookup"><span data-stu-id="eddfe-121">Math Canonical Functions</span></span>](math-canonical-functions.md)  
 <span data-ttu-id="eddfe-122">Décrit les fonctions canoniques mathématiques [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eddfe-122">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="eddfe-123">Fonctions canoniques de chaîne</span><span class="sxs-lookup"><span data-stu-id="eddfe-123">String Canonical Functions</span></span>](string-canonical-functions.md)  
 <span data-ttu-id="eddfe-124">Décrit les fonctions canoniques de chaîne [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eddfe-124">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="eddfe-125">Fonctions canoniques de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="eddfe-125">Date and Time Canonical Functions</span></span>](date-and-time-canonical-functions.md)  
 <span data-ttu-id="eddfe-126">Décrit les fonctions canoniques de date et d'heure [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eddfe-126">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="eddfe-127">Fonctions canoniques au niveau du bit</span><span class="sxs-lookup"><span data-stu-id="eddfe-127">Bitwise Canonical Functions</span></span>](bitwise-canonical-functions.md)  
 <span data-ttu-id="eddfe-128">Décrit les fonctions canoniques au niveau du bit [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eddfe-128">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="eddfe-129">Fonctions spatiales</span><span class="sxs-lookup"><span data-stu-id="eddfe-129">Spatial Functions</span></span>](spatial-functions.md)  
 <span data-ttu-id="eddfe-130">Décrit les fonctions canoniques spatiales [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eddfe-130">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="eddfe-131">Autres fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="eddfe-131">Other Canonical Functions</span></span>](other-canonical-functions.md)  
 <span data-ttu-id="eddfe-132">Décrit les fonctions qui ne sont pas considérées comme des fonctions au niveau du bit, des fonctions de date/heure, des fonctions de chaîne, des fonctions mathématiques ni des fonctions d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="eddfe-132">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eddfe-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eddfe-133">See also</span></span>

- [<span data-ttu-id="eddfe-134">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="eddfe-134">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="eddfe-135">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="eddfe-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="eddfe-136">Mappage du modèle conceptuel canonique aux fonctions SQL Server</span><span class="sxs-lookup"><span data-stu-id="eddfe-136">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [<span data-ttu-id="eddfe-137">Fonctions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="eddfe-137">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)
