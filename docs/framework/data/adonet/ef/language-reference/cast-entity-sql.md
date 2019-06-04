---
title: CAST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: 743c90cd9bc77a89051c59a217befa4275b28572
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489948"
---
# <a name="cast-entity-sql"></a>CAST (Entity SQL)
Convertit une expression d'un type de données à un autre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression valide convertible en `data_type`.  
  
 `data_type`  
 Type de données cible fourni par le système. Il doit s'agir d'un type primitif (scalaire). Le type de données `data_type` utilisé dépend de l'espace de requête. Si une requête est exécutée avec la classe <xref:System.Data.EntityClient.EntityCommand>, le type de données est un type défini dans le modèle conceptuel. Pour plus d'informations, consultez [CSDL Specification](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md). Si une requête est exécutée avec la classe <xref:System.Data.Objects.ObjectQuery%601>, le type de données est un type CLR (Common Language Runtime).  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne la même valeur que `data_type`.  
  
## <a name="remarks"></a>Notes  
 L’expression de cast a une sémantique similaire à l’expression de conversion Transact-SQL. L'expression de cast sert à convertir une valeur d'un type en valeur d'un autre type.  
  
```  
CAST( e as T )  
```  
  
 Si e est de type S et que S est convertible en T, l'expression ci-dessus est une expression de cast valide. T doit correspondre à un type primitif (scalaire).  
  
 Les valeurs des facettes Precision et Scale peuvent être éventuellement fournies lors de la conversion en `Edm.Decimal`. Si elles ne sont pas explicitement fournies, les valeurs par défaut des facettes Precision et Scale sont respectivement 18 et 0. Plus spécifiquement, les surcharges suivantes sont prises en charge pour `Decimal`:  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 L'utilisation d'une expression de cast est considérée comme une conversion explicite. Les conversions explicites peuvent tronquer des données ou entraîner une perte de précision.  
  
> [!NOTE]
>  CAST n'est pris en charge que sur les types primitifs et les types de membres d'énumération.  
  
## <a name="example"></a>Exemple  
 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l'opérateur CAST pour convertir une expression d'un type de données à une autre. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite dans [Comment : Exécuter une requête qui retourne les résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
