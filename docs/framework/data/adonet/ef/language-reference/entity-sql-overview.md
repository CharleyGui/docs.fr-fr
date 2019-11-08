---
title: Vue d'ensemble d'Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: e0f154ab2d9db1a1fdbaba8c72bc7e43ad71ee0b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738486"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="996d2-102">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="996d2-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="996d2-103">est un langage de type SQL qui vous permet d’interroger des modèles conceptuels dans le Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="996d2-103">is a SQL-like language that enables you to query conceptual models in the Entity Framework.</span></span> <span data-ttu-id="996d2-104">Les modèles conceptuels représentent des données sous la forme d’entités et de relations, et [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vous permet d’interroger ces entités et relations dans un format familier à ceux qui ont utilisé SQL.</span><span class="sxs-lookup"><span data-stu-id="996d2-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  
      
 <span data-ttu-id="996d2-105">Le Entity Framework fonctionne avec les fournisseurs de données spécifiques au stockage pour traduire des [!INCLUDE[esql](../../../../../../includes/esql-md.md)] génériques en requêtes spécifiques au stockage.</span><span class="sxs-lookup"><span data-stu-id="996d2-105">The Entity Framework works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="996d2-106">Le fournisseur EntityClient fournit une méthode pour exécuter une commande [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sur un modèle d'entité et retourner des types de données enrichis, y compris des résultats scalaires, des jeux de résultats et des graphiques d'objets.</span><span class="sxs-lookup"><span data-stu-id="996d2-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="996d2-107">Lorsque vous construisez des objets <xref:System.Data.EntityClient.EntityCommand>, vous pouvez spécifier un nom de procédure stockée ou le texte d'une requête en assignant une chaîne de requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] à sa propriété <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="996d2-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="996d2-108"><xref:System.Data.EntityClient.EntityDataReader> expose les résultats de l'exécution d'un <xref:System.Data.EntityClient.EntityCommand> sur un modèle EDM.</span><span class="sxs-lookup"><span data-stu-id="996d2-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="996d2-109">Pour exécuter la commande qui retourne l'objet <xref:System.Data.EntityClient.EntityDataReader>, appelez la méthode <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="996d2-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="996d2-110">Outre le fournisseur EntityClient, le Entity Framework vous permet d’utiliser des [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pour exécuter des requêtes sur un modèle conceptuel et retourner des données sous forme d’objets CLR fortement typés qui sont des instances de types d’entité.</span><span class="sxs-lookup"><span data-stu-id="996d2-110">In addition to the EntityClient provider, the Entity Framework enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="996d2-111">Pour plus d’informations, consultez [utilisation des objets](../working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="996d2-111">For more information, see [Working with Objects](../working-with-objects.md).</span></span>  
  
 <span data-ttu-id="996d2-112">Cette section fournit des informations conceptuelles sur [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="996d2-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="996d2-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="996d2-113">In This Section</span></span>  
 [<span data-ttu-id="996d2-114">Différences entre Entity SQL et Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="996d2-114">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="996d2-115">Aide-mémoire Entity SQL</span><span class="sxs-lookup"><span data-stu-id="996d2-115">Entity SQL Quick Reference</span></span>](entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="996d2-116">Système de type</span><span class="sxs-lookup"><span data-stu-id="996d2-116">Type System</span></span>](type-system-entity-sql.md)  
  
 [<span data-ttu-id="996d2-117">Définitions de type</span><span class="sxs-lookup"><span data-stu-id="996d2-117">Type Definitions</span></span>](type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="996d2-118">Construction de types</span><span class="sxs-lookup"><span data-stu-id="996d2-118">Constructing Types</span></span>](constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="996d2-119">Mise en cache d’un plan de requête</span><span class="sxs-lookup"><span data-stu-id="996d2-119">Query Plan Caching</span></span>](query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="996d2-120">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="996d2-120">Namespaces</span></span>](namespaces-entity-sql.md)  
  
 [<span data-ttu-id="996d2-121">Identificateurs</span><span class="sxs-lookup"><span data-stu-id="996d2-121">Identifiers</span></span>](identifiers-entity-sql.md)  
  
 [<span data-ttu-id="996d2-122">Paramètres</span><span class="sxs-lookup"><span data-stu-id="996d2-122">Parameters</span></span>](parameters-entity-sql.md)  
  
 [<span data-ttu-id="996d2-123">Variables</span><span class="sxs-lookup"><span data-stu-id="996d2-123">Variables</span></span>](variables-entity-sql.md)  
  
 [<span data-ttu-id="996d2-124">Expressions non prises en charge</span><span class="sxs-lookup"><span data-stu-id="996d2-124">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="996d2-125">Littéraux</span><span class="sxs-lookup"><span data-stu-id="996d2-125">Literals</span></span>](literals-entity-sql.md)  
  
 [<span data-ttu-id="996d2-126">Littéraux null et inférence de type</span><span class="sxs-lookup"><span data-stu-id="996d2-126">Null Literals and Type Inference</span></span>](null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="996d2-127">Jeu de caractères en entrée</span><span class="sxs-lookup"><span data-stu-id="996d2-127">Input Character Set</span></span>](input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="996d2-128">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="996d2-128">Query Expressions</span></span>](query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="996d2-129">Fonctions</span><span class="sxs-lookup"><span data-stu-id="996d2-129">Functions</span></span>](functions-entity-sql.md)  
  
 [<span data-ttu-id="996d2-130">Priorité des opérateurs</span><span class="sxs-lookup"><span data-stu-id="996d2-130">Operator Precedence</span></span>](operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="996d2-131">Pagination</span><span class="sxs-lookup"><span data-stu-id="996d2-131">Paging</span></span>](paging-entity-sql.md)  
  
 [<span data-ttu-id="996d2-132">Sémantique de comparaison</span><span class="sxs-lookup"><span data-stu-id="996d2-132">Comparison Semantics</span></span>](comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="996d2-133">Composition de requêtes Entity SQL imbriquées</span><span class="sxs-lookup"><span data-stu-id="996d2-133">Composing Nested Entity SQL Queries</span></span>](composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="996d2-134">Types structurés autorisant la valeur null</span><span class="sxs-lookup"><span data-stu-id="996d2-134">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="996d2-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="996d2-135">See also</span></span>

- [<span data-ttu-id="996d2-136">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="996d2-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="996d2-137">Langage Entity SQL</span><span class="sxs-lookup"><span data-stu-id="996d2-137">Entity SQL Language</span></span>](entity-sql-language.md)
- [<span data-ttu-id="996d2-138">Spécifications CSDL, SSDL et MSL</span><span class="sxs-lookup"><span data-stu-id="996d2-138">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
