---
title: Génération SQL
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 9c5301d3f4d5bc2e0db4a138c6d8ceb06d3a7845
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854355"
---
# <a name="sql-generation"></a><span data-ttu-id="5ae35-102">Génération SQL</span><span class="sxs-lookup"><span data-stu-id="5ae35-102">SQL Generation</span></span>
<span data-ttu-id="5ae35-103">Lorsque vous écrivez un fournisseur pour le Entity Framework, vous devez traduire Entity Framework arborescences de commandes en SQL qu’une base de données spécifique peut comprendre, comme Transact-SQL pour SQL Server ou PL/SQL pour Oracle.</span><span class="sxs-lookup"><span data-stu-id="5ae35-103">When you write a provider for the Entity Framework, you must translate Entity Framework command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="5ae35-104">Dans cette section, vous allez apprendre à développer un composant de génération SQL (pour les requêtes SELECT) pour un fournisseur Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="5ae35-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an Entity Framework provider.</span></span> <span data-ttu-id="5ae35-105">Pour plus d’informations sur les requêtes d’insertion, de mise à jour et de suppression, consultez Modification de la [génération SQL](modification-sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="5ae35-105">For information about insert, update, and delete queries, see [Modification SQL Generation](modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="5ae35-106">Pour comprendre cette section, vous devez connaître les Entity Framework et le modèle de fournisseur ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="5ae35-106">To understand this section, you should be familiar with the Entity Framework and the ADO.NET Provider Model.</span></span> <span data-ttu-id="5ae35-107">Vous devez également comprendre les arborescences de commandes et les <xref:System.Data.Common.CommandTrees.DbExpression>.</span><span class="sxs-lookup"><span data-stu-id="5ae35-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="5ae35-108">Rôle du module de génération SQL</span><span class="sxs-lookup"><span data-stu-id="5ae35-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="5ae35-109">Le module de génération SQL d’un fournisseur de Entity Framework traduit une arborescence de commandes de requête donnée en une instruction SQL SELECT unique qui cible une base de données conforme SQL : 1999.</span><span class="sxs-lookup"><span data-stu-id="5ae35-109">The SQL generation module of an Entity Framework provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="5ae35-110">Le SQL généré doit avoir aussi peu de requêtes imbriquées que possible.</span><span class="sxs-lookup"><span data-stu-id="5ae35-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="5ae35-111">Le module de génération SQL ne doit pas simplifier l’arborescence de commandes de requête de sortie.</span><span class="sxs-lookup"><span data-stu-id="5ae35-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="5ae35-112">La Entity Framework effectue cette opération, par exemple en éliminant les jointures et en réduisant les nœuds de filtre consécutifs.</span><span class="sxs-lookup"><span data-stu-id="5ae35-112">The Entity Framework will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="5ae35-113">La classe <xref:System.Data.Common.DbProviderServices> est le point de départ permettant d’accéder à la couche de génération SQL pour convertir des arborescences de commandes en <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="5ae35-113">The <xref:System.Data.Common.DbProviderServices> class is the starting point for accessing the SQL generation layer to convert command trees into <xref:System.Data.Common.DbCommand>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ae35-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5ae35-114">In This Section</span></span>  
 [<span data-ttu-id="5ae35-115">Forme des arborescences de commandes</span><span class="sxs-lookup"><span data-stu-id="5ae35-115">The Shape of the Command Trees</span></span>](the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="5ae35-116">Génération SQL à partir d’arborescences de commandes - Bonnes pratiques</span><span class="sxs-lookup"><span data-stu-id="5ae35-116">Generating SQL from Command Trees - Best Practices</span></span>](generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="5ae35-117">Génération SQL dans l’exemple de fournisseur</span><span class="sxs-lookup"><span data-stu-id="5ae35-117">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="5ae35-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ae35-118">See also</span></span>

- [<span data-ttu-id="5ae35-119">Écriture d’un fournisseur de données Entity Framework</span><span class="sxs-lookup"><span data-stu-id="5ae35-119">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
