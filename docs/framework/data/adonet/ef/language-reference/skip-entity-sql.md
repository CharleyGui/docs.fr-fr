---
title: SKIP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 75140384823588b8f6785de00b0ab3cd17314a3f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319343"
---
# <a name="skip-entity-sql"></a>SKIP (Entity SQL)

Vous pouvez effectuer une pagination physique à l'aide de la sous-clause SKIP de la clause ORDER BY. La sous-clause SKIP ne peut pas être utilisée séparément de la clause ORDER BY.

## <a name="syntax"></a>Syntaxe

```sql
[ SKIP n ]
```

## <a name="arguments"></a>Arguments

`n` \
Nombre d'éléments à ignorer.

## <a name="remarks"></a>Notes

Si une sous-clause d'expression SKIP est présente dans une clause ORDER BY, les résultats sont triés en fonction de la spécification de classement et le jeu de résultats comprend plusieurs lignes immédiatement à la suite de l'expression SKIP. Par exemple, SKIP 5 ignore les cinq premières lignes et retourne la sixième ligne et les suivantes.

> [!NOTE]
> Une requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] n'est pas valide si le modificateur TOP et la sous-clause SKIP figurent dans la même expression de requête. La requête doit être réécrite en remplaçant l'expression TOP par l'expression LIMIT.

> [!NOTE]
> Dans SQL Server 2000, l’utilisation de SKIP avec ORDER BY sur des colonnes non-clés peut retourner des résultats incorrects. Le nombre de lignes ignorées peut être supérieur au nombre de lignes spécifié si la colonne non-clé contient des données en double. Cela est dû au fait que SKIP est traduit pour SQL Server 2000. Par exemple, dans le code suivant plus de cinq lignes pourraient être ignorées si `E.NonKeyColumn` contient des valeurs en double :
>
> ```sql
> SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L
> ```

La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dans [Comment : paginer des résultats](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) de la requête utilise l’opérateur Order By avec skip pour spécifier l’ordre de tri utilisé sur les objets retournés dans une instruction SELECT.

## <a name="see-also"></a>Voir aussi

- [ORDER BY](order-by-entity-sql.md)
- [Comment : paginer les résultats d’une requête](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Pagination](paging-entity-sql.md)
- [TOP](top-entity-sql.md)
