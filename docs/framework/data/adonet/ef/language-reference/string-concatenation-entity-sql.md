---
title: + (Concaténation de chaînes) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 9c078e193eeecd4d331c5e3c04c66dee2c4a1daa
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319315"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="44a32-102">+ (concaténation de chaînes) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="44a32-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="44a32-103">Concatène deux chaînes.</span><span class="sxs-lookup"><span data-stu-id="44a32-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44a32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44a32-104">Syntax</span></span>  
  
```sql  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="44a32-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="44a32-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="44a32-106">Toute expression valide de l'un des types de données EDM.String.</span><span class="sxs-lookup"><span data-stu-id="44a32-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="44a32-107">Les deux expressions doivent être du même type de données. Si tel n'est pas le cas, l'une doit être implicitement convertible dans le type de données de l'autre.</span><span class="sxs-lookup"><span data-stu-id="44a32-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="44a32-108">Types de résultats</span><span class="sxs-lookup"><span data-stu-id="44a32-108">Result Types</span></span>  
 <span data-ttu-id="44a32-109">Type de données qui résulte de la promotion de type implicite de deux arguments.</span><span class="sxs-lookup"><span data-stu-id="44a32-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="44a32-110">Pour plus d’informations sur la promotion de type implicite, consultez [système de type](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="44a32-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44a32-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="44a32-111">Example</span></span>  
 <span data-ttu-id="44a32-112">La requête Entity SQL ci-dessous utilise l'opérateur + pour concaténer deux chaînes.</span><span class="sxs-lookup"><span data-stu-id="44a32-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="44a32-113">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="44a32-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="44a32-114">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="44a32-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="44a32-115">Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="44a32-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="44a32-116">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="44a32-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CONCAT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="44a32-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44a32-117">See also</span></span>

- [<span data-ttu-id="44a32-118">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="44a32-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="44a32-119">Types de modèles conceptuels (CSDL)</span><span class="sxs-lookup"><span data-stu-id="44a32-119">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
