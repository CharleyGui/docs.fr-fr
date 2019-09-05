---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 3b746a82f72fc7f42f9d91ddd0a7d6f4f86ac0bb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250577"
---
# <a name="isof-entity-sql"></a>ISOF (Entity SQL)
Détermine si le type d'une expression appartient au type spécifié ou à l'un de ses sous-types.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression de requête valide pour en déterminer le type.  
  
 NOT  
 Inverse le résultat EDM.Boolean de l'opérateur IS OF.  
  
 ONLY  
 Indique que l'opérateur IS OF ne retourne `true` que si `expression` appartient au type `type` et non à l'un de ses sous-types.  
  
 `type`  
 Type sur lequel tester `expression`. Le type doit être qualifié par un espace de noms.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` si `expression` est de type T, qui est soit un type de base, soit un type dérivé de `type` ; null si `expression` a la valeur null au moment de l'exécution ; sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Les expressions `expression IS NOT OF (type)` et `expression IS NOT OF (ONLY type)` sont syntaxiquement équivalentes `NOT (expression IS OF (type))` à `NOT (expression IS OF (ONLY type))`et, respectivement.  
  
 Le tableau suivant indique le comportement de l'opérateur `IS OF` sur certains modèles courants et d'autres plus singuliers. Toutes les exceptions sont levées côté client avant que le fournisseur soit appelé :  
  
|Motif|Comportement|  
|-------------|--------------|  
|null IS OF (EntityType)|Exception|  
|null IS OF (ComplexType)|Exception|  
|null IS OF (RowType)|Exception|  
|TREAT (null AS EntityType) IS OF (EntityType)|Retourne DBNull|  
|TREAT (null AS ComplexType) IS OF (ComplexType)|Exception|  
|TREAT (null AS RowType) IS OF (RowType)|Exception|  
|EntityType IS OF (EntityType)|Retourne true/false|  
|ComplexType IS OF (ComplexType)|Exception|  
|RowType IS OF (RowType)|Exception|  
  
## <a name="example"></a>Exemple  
 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l’opérateur is of pour déterminer le type d’une expression de requête, puis utilise l’opérateur Treat pour convertir un objet du type course en collection d’objets de type OnsiteCourse. Cette requête est basée sur le modèle [School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
