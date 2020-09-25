---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 3cbbc9b6feda1bde104ed2c95d4dca274b090028
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202277"
---
# <a name="isof-entity-sql"></a>ISOF (Entity SQL)

Détermine si le type d'une expression appartient au type spécifié ou à l'un de ses sous-types.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
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
  
## <a name="return-value"></a>Valeur renvoyée  

 `true` si `expression` est de type T, qui est soit un type de base, soit un type dérivé de `type` ; null si `expression` a la valeur null au moment de l'exécution ; sinon, `false`.  
  
## <a name="remarks"></a>Notes  

 Les expressions `expression IS NOT OF (type)` et `expression IS NOT OF (ONLY type)` sont syntaxiquement équivalentes `NOT (expression IS OF (type))` à `NOT (expression IS OF (ONLY type))` et, respectivement.  
  
 Le tableau suivant indique le comportement de l'opérateur `IS OF` sur certains modèles courants et d'autres plus singuliers. Toutes les exceptions sont levées côté client avant que le fournisseur soit appelé :  
  
|Modèle|Comportement|  
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

 La requête ci-dessous [!INCLUDE[esql](../../../../../../includes/esql-md.md)] utilise l’opérateur is of pour déterminer le type d’une expression de requête, puis utilise l’opérateur Treat pour convertir un objet du type course en collection d’objets de type OnsiteCourse. Cette requête est basée sur le modèle [School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [ ! code-SQL [DP EntityServices concepts # TREAT_ISOF] ~/Samples/snippets/TSQL/VS_Snippets_Data/DP EntityServices concepts/TSQL/EntitySql. SQL # treat_isof)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
