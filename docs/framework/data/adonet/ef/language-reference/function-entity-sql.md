---
title: FUNCTION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: ae8da3985f11a2e9f52852876a21f50a412e3b27
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250937"
---
# <a name="function-entity-sql"></a><span data-ttu-id="325c0-102">FUNCTION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="325c0-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="325c0-103">Définit une fonction dans la portée d'une commande de requête Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="325c0-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="325c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="325c0-104">Syntax</span></span>  
  
```  
FUNCTION function-name  
( [ { parameter_name <type_definition>   
        [ ,...n ]  
  ]  
) AS ( function_expression )   
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )   
                | REF ( data_type )   
                | ROW ( row_expression )   
        }   
```  
  
## <a name="arguments"></a><span data-ttu-id="325c0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="325c0-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="325c0-106">Nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="325c0-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="325c0-107">Nom d'un paramètre dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="325c0-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="325c0-108">Expression Entity SQL valide qui correspond à la fonction.</span><span class="sxs-lookup"><span data-stu-id="325c0-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="325c0-109">La commande dans la fonction peut agir sur les paramètres `parameter_name` transmis à la fonction.</span><span class="sxs-lookup"><span data-stu-id="325c0-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="325c0-110">Nom d'un type pris en charge.</span><span class="sxs-lookup"><span data-stu-id="325c0-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="325c0-111">COLLECTION (< type_definition`>` )</span><span class="sxs-lookup"><span data-stu-id="325c0-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="325c0-112">Expression qui retourne une collection de types, lignes ou références pris en charge.</span><span class="sxs-lookup"><span data-stu-id="325c0-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="325c0-113">REF **(** `data_type` **)**</span><span class="sxs-lookup"><span data-stu-id="325c0-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="325c0-114">Expression qui retourne une référence à un type d'entité.</span><span class="sxs-lookup"><span data-stu-id="325c0-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="325c0-115">ROW **(** `row_expression` **)**</span><span class="sxs-lookup"><span data-stu-id="325c0-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="325c0-116">Expression qui retourne des enregistrements anonymes, structurellement typés à partir d'une ou plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="325c0-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="325c0-117">Pour plus d'informations, consultez [ROW](row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="325c0-117">For more information, see [ROW](row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="325c0-118">Notes</span><span class="sxs-lookup"><span data-stu-id="325c0-118">Remarks</span></span>  
 <span data-ttu-id="325c0-119">Plusieurs fonctions du même nom peuvent être déclarées inline, à condition que les signatures des fonctions soient différentes.</span><span class="sxs-lookup"><span data-stu-id="325c0-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="325c0-120">Pour plus d'informations, consultez [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="325c0-120">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="325c0-121">Une fonction incluse peut être appelée dans une commande Entity SQL après seulement qu'elle a été définie dans cette commande.</span><span class="sxs-lookup"><span data-stu-id="325c0-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="325c0-122">Toutefois, une fonction incluse peut être appelée au sein d'une autre fonction incluse avant ou après la définition de la fonction appelée.</span><span class="sxs-lookup"><span data-stu-id="325c0-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="325c0-123">Dans l'exemple suivant, la fonction  A appelle la fonction B avant que la fonction  B soit définie :</span><span class="sxs-lookup"><span data-stu-id="325c0-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="325c0-124">Pour plus d’informations, consultez [Guide pratique pour Appeler une fonction](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="325c0-124">For more information, see [How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span></span>  
  
 <span data-ttu-id="325c0-125">Les fonctions peuvent également être déclarées dans le modèle lui-même.</span><span class="sxs-lookup"><span data-stu-id="325c0-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="325c0-126">Les fonctions déclarées dans le modèle sont exécutées de la même façon que les fonctions déclarées inline dans la commande.</span><span class="sxs-lookup"><span data-stu-id="325c0-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="325c0-127">Pour plus d’informations, consultez [fonctions définies par l’utilisateur](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="325c0-127">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="325c0-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="325c0-128">Example</span></span>  
 <span data-ttu-id="325c0-129">La commande Entity SQL suivante définit une fonction `Products` qui accepte une valeur entière pour filtrer les produits retournés.</span><span class="sxs-lookup"><span data-stu-id="325c0-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a><span data-ttu-id="325c0-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="325c0-130">Example</span></span>  
 <span data-ttu-id="325c0-131">La commande Entity SQL suivante définit une fonction `StringReturnsCollection` qui accepte une collection de chaînes pour filtrer les contacts retournés.</span><span class="sxs-lookup"><span data-stu-id="325c0-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="325c0-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="325c0-132">See also</span></span>

- [<span data-ttu-id="325c0-133">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="325c0-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="325c0-134">Langage Entity SQL</span><span class="sxs-lookup"><span data-stu-id="325c0-134">Entity SQL Language</span></span>](entity-sql-language.md)
