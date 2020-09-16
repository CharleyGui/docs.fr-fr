---
title: Appel de fonctions dans les requêtes LINQ to Entities
description: Utilisez ces articles pour voir comment les classes EntityFunctions et SqlFunctions fournissent l’accès aux fonctions canoniques et de base de données dans le cadre de la Entity Framework.
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: eb206e9b331da1ae442c1f310e78fec5c6b57e82
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546046"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="1b742-103">Appel de fonctions dans les requêtes LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1b742-103">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="1b742-104">Les rubriques de cette section expliquent comment appeler des fonctions dans les requêtes LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="1b742-104">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="1b742-105">Les classes <xref:System.Data.Objects.EntityFunctions> et <xref:System.Data.Objects.SqlClient.SqlFunctions> donnent accès à des fonctions canoniques et de base de données dans le cadre d'Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="1b742-105">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="1b742-106">Pour plus d’informations, consultez [Comment : appeler des fonctions canoniques](how-to-call-canonical-functions.md) et [Comment : appeler des fonctions de base de données](how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="1b742-106">For more information, see [How to: Call Canonical Functions](how-to-call-canonical-functions.md) and [How to: Call Database Functions](how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="1b742-107">L'appel d'une fonction personnalisée passe par trois étapes de base obligatoires :</span><span class="sxs-lookup"><span data-stu-id="1b742-107">The process for calling a custom function requires three basic steps:</span></span>  
  
1. <span data-ttu-id="1b742-108">Définissez une fonction dans votre modèle conceptuel ou déclarez-la dans votre modèle de stockage.</span><span class="sxs-lookup"><span data-stu-id="1b742-108">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2. <span data-ttu-id="1b742-109">Ajoutez une méthode à votre application et mappez-la à la fonction du modèle avec un objet <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1b742-109">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3. <span data-ttu-id="1b742-110">Appelez la fonction dans une requête LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="1b742-110">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="1b742-111">Pour plus d'informations, consultez les rubriques de cette section.</span><span class="sxs-lookup"><span data-stu-id="1b742-111">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b742-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1b742-112">In This Section</span></span>  
 [<span data-ttu-id="1b742-113">Comment : appeler des fonctions de chaînes canoniques</span><span class="sxs-lookup"><span data-stu-id="1b742-113">How to: Call Canonical Functions</span></span>](how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="1b742-114">Comment : appeler des fonctions de base de données</span><span class="sxs-lookup"><span data-stu-id="1b742-114">How to: Call Database Functions</span></span>](how-to-call-database-functions.md)  
  
 [<span data-ttu-id="1b742-115">Comment : appeler des fonctions de base de données personnalisées</span><span class="sxs-lookup"><span data-stu-id="1b742-115">How to: Call Custom Database Functions</span></span>](how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="1b742-116">Comment : appeler des fonctions définies par modèle dans les requêtes</span><span class="sxs-lookup"><span data-stu-id="1b742-116">How to: Call Model-Defined Functions in Queries</span></span>](how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="1b742-117">Comment : appeler des fonctions définies par modèle comme méthodes d'objet</span><span class="sxs-lookup"><span data-stu-id="1b742-117">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="1b742-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b742-118">See also</span></span>

- [<span data-ttu-id="1b742-119">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1b742-119">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="1b742-120">Fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="1b742-120">Canonical Functions</span></span>](canonical-functions.md)
- <span data-ttu-id="1b742-121">[Présentation d'un fichier .edmx](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1b742-121">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- <span data-ttu-id="1b742-122">[Procédure : définir des fonctions personnalisées dans le modèle conceptuel](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1b742-122">[How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span></span>
