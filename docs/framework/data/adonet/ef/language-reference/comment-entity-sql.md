---
title: -- (Commentaire) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 9ad6e38726d0802c3bc2090a4e6f11f008828ee5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197896"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="eb6ac-102">-- (Commentaire) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="eb6ac-102">-- (Comment) (Entity SQL)</span></span>

<span data-ttu-id="eb6ac-103">Les requêtes[!INCLUDE[esql](../../../../../../includes/esql-md.md)] peuvent contenir des commentaires.</span><span class="sxs-lookup"><span data-stu-id="eb6ac-103">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries can contain comments.</span></span> <span data-ttu-id="eb6ac-104">Deux tirets (`--`) marquent le début d'une ligne de commentaire.</span><span class="sxs-lookup"><span data-stu-id="eb6ac-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb6ac-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb6ac-105">Syntax</span></span>  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="eb6ac-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="eb6ac-106">Arguments</span></span>  

 `text_of_comment`  
 <span data-ttu-id="eb6ac-107">Chaîne de caractères contenant le texte du commentaire.</span><span class="sxs-lookup"><span data-stu-id="eb6ac-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb6ac-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="eb6ac-108">Example</span></span>  

 <span data-ttu-id="eb6ac-109">La requête Entity SQL ci-dessous montre comment utiliser les commentaires.</span><span class="sxs-lookup"><span data-stu-id="eb6ac-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="eb6ac-110">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="eb6ac-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="eb6ac-111">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="eb6ac-111">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="eb6ac-112">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="eb6ac-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="eb6ac-113">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="eb6ac-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="eb6ac-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb6ac-114">See also</span></span>

- [<span data-ttu-id="eb6ac-115">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="eb6ac-115">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="eb6ac-116">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="eb6ac-116">Entity SQL Reference</span></span>](entity-sql-reference.md)
