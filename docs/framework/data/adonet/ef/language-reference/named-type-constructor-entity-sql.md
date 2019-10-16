---
title: Constructeur de type nommé (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: f40adce1a9e031ed0b7cd5d03d9c63db255aa610
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319573"
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="9caf0-102">Constructeur de type nommé (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9caf0-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="9caf0-103">Permet de créer des instances des types nominaux de modèle conceptuel, tels que les types d'entités ou complexes.</span><span class="sxs-lookup"><span data-stu-id="9caf0-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9caf0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9caf0-104">Syntax</span></span>  
  
```sql  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="9caf0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9caf0-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="9caf0-106">Valeur correspondant à un identificateur simple ou entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="9caf0-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="9caf0-107">Pour plus d’informations, consultez [identificateurs](identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="9caf0-107">For more information see, [Identifiers](identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="9caf0-108">Attributs du type supposés se trouver dans le même ordre d'apparition que dans la déclaration du type.</span><span class="sxs-lookup"><span data-stu-id="9caf0-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9caf0-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9caf0-109">Return Value</span></span>  
 <span data-ttu-id="9caf0-110">Instances de types complexes et de types d'entités nommés.</span><span class="sxs-lookup"><span data-stu-id="9caf0-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9caf0-111">Notes</span><span class="sxs-lookup"><span data-stu-id="9caf0-111">Remarks</span></span>  
 <span data-ttu-id="9caf0-112">Les exemples suivants montrent comment construire des types nominaux et des types complexes :</span><span class="sxs-lookup"><span data-stu-id="9caf0-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="9caf0-113">L'expression ci-dessous crée une instance de type `Person` :</span><span class="sxs-lookup"><span data-stu-id="9caf0-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="9caf0-114">L'expression ci-dessous crée une instance d'un type complexe :</span><span class="sxs-lookup"><span data-stu-id="9caf0-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="9caf0-115">L'expression ci-dessous crée une instance d'un type complexe imbriqué :</span><span class="sxs-lookup"><span data-stu-id="9caf0-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="9caf0-116">L'expression ci-dessous crée une instance d'une entité avec un type complexe imbriqué :</span><span class="sxs-lookup"><span data-stu-id="9caf0-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="9caf0-117">L'exemple suivant montre comment initialiser une propriété d'un type complexe en valeur null :`MyModel.ZipCode(‘98118’, null)`</span><span class="sxs-lookup"><span data-stu-id="9caf0-117">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="9caf0-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="9caf0-118">Example</span></span>  
 <span data-ttu-id="9caf0-119">La requête Entity SQL ci-dessous utilise le constructeur de type nommé pour créer une instance d'un type de modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="9caf0-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="9caf0-120">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="9caf0-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9caf0-121">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9caf0-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9caf0-122">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9caf0-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9caf0-123">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="9caf0-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NAMED_TYPE_CONSTRUCTOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="9caf0-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9caf0-124">See also</span></span>

- [<span data-ttu-id="9caf0-125">Construction de types</span><span class="sxs-lookup"><span data-stu-id="9caf0-125">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="9caf0-126">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9caf0-126">Entity SQL Reference</span></span>](entity-sql-reference.md)
