---
title: . (Accès aux membres) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 82cd2f17b2b5ea484a8202b50619047b428fe94a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192150"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="3cf2d-103">.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-103">.</span></span> <span data-ttu-id="3cf2d-104">(Accès aux membres) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3cf2d-104">(Member Access) (Entity SQL)</span></span>

<span data-ttu-id="3cf2d-105">L’opérateur point (.) est l' [!INCLUDE[esql](../../../../../../includes/esql-md.md)] opérateur d’accès aux membres.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="3cf2d-106">L'opérateur d'accès aux membres permet de produire la valeur d'une propriété ou d'un champ d'une instance de type de modèle conceptuel structurel.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cf2d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cf2d-107">Syntax</span></span>  
  
```sql  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="3cf2d-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="3cf2d-108">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="3cf2d-109">Instance d'un type de modèle conceptuel structurel.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="3cf2d-110">Propriété ou champ appartenant à une instance d'objet.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cf2d-111">Notes</span><span class="sxs-lookup"><span data-stu-id="3cf2d-111">Remarks</span></span>  

 <span data-ttu-id="3cf2d-112">L'opérateur point (.) peut être utilisé pour extraire les champs d'un enregistrement, de la même manière que l'on extrait les propriétés d'un type complexe ou d'un type d'entité.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="3cf2d-113">Par exemple, si n de type Nom est membre du type Personne et que p est une instance du type Personne, alors p.n est une expression d'accès aux membres valide qui produit une valeur de type Nom.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="3cf2d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cf2d-114">See also</span></span>

- [<span data-ttu-id="3cf2d-115">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3cf2d-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
