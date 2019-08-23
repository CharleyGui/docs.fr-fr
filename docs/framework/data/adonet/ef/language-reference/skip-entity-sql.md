---
title: SKIP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 6ddbdd41a00b3934649b24ca96a5a07e5cbf0d34
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911133"
---
# <a name="skip-entity-sql"></a>SKIP (Entity SQL)
Vous pouvez effectuer une pagination physique à l'aide de la sous-clause SKIP de la clause ORDER BY. La sous-clause SKIP ne peut pas être utilisée séparément de la clause ORDER BY.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Nombre d'éléments à ignorer.  
  
## <a name="remarks"></a>Notes  
 Si une sous-clause d'expression SKIP est présente dans une clause ORDER BY, les résultats sont triés en fonction de la spécification de classement et le jeu de résultats comprend plusieurs lignes immédiatement à la suite de l'expression SKIP. Par exemple, SKIP 5 ignore les cinq premières lignes et retourne la sixième ligne et les suivantes.  
  
> [!NOTE]
> Une requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] n'est pas valide si le modificateur TOP et la sous-clause SKIP figurent dans la même expression de requête. La requête doit être réécrite en remplaçant l'expression TOP par l'expression LIMIT.  
  
> [!NOTE]
> Dans SQL Server 2000, l’utilisation de SKIP avec ORDER BY sur des colonnes non-clés peut retourner des résultats incorrects. Le nombre de lignes ignorées peut être supérieur au nombre de lignes spécifié si la colonne non-clé contient des données en double. Cela est dû au fait que SKIP est traduit pour SQL Server 2000. Par exemple, dans le code suivant plus de cinq lignes pourraient être ignorées si `E.NonKeyColumn` contient des valeurs en double :  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 La [!INCLUDE[esql](../../../../../../includes/esql-md.md)] requête dans [Comment: La page à travers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) les résultats de la requête utilise l’opérateur Order By avec skip pour spécifier l’ordre de tri utilisé sur les objets retournés dans une instruction SELECT.  
  
## <a name="see-also"></a>Voir aussi

- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Guide pratique : Page des résultats de la requête](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Pagination](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
