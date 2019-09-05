---
title: COLLECTION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 0e611add4ce3f20e42bb01b0bf0392bbe81ec548
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251196"
---
# <a name="collection-entity-sql"></a>COLLECTION (Entity SQL)
Le mot clé COLLECTION est utilisé uniquement dans la définition d'une fonction incluse. Les fonctions de collection sont des fonctions qui fonctionnent sur une collection de valeurs et produisent une sortie scalaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a>Arguments  
 `type_definition`  
 Expression qui retourne une collection de types, lignes ou références pris en charge.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur le mot clé COLLECTION, consultez [Type Definitions](type-definitions-entity-sql.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser le mot clé COLLECTION pour déclarer une collection de décimales en tant qu'argument pour une fonction de requête incluse.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
