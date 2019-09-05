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
# <a name="unsupported-expressions"></a>Expressions non prises en charge

Cette rubrique décrit les expressions Transact-SQL qui ne sont pas [!INCLUDE[esql](../../../../../../includes/esql-md.md)]prises en charge dans. Pour plus d’informations, consultez [How Entity SQL diffère de Transact-SQL](how-entity-sql-differs-from-transact-sql.md).

## <a name="quantified-predicates"></a>Prédicats quantifiés

Transact-SQL autorise les constructions de la forme suivante :

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

Toutefois, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge ces constructions. Des expressions équivalentes peuvent être écrites dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], comme suit :

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a>* (opérateur)

Transact-SQL prend en charge l’utilisation de l’opérateur * dans la clause SELECT pour indiquer que toutes les colonnes doivent être projetées. Cet opérateur n'est pas pris en charge dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble d’Entity SQL](entity-sql-overview.md)
- [Différences entre Entity SQL et Transact-SQL](how-entity-sql-differs-from-transact-sql.md)
