---
title: Expressions non prises en charge (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: af0e00f470584883b6a65b63f2650c1c359b404c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489858"
---
# <a name="unsupported-expressions"></a><span data-ttu-id="34e91-102">Expressions non prises en charge</span><span class="sxs-lookup"><span data-stu-id="34e91-102">Unsupported expressions</span></span>

<span data-ttu-id="34e91-103">Cette rubrique décrit les expressions de Transact-SQL qui ne sont pas pris en charge dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34e91-103">This topic describes Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="34e91-104">Pour plus d’informations, consultez [différences Entity SQL et à partir de Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="34e91-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="34e91-105">Prédicats quantifiés</span><span class="sxs-lookup"><span data-stu-id="34e91-105">Quantified predicates</span></span>

<span data-ttu-id="34e91-106">Transact-SQL autorise les constructions de la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="34e91-106">Transact-SQL allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

<span data-ttu-id="34e91-107">Toutefois, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge ces constructions.</span><span class="sxs-lookup"><span data-stu-id="34e91-107">[!INCLUDE[esql](../../../../../../includes/esql-md.md)], however, does not support such constructs.</span></span> <span data-ttu-id="34e91-108">Des expressions équivalentes peuvent être écrites dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], comme suit :</span><span class="sxs-lookup"><span data-stu-id="34e91-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="34e91-109">\* (opérateur)</span><span class="sxs-lookup"><span data-stu-id="34e91-109">\* operator</span></span>

<span data-ttu-id="34e91-110">Transact-SQL prend en charge l’utilisation de la \* opérateur dans la clause SELECT pour indiquer que toutes les colonnes doivent être projetées. Cet opérateur n'est pas pris en charge dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34e91-110">Transact-SQL supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="34e91-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34e91-111">See also</span></span>

- [<span data-ttu-id="34e91-112">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="34e91-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="34e91-113">Différences entre Entity SQL et Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="34e91-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
