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
# <a name="unsupported-expressions"></a>Expressions non prises en charge

Cette rubrique décrit les expressions de Transact-SQL qui ne sont pas pris en charge dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Pour plus d’informations, consultez [différences Entity SQL et à partir de Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).

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

Transact-SQL prend en charge l’utilisation de la * opérateur dans la clause SELECT pour indiquer que toutes les colonnes doivent être projetées. Cet opérateur n'est pas pris en charge dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble d’Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Différences entre Entity SQL et Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
