---
title: Appel de fonctions dans les requêtes LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 267bb393d9e75c66eb18139e8897da34bd86e159
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251262"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="12c83-102">Appel de fonctions dans les requêtes LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="12c83-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="12c83-103">Les rubriques de cette section expliquent comment appeler des fonctions dans les requêtes LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="12c83-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="12c83-104">Les classes <xref:System.Data.Objects.EntityFunctions> et <xref:System.Data.Objects.SqlClient.SqlFunctions> donnent accès à des fonctions canoniques et de base de données dans le cadre d'Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="12c83-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="12c83-105">Pour plus d'informations, voir [Procédure : Appeler des fonctions](how-to-call-canonical-functions.md) canoniques et [Comment : Appeler des fonctions](how-to-call-database-functions.md)de base de données.</span><span class="sxs-lookup"><span data-stu-id="12c83-105">For more information, see [How to: Call Canonical Functions](how-to-call-canonical-functions.md) and [How to: Call Database Functions](how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="12c83-106">L'appel d'une fonction personnalisée passe par trois étapes de base obligatoires :</span><span class="sxs-lookup"><span data-stu-id="12c83-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1. <span data-ttu-id="12c83-107">Définissez une fonction dans votre modèle conceptuel ou déclarez-la dans votre modèle de stockage.</span><span class="sxs-lookup"><span data-stu-id="12c83-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2. <span data-ttu-id="12c83-108">Ajoutez une méthode à votre application et mappez-la à la fonction du modèle avec un objet <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="12c83-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3. <span data-ttu-id="12c83-109">Appelez la fonction dans une requête LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="12c83-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="12c83-110">Pour plus d'informations, consultez les rubriques de cette section.</span><span class="sxs-lookup"><span data-stu-id="12c83-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="12c83-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="12c83-111">In This Section</span></span>  
 [<span data-ttu-id="12c83-112">Guide pratique : Appeler des fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="12c83-112">How to: Call Canonical Functions</span></span>](how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="12c83-113">Guide pratique pour Appeler des fonctions de base de données</span><span class="sxs-lookup"><span data-stu-id="12c83-113">How to: Call Database Functions</span></span>](how-to-call-database-functions.md)  
  
 [<span data-ttu-id="12c83-114">Guide pratique pour Appeler des fonctions de base de données personnalisées</span><span class="sxs-lookup"><span data-stu-id="12c83-114">How to: Call Custom Database Functions</span></span>](how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="12c83-115">Guide pratique pour Appeler des fonctions définies par modèle dans les requêtes</span><span class="sxs-lookup"><span data-stu-id="12c83-115">How to: Call Model-Defined Functions in Queries</span></span>](how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="12c83-116">Guide pratique pour Appeler des fonctions définies par modèle comme méthodes d’objet</span><span class="sxs-lookup"><span data-stu-id="12c83-116">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="12c83-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12c83-117">See also</span></span>

- [<span data-ttu-id="12c83-118">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="12c83-118">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="12c83-119">Fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="12c83-119">Canonical Functions</span></span>](canonical-functions.md)
- <span data-ttu-id="12c83-120">[Vue d’ensemble du fichier. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12c83-120">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- <span data-ttu-id="12c83-121">[Guide pratique pour Définir des fonctions personnalisées dans le modèle conceptuel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12c83-121">[How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span></span>
