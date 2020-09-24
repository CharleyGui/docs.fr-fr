---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: c4c2d6020e5355930dfa8880b0966dfe015baa51
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161839"
---
# <a name="like-entity-sql"></a>LIKE (Entity SQL)

Détermine si une `String` de caractères donnée correspond à un modèle spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Arguments  

 `match`  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Expression qui prend la valeur `String` .  
  
 `pattern`  
 Modèle devant correspondre à la valeur `String` spécifiée.  
  
 `escape`  
 Caractère d'échappement.  
  
 NOT  
 Indique que la valeur du résultat de l'opérateur LIKE est inversée.  
  
## <a name="return-value"></a>Valeur renvoyée  

 `true` si la `string` correspond au modèle ; sinon, `false`.  
  
## <a name="remarks"></a>Notes  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] les expressions qui utilisent l’opérateur LIKE sont évaluées à peu près de la même façon que les expressions qui utilisent l’égalité comme critères de filtre. Toutefois, les [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressions qui utilisent l’opérateur Like peuvent inclure à la fois des littéraux et des caractères génériques.  
  
 Le tableau ci-dessous décrit la syntaxe de la chaîne (`string`) de modèle.  
  
|Caractère générique|Description|Exemple|  
|------------------------|-----------------|-------------|  
|%|Toute chaîne (`string`) de zéro, un ou plusieurs caractères.|`title like '%computer%'` recherche tous les titres avec le mot `"computer"` n’importe où dans le titre.|  
|_ (souligné)|N'importe quel caractère.|`firstname like '_ean'` recherche tous les prénoms de quatre lettres qui se terminent par `"ean` , par exemple Dean ou Jean.|  
|[ ]|Tout caractère unique se trouvant dans la plage ([a-f]) ou l'ensemble spécifié ([abcdef]).|`lastname like '[C-P]arsen'` recherche les derniers noms se terminant par « faiblen » et commençant par n’importe quel caractère unique entre C et P, par exemple Carsen ou Larsen.|  
|[^]|Tout caractère unique ne se trouvant pas dans la plage ([^a-f]) ou l'ensemble spécifié ([^abcdef]).|`lastname like 'de[^l]%'` recherche tous les noms qui commencent par « de » et n’inclut pas « l » comme lettre suivante.|  
  
> [!NOTE]
> L'opérateur [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE et la clause ESCAPE ne peuvent pas être appliqués aux valeurs de `System.DateTime` ou `System.Guid`.  
  
 Le mot clé LIKE prend en charge la recherche générique ASCII ainsi que la recherche générique Unicode. Lorsque tous les paramètres sont des caractères ASCII, une recherche générique ASCII est effectuée. Si un ou plusieurs arguments sont de type Unicode, tous les arguments sont convertis en Unicode et une recherche générique Unicode est effectuée. Lors de l'utilisation de données Unicode avec LIKE, les espaces de droite sont significatifs ; pour les autres données, cependant, ils ne le sont pas. La syntaxe de la chaîne de modèle [!INCLUDE[esql](../../../../../../includes/esql-md.md)] est identique à celle de Transact-SQL.  
  
 Une chaîne peut comprendre des caractères normaux ainsi que des caractères génériques. Au cours de l'analyse, les caractères normaux doivent correspondre exactement aux caractères spécifiés dans la `string` de caractères. Toutefois, les caractères génériques peuvent être associés à des portions aléatoires de la chaîne de caractères. Lorsqu'il est utilisé avec des caractères génériques, l'opérateur LIKE est plus souple que les opérateurs de comparaison de chaînes « = » et « != ».  
  
> [!NOTE]
> Vous pouvez utiliser des extensions spécifiques au fournisseur si vous ciblez un fournisseur spécifique. Toutefois, de telles constructions peuvent être traitées différemment par d'autres fournisseurs, par exemple. SqlServer prend en charge les modèles [first-last] et [^first-last]. Le premier modèle correspond exactement à un caractère compris entre les premier et dernier caractères, tandis que le second modèle correspond exactement à un caractère non compris entre les premier et dernier caractères.  
  
### <a name="escape"></a>Caractère d'échappement  

 En utilisant la clause ESCAPE, vous pouvez rechercher des chaînes de caractères qui contiennent un ou plusieurs des caractères génériques spéciaux décrits dans le tableau de la section précédente. Par exemple, supposons que plusieurs documents contiennent le littéral « 100 % » dans le titre et que vous souhaitez rechercher tous ces documents. Car le pourcentage (%) le caractère est un caractère générique, vous devez le placer dans une séquence d’échappement à l’aide de la [!INCLUDE[esql](../../../../../../includes/esql-md.md)] clause Escape pour exécuter la recherche avec succès. Voici un exemple de ce filtre :  
  
```sql  
"title like '%100!%%' escape '!'"  
```  
  
 Dans cette expression de recherche, le caractère générique de pourcentage (%) qui suit immédiatement le point d'exclamation (!) est traité comme un littéral et non comme un caractère générique. Vous pouvez utiliser n’importe quel caractère comme caractère d’échappement, à l’exception des [!INCLUDE[esql](../../../../../../includes/esql-md.md)] caractères génériques et des crochets ( `[ ]` ). Dans l'exemple précédent, le point d'exclamation (!) fait office de caractère d'échappement.  
  
## <a name="example"></a>Exemple  

 Les deux [!INCLUDE[esql](../../../../../../includes/esql-md.md)] requêtes suivantes utilisent les opérateurs like et Escape pour déterminer si une chaîne de caractères spécifique correspond à un modèle spécifié. La première requête recherche le `Name` qui commence par les caractères `Down_` . Cette requête utilise l'option ESCAPE car le caractère de soulignement (`_`) est un caractère générique. Sans l'option ESCAPE, la requête rechercherait toutes les valeurs `Name` commençant par le mot `Down` suivi de tout caractère unique autre que le caractère de soulignement. Les requêtes sont basées sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#LIKE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#like)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
