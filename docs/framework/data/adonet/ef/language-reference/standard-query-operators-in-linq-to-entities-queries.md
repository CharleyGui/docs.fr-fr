---
title: Opérateurs de requête standard dans les requêtes LINQ to Entities
ms.date: 08/21/2018
ms.assetid: 7fa55a9b-6219-473d-b1e5-2884a32dcdff
ms.openlocfilehash: a61296d924ab1ff32b5bee523d6f0a06dda95db3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557773"
---
# <a name="standard-query-operators-in-linq-to-entities-queries"></a>Opérateurs de requête standard dans les requêtes LINQ to Entities
Dans une requête, vous indiquez les informations que vous voulez extraire de la source de données. Une requête peut également spécifier la manière dont ces informations doivent être triées, regroupées et mises en forme avant d'être retournées. LINQ fournit un ensemble de méthodes de requête standard utilisables dans une requête. La plupart de ces méthodes fonctionnent sur des séquences. dans ce contexte, une séquence est un objet dont le type implémente l' <xref:System.Collections.Generic.IEnumerable%601> interface ou l' <xref:System.Linq.IQueryable%601> interface. Les fonctionnalités de requête des opérateurs de requête standard incluent le filtrage, la projection, l'agrégation, le tri, le regroupement, la pagination, etc. Certains des opérateurs de requête standard les plus couramment utilisés ont une syntaxe de mots clés dédiée qui leur permet d'être appelés à l'aide d'une syntaxe d'expression de requête. Une expression de requête est une façon différente et plus lisible d'exprimer une requête que son équivalent fondé sur une méthode. Les clauses d'expression de requête sont traduites en appels aux méthodes de requête lors de la compilation. Pour obtenir la liste des opérateurs de requête standard qui ont des clauses d’expression de requête équivalentes, consultez [vue d’ensemble des opérateurs de requête standard](/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).  
  
 Les opérateurs de requête standard ne sont pas tous pris en charge dans les requêtes LINQ to Entities. Pour plus d’informations, consultez [Méthodes LINQ prises en charge et non prises en charge (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md). Cette rubrique fournit des informations sur les opérateurs de requête standard qui sont spécifiques à LINQ to Entities. Pour plus d’informations sur les problèmes connus dans les requêtes LINQ to Entities, consultez [problèmes connus et considérations dans LINQ to Entities](known-issues-and-considerations-in-linq-to-entities.md).  
  
## <a name="projection-and-filtering-methods"></a>Méthodes de projection et de filtrage  
 La *projection* fait référence à la transformation des éléments d’un jeu de résultats dans un format souhaité. Par exemple, vous pouvez projeter un sous-ensemble des propriétés dont vous avez besoin de chaque objet du jeu de résultats, vous pouvez projeter une propriété et lui appliquer un calcul mathématique, ou vous pouvez projeter l'objet entier à partir du jeu de résultats. Les méthodes de projection sont `Select` et `SelectMany`.  
  
 Le *filtrage* fait référence à l’opération de restriction du jeu de résultats pour qu’il ne contienne que les éléments qui correspondent à une condition spécifiée. La méthode de filtrage est `Where`.  
  
 La plupart des surcharges des méthodes de projection et de filtrage sont prises en charge dans LINQ to Entities, à l’exception de celles qui acceptent un argument positionnel.  
  
## <a name="join-methods"></a>Méthodes de jointure  
 La jointure est une opération importante dans les requêtes qui ciblent des sources de données qui n'ont pas de relations explorables les unes avec les autres. Une jointure de deux sources de données est l'association d'objets dans une source de données avec des objets dans l'autre source de données qui partagent un attribut commun ou une propriété commune. Les méthodes de jointure sont `Join` et `GroupJoin`.  
  
 La plupart des surcharges des méthodes de jointure sont prises en charge, à l'exception de celles qui utilisent un <xref:System.Collections.Generic.IEqualityComparer%601>. Ceci est dû au fait que le comparateur ne peut pas être traduit dans la source de données.  
  
## <a name="set-methods"></a>Définir des méthodes  
 Les opérations de définition dans LINQ sont des opérations de requête qui basent leurs jeux de résultats sur la présence ou l'absence d'éléments équivalents dans une collection (ou un ensemble) identique ou distincte. Les méthodes de définition sont `All`, `Any`, `Concat`, `Contains`, `DefaultIfEmpty`, `Distinct`, `EqualAll`, `Except`, `Intersect` et `Union`.  
  
 La plupart des surcharges des méthodes Set sont prises en charge dans LINQ to Entities, bien qu’il existe des différences de comportement par rapport à LINQ to Objects. Toutefois, les méthodes Set qui utilisent un ne <xref:System.Collections.Generic.IEqualityComparer%601> sont pas prises en charge, car le comparateur ne peut pas être traduit dans la source de données.  
  
## <a name="ordering-methods"></a>Méthodes de classement  
 Le classement, ou tri, fait référence au classement des éléments d'un jeu de résultats en fonction d'un ou de plusieurs attributs. En spécifiant plus d'un critère de classement, vous pouvez rompre les liens au sein d'un groupe.  
  
 La plupart des surcharges des méthodes de classement sont prises en charge, à l'exception de celles qui utilisent un <xref:System.Collections.Generic.IComparer%601>. Ceci est dû au fait que le comparateur ne peut pas être traduit dans la source de données. Les méthodes de classement sont `OrderBy`, `OrderByDescending`, `ThenBy`, `ThenByDescending` et `Reverse`.  
  
 Étant donné que la requête est exécutée sur la source de données, le comportement de classement peut différer par rapport aux requêtes exécutées dans le CLR. Ceci est dû au fait que les options de classement, telles que le classement des cas, le classement kanji et le classement des valeurs Null, peuvent être définies dans la source de données. Selon la source de données, ces options de classement peuvent produire d'autres résultats que dans le CLR.  
  
 Si vous spécifiez le même sélecteur de clé dans plusieurs opérations de classement, un classement en double sera produit. Cela n'est pas valide et une exception sera levée.  
  
## <a name="grouping-methods"></a>Méthodes de regroupement  
 Le regroupement consiste à placer des données dans des groupes afin que les éléments de chaque groupe partagent un attribut commun. La méthode de regroupement est `GroupBy`.  
  
 La plupart des surcharges des méthodes de regroupement sont prises en charge, à l'exception de celles qui utilisent un <xref:System.Collections.Generic.IEqualityComparer%601>. Ceci est dû au fait que le comparateur ne peut pas être traduit dans la source de données.  
  
 Les méthodes de regroupement sont mappées à la source de données à l'aide d'une sous-requête distincte pour le sélecteur de clé. La sous-requête de comparaison du sélecteur de clé est exécutée en utilisant la sémantique de la source de données, en tenant compte des problèmes en rapport avec la comparaison de valeurs `null`.  
  
## <a name="aggregate-methods"></a>Méthodes d'agrégation  
 Une opération d’agrégation calcule une valeur unique à partir d’une collection de valeurs. Par exemple, le calcul de la température quotidienne moyenne à partir des valeurs de température quotidiennes d'un mois est un exemple d'opération d'agrégation. Les méthodes d'agrégation sont `Aggregate`, `Average`, `Count`, `LongCount`, `Max`, `Min` et `Sum`.  
  
 La plupart des surcharges des méthodes d'agrégation sont prises en charge. Pour le comportement vis-à-vis des valeurs NULL, les méthodes d'agrégation utilisent la sémantique de la source de données. Le comportement des méthodes d'agrégation en présence de valeurs NULL peut être différent selon la source de données principale utilisée. Le comportement des méthodes d'agrégation utilisant la sémantique de la source de données peut également être différent du comportement attendu des méthodes CLR. Par exemple, le comportement par défaut de la méthode `Sum` sur SQL Server consiste à ignorer toutes les valeurs NULL au lieu de lever une exception.  
  
 Toutes les exceptions résultant d'une agrégation, telles qu'un dépassement de capacité de la fonction `Sum`, sont levées en tant qu'exceptions de source de données ou exceptions Entity Framework au cours de la matérialisation des résultats de la requête.  
  
 Pour les méthodes qui impliquent un calcul sur une séquence, telles que `Sum` ou `Average`, le calcul réel est effectué sur le serveur. Par conséquent, des conversions de type et une perte de précision peuvent se produire sur le serveur et les résultats peuvent différer des résultats attendus en utilisant la sémantique CLR.  
  
 Le comportement par défaut des méthodes d'agrégation pour des valeurs NULL/non NULL est indiqué dans le tableau suivant :  
  
|Méthode|Pas de données|Toutes les valeurs sont NULL|Certaines valeurs sont NULL|Aucune valeur n'est NULL|  
|------------|-------------|---------------------|----------------------|--------------------|  
|`Average`|Retourne la valeur NULL.|Retourne la valeur NULL.|Retourne la moyenne des valeurs non NULL dans une séquence.|Calcule la moyenne d'une séquence de valeurs numériques.|  
|`Count`|Retourne 0|Retourne le nombre de valeurs NULL dans la séquence.|Retourne le nombre de valeurs NULL et non NULL dans la séquence.|Retourne le nombre d'éléments dans la séquence.|  
|`Max`|Retourne la valeur NULL.|Retourne la valeur NULL.|Retourne la valeur non NULL maximale dans une séquence.|Retourne la valeur maximale dans une séquence.|  
|`Min`|Retourne la valeur NULL.|Retourne la valeur NULL.|Retourne la valeur non NULL minimale dans une séquence.|Retourne la valeur minimale dans une séquence.|  
|`Sum`|Retourne la valeur NULL.|Retourne la valeur NULL.|Retourne la somme de la valeur non NULL dans une séquence.|Calcule la somme d'une séquence de valeurs numériques.|  
  
## <a name="type-methods"></a>Méthodes de type  
 Les deux méthodes LINQ qui traitent de la conversion et du test de type sont toutes deux prises en charge dans le contexte de l’Entity Framework. Cela signifie que les seuls types pris en charge sont les types qui mappent au type de Entity Framework approprié. Pour obtenir la liste de ces types, consultez [types de modèle conceptuel (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl). Les méthodes de type sont `Convert` et `OfType`.  
  
 La méthode `OfType` est prise en charge pour les types d'entités. La méthode `Convert` est prise en charge pour les types primitifs de modèle conceptuel.  Les méthodes C# `is` et `as` sont également prises en charge.  
  
## <a name="paging-methods"></a>Méthodes de pagination  
 Les opérations de pagination retournent un seul élément ou plusieurs éléments d’une séquence. Les méthodes de pagination prises en charge sont `First` ,,,, `FirstOrDefault` `Single` `SingleOrDefault` `Skip` et `Take` .  
  
 Un certain nombre de méthodes de pagination ne sont pas prises en charge, en raison soit de l’incapacité à mapper des fonctions à la source de données, soit à l’absence de classement implicite des jeux sur la source de données. Les méthodes qui retournent une valeur par défaut sont limitées aux types primitifs de modèle conceptuel et aux types référence avec des valeurs par défaut NULL. Les méthodes de pagination qui sont exécutées sur une séquence vide retourneront la valeur NULL.  
  
## <a name="see-also"></a>Voir aussi

- [Méthodes LINQ prises en charge et non prises en charge (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md)
- [Vue d'ensemble des opérateurs de requête standard](/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120))
