---
title: :::no-loc(Join):::Opérations (C#)
description: Une jointure de deux sources de données associe des objets à des objets qui partagent un attribut dans des sources de données. En savoir plus sur les méthodes de jointure dans l’infrastructure LINQ en C#.
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- ':::no-loc(Join):::'
- ':::no-loc(GroupJoin):::'
ms.openlocfilehash: 1b453f1752edf0cc126f8e27dbdd9e91ad9143f3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165692"
---
# <a name="no-locjoin-operations-c"></a>:::no-loc(Join):::Opérations (C#)

Une *jointure* de deux sources de données est l’association des objets d’une source de données aux objets qui partagent un attribut commun dans une autre source de données.  
  
 :::no-loc(Join):::ING est une opération importante dans les requêtes qui ciblent des sources de données dont les relations ne peuvent pas être suivies directement. En programmation orientée objet, cela peut correspondre à une corrélation entre objets qui n'est pas modélisée, par exemple la direction vers l'arrière dans une relation à sens unique. Voici un exemple de relation à sens unique : une classe Customer a une propriété de type City, alors que la classe City n'a aucune propriété correspondant à une collection d'objets Customer. Si vous avez une liste d'objets City et si vous souhaitez rechercher tous les clients de chaque ville, vous pouvez recourir à une opération de jointure.  
  
 Les méthodes de jointure fournies dans le framework LINQ sont <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> et <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A>. Ces méthodes effectuent des équijointures, qui sont des jointures associant deux sources de données en fonction de l’égalité de leurs clés. (Pour comparaison, Transact-SQL prend en charge les opérateurs de jointure autres que « Equals », par exemple l’opérateur « inférieur à ».) En termes de base de données relationnelle, <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> implémente une jointure interne, un type de jointure dans lequel seuls les objets qui ont une correspondance dans l’autre jeu de données sont retournés. La méthode <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> n’a aucun équivalent direct dans le contexte des bases de données relationnelles, mais elle implémente un sur-ensemble de jointures internes et de jointures externes gauches. Une jointure externe gauche est une jointure qui retourne chaque élément de la source de données (gauche), même si elle n’a pas d’éléments corrélés dans l’autre source de données.  
  
 L'illustration suivante présente une vue conceptuelle de deux ensembles, ainsi que leurs éléments inclus dans une jointure interne ou une jointure externe gauche.  
  
 ![Deux cercles se chevauchant montrant l’interne&#47;externe.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d'expression de requête C#|Informations complémentaires|  
|-----------------|-----------------|---------------------------------|----------------------|  
|:::no-loc(Join):::|:::no-loc(Join):::s deux séquences basées sur des fonctions de sélection de clé et extrait des paires de valeurs.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.:::no-loc(Join):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(Join):::%2A?displayProperty=nameWithType>|  
|:::no-loc(GroupJoin):::|:::no-loc(Join):::deux séquences basées sur des fonctions de sélection de clé et regroupent les correspondances résultantes pour chaque élément.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Exemples de syntaxe d’expression de requête
  
### :::no-loc(Join):::  
  
L’exemple suivant utilise la `join … in … on … equals …` clause pour joindre deux séquences en fonction d’une valeur spécifique :
  
[!code-csharp[:::no-loc(Join):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(Join):::)]  

### :::no-loc(GroupJoin):::  

L’exemple suivant utilise la `join … in … on … equals … into …` clause pour joindre deux séquences en fonction d’une valeur spécifique et regroupe les correspondances résultantes pour chaque élément :
  
[!code-csharp[:::no-loc(GroupJoin):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(GroupJoin):::)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq>
- [Vue d’ensemble des opérateurs de requête standard (C#)](./standard-query-operators-overview.md)
- [Types anonymes](../../classes-and-structs/anonymous-types.md)
- [Formulation :::no-loc(Join)::: des requêtes s et Cross-Product](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [join, clause](../../../language-reference/keywords/join-clause.md)
- [:::no-loc(Join):::à l’aide de clés composites](../../../linq/join-by-using-composite-keys.md)
- [Comment joindre du contenu issu de fichiers différents (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md)
- [Classer les résultats d’une clause join](../../../linq/order-the-results-of-a-join-clause.md)
- [Effectuer des opérations de jointure personnalisées](../../../linq/perform-custom-join-operations.md)
- [Effectuer des jointures groupées](../../../linq/perform-grouped-joins.md)
- [Effectuer des jointures internes](../../../linq/perform-inner-joins.md)
- [Effectuer des jointures externes gauches](../../../linq/perform-left-outer-joins.md)
- [Comment remplir des collections d’objets à partir de plusieurs sources (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
