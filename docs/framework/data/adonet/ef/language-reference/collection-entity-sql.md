---
title: COLLECTION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 0e611add4ce3f20e42bb01b0bf0392bbe81ec548
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251196"
---
# <a name="collection-entity-sql"></a><span data-ttu-id="f6f9e-102">COLLECTION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f6f9e-102">COLLECTION (Entity SQL)</span></span>
<span data-ttu-id="f6f9e-103">Le mot clé COLLECTION est utilisé uniquement dans la définition d'une fonction incluse.</span><span class="sxs-lookup"><span data-stu-id="f6f9e-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="f6f9e-104">Les fonctions de collection sont des fonctions qui fonctionnent sur une collection de valeurs et produisent une sortie scalaire.</span><span class="sxs-lookup"><span data-stu-id="f6f9e-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6f9e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6f9e-105">Syntax</span></span>  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a><span data-ttu-id="f6f9e-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="f6f9e-106">Arguments</span></span>  
 `type_definition`  
 <span data-ttu-id="f6f9e-107">Expression qui retourne une collection de types, lignes ou références pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f6f9e-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6f9e-108">Notes</span><span class="sxs-lookup"><span data-stu-id="f6f9e-108">Remarks</span></span>  
 <span data-ttu-id="f6f9e-109">Pour plus d’informations sur le mot clé COLLECTION, consultez [Type Definitions](type-definitions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f6f9e-109">For more information about the COLLECTION keyword, see [Type Definitions](type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6f9e-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="f6f9e-110">Example</span></span>  
 <span data-ttu-id="f6f9e-111">L'exemple suivant montre comment utiliser le mot clé COLLECTION pour déclarer une collection de décimales en tant qu'argument pour une fonction de requête incluse.</span><span class="sxs-lookup"><span data-stu-id="f6f9e-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="f6f9e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6f9e-112">See also</span></span>

- [<span data-ttu-id="f6f9e-113">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f6f9e-113">Entity SQL Reference</span></span>](entity-sql-reference.md)
