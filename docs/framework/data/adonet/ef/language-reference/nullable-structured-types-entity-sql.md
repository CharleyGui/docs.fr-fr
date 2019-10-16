---
title: Types structurés autorisant la valeur null (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: b155c672d8c0bef8b01fb26fb49908f094add25a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319488"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="6cccc-102">Types structurés autorisant la valeur null (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6cccc-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="6cccc-103">Une instance `null` d'un type structuré est une instance qui n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="6cccc-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="6cccc-104">Cela est différent d'une instance existante dans laquelle toutes les propriétés ont des valeurs `null`.</span><span class="sxs-lookup"><span data-stu-id="6cccc-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="6cccc-105">Cette rubrique décrit les types structurés Nullable, y compris quels types sont Nullable et quels modèles de code produisent des instances `null` de types Nullable structurés.</span><span class="sxs-lookup"><span data-stu-id="6cccc-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="6cccc-106">Différents types structurés Nullable</span><span class="sxs-lookup"><span data-stu-id="6cccc-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="6cccc-107">Il existe trois sortes de types de structure Nullable :</span><span class="sxs-lookup"><span data-stu-id="6cccc-107">There are three kinds of nullable structure types:</span></span>  
  
- <span data-ttu-id="6cccc-108">Types de ligne</span><span class="sxs-lookup"><span data-stu-id="6cccc-108">Row types.</span></span>  
  
- <span data-ttu-id="6cccc-109">Types complexes.</span><span class="sxs-lookup"><span data-stu-id="6cccc-109">Complex types.</span></span>  
  
- <span data-ttu-id="6cccc-110">types d'entités</span><span class="sxs-lookup"><span data-stu-id="6cccc-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="6cccc-111">Modèles de code qui produisent des instances Null de types structurés</span><span class="sxs-lookup"><span data-stu-id="6cccc-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="6cccc-112">Les scénarios suivants produisent des instances `null` :</span><span class="sxs-lookup"><span data-stu-id="6cccc-112">The following scenarios produce `null` instances:</span></span>  
  
- <span data-ttu-id="6cccc-113">Mise en forme de données `null` comme type structuré :</span><span class="sxs-lookup"><span data-stu-id="6cccc-113">Shaping `null` as a structured type:</span></span>  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- <span data-ttu-id="6cccc-114">Upcast d'un type de base vers un type dérivé :</span><span class="sxs-lookup"><span data-stu-id="6cccc-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- <span data-ttu-id="6cccc-115">Jointure externe sur condition fausse :</span><span class="sxs-lookup"><span data-stu-id="6cccc-115">Outer join on false condition:</span></span>  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="6cccc-116">-- ou</span><span class="sxs-lookup"><span data-stu-id="6cccc-116">--or</span></span>  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="6cccc-117">-- ou</span><span class="sxs-lookup"><span data-stu-id="6cccc-117">--or</span></span>  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- <span data-ttu-id="6cccc-118">Suppression d'une référence `null` :</span><span class="sxs-lookup"><span data-stu-id="6cccc-118">Dereferencing a `null` reference:</span></span>  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- <span data-ttu-id="6cccc-119">Obtention d’ANYELEMENT à partir d’une collection vide :</span><span class="sxs-lookup"><span data-stu-id="6cccc-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- <span data-ttu-id="6cccc-120">Recherche d'instances `null` de types structurés :</span><span class="sxs-lookup"><span data-stu-id="6cccc-120">Checking for `null` instances of structured types:</span></span>  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6cccc-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cccc-121">See also</span></span>

- [<span data-ttu-id="6cccc-122">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6cccc-122">Entity SQL Overview</span></span>](entity-sql-overview.md)
