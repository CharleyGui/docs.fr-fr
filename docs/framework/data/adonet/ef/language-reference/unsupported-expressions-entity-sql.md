---
title: Expressions non prises en charge (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: 956fe117eb0c59392c3999046bc70deaed268ac6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248780"
---
# <a name="unsupported-expressions"></a><span data-ttu-id="ab0b3-102">Expressions non prises en charge</span><span class="sxs-lookup"><span data-stu-id="ab0b3-102">Unsupported expressions</span></span>

<span data-ttu-id="ab0b3-103">Cette rubrique décrit les expressions Transact-SQL qui ne sont pas [!INCLUDE[esql](../../../../../../includes/esql-md.md)]prises en charge dans.</span><span class="sxs-lookup"><span data-stu-id="ab0b3-103">This topic describes Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="ab0b3-104">Pour plus d’informations, consultez [How Entity SQL diffère de Transact-SQL](how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ab0b3-104">For more information, see [How Entity SQL Differs from Transact-SQL](how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="ab0b3-105">Prédicats quantifiés</span><span class="sxs-lookup"><span data-stu-id="ab0b3-105">Quantified predicates</span></span>

<span data-ttu-id="ab0b3-106">Transact-SQL autorise les constructions de la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="ab0b3-106">Transact-SQL allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

<span data-ttu-id="ab0b3-107">Toutefois, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge ces constructions.</span><span class="sxs-lookup"><span data-stu-id="ab0b3-107">[!INCLUDE[esql](../../../../../../includes/esql-md.md)], however, does not support such constructs.</span></span> <span data-ttu-id="ab0b3-108">Des expressions équivalentes peuvent être écrites dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], comme suit :</span><span class="sxs-lookup"><span data-stu-id="ab0b3-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="ab0b3-109">\* (opérateur)</span><span class="sxs-lookup"><span data-stu-id="ab0b3-109">\* operator</span></span>

<span data-ttu-id="ab0b3-110">Transact-SQL prend en charge l’utilisation de l’opérateur \* dans la clause SELECT pour indiquer que toutes les colonnes doivent être projetées. Cet opérateur n'est pas pris en charge dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab0b3-110">Transact-SQL supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="ab0b3-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab0b3-111">See also</span></span>

- [<span data-ttu-id="ab0b3-112">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ab0b3-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="ab0b3-113">Différences entre Entity SQL et Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab0b3-113">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)
