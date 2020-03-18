---
title: Opérations de requête LINQ de base (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
ms.openlocfilehash: 91c038303c1ad7c2530964d3102aae49090c4c2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635936"
---
# <a name="basic-linq-query-operations-c"></a>Opérations de requête LINQ de base (C#)
Ce sujet donne une brève introduction aux expressions de requête de LINQ et à certains des types typiques d’opérations que vous effectuez dans une requête. Vous trouverez des informations plus détaillées dans les rubriques suivantes :  
  
 [Expressions de requête LINQ](../../../linq/index.md)  
  
 [Vue d’ensemble des opérateurs de requête standard (C#)](./standard-query-operators-overview.md)  
  
 [Procédure pas à pas : écriture de requêtes en C#](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> Si vous êtes déjà familiarisé avec un langage de requête tel que SQL ou XQuery, vous pouvez ignorer la plupart des informations de cette rubrique. Renseignez-vous`from` sur la « clause » de la section suivante pour en savoir plus sur l’ordre des clauses dans les expressions de requête du LINQ.  
  
## <a name="obtaining-a-data-source"></a>Obtention d’une source de données  
 Dans une requête linQ, la première étape consiste à spécifier la source de données. Dans C#, comme dans la plupart des langages de programmation, une variable doit être déclarée avant de pouvoir être utilisée. Dans une requête LINQ, `from` la clause vient en premier`customers`afin d’introduire la source de données ( ) et la *variable de gamme* (`cust`).  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 La variable de portée est similaire à la variable d’itération dans une boucle `foreach`, à la différence qu’aucune itération réelle ne se produit dans une expression de requête. Quand la requête est exécutée, la variable de portée sert de référence à chaque élément consécutif dans `customers`. Comme le compilateur déduit le type de `cust`, vous n’avez pas à le spécifier explicitement. Des variables de portée supplémentaires peuvent être introduites par une clause `let`. Pour plus d’informations, consultez [let, clause](../../../language-reference/keywords/let-clause.md).  
  
> [!NOTE]
> Pour les sources de données non génériques telles que <xref:System.Collections.ArrayList>, la variable de portée doit être explicitement typée. Pour plus d’informations, voir [Comment interroger un TableauList avec LINQ (C)](./how-to-query-an-arraylist-with-linq.md) et [à partir de la clause](../../../language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtrage  
 L'opération de requête la plus courante est probablement l'application d'un filtre sous forme d'expression booléenne. Du fait du filtre, la requête retourne uniquement les éléments pour lesquels l’expression a la valeur true. Le résultat est produit à l'aide de la clause `where`. En effet, le filtre spécifie les éléments à exclure de la séquence source. Dans l’exemple suivant, seuls les clients (`customers`) qui ont une adresse à Londres sont retournés.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 Vous pouvez utiliser les opérateurs logiques C# `AND` et `OR` habituels pour appliquer le nombre d’expressions de filtre nécessaire dans la clause `where`. Par exemple, pour retourner uniquement les clients situés à « Londres » ET (`AND`) dont le nom est « Devon », vous devez écrire le code suivant :  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Pour retourner les clients situés à Londres ou à Paris, vous devez écrire le code suivant :  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Pour plus d’informations, consultez [where, clause](../../../language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Commande  
 Il est souvent utile de trier les données retournées. La clause `orderby` permet de trier les éléments de la séquence retournée en fonction du comparateur par défaut pour le type qui est trié. Par exemple, la requête suivante peut être étendue pour trier les résultats selon la propriété `Name`. Comme `Name` est une chaîne, le comparateur par défaut effectue un tri alphabétique de A à Z.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Pour trier les résultats dans l’ordre inverse, de Z à A, utilisez la clause `orderby…descending`.  
  
 Pour plus d’informations, voir [clause d’ordre](../../../language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Regroupement  
 La clause `group` vous permet de grouper vos résultats selon une clé que vous spécifiez. Par exemple, vous pouvez spécifier un regroupement des résultats par ville (`City`) pour que tous les clients de Londres ou Paris soient dans des groupes individuels. Dans ce cas, utilisez la clé `cust.City`.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Quand vous terminez une requête avec une clause `group`, les résultats sont présentés sous la forme d’une liste de listes. Chaque élément de la liste est un objet qui a un membre `Key` et une liste d’éléments qui sont regroupés sous cette clé. Quand vous itérez une requête qui produit une séquence de groupes, vous devez utiliser une boucle `foreach` imbriquée. La boucle externe itère chaque groupe et la boucle interne itère les membres de chaque groupe.  
  
 Si vous devez faire référence aux résultats d’une opération de regroupement, utilisez le mot clé `into` pour créer un identificateur susceptible d’être interrogé ultérieurement. La requête suivante retourne uniquement les groupes qui contiennent plus de deux clients :  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Pour plus d’informations, voir [clause de groupe](../../../language-reference/keywords/group-clause.md).  
  
## <a name="joining"></a>Jonction  
 Les opérations de jointure créent des associations entre les séquences qui ne sont pas explicitement modélisées dans les sources de données. Par exemple, effectuez une jointure pour rechercher tous les clients et distributeurs qui se trouvent au même endroit. Dans LINQ, la clause fonctionne toujours contre les `join` collections d’objets au lieu des tables de base de données directement.  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 Dans LINQ, vous n’avez pas à utiliser `join` aussi souvent que vous le faites dans SQL, parce que les clés étrangères dans LINQ sont représentés dans le modèle d’objet comme propriétés qui détiennent une collection d’articles. Par exemple, un objet `Customer` contient une collection d’objets `Order`. Au lieu d’effectuer une jointure, accédez aux commandes en utilisant la notation par points :  
  
```csharp
from order in Customer.Orders...  
```  
  
 Pour plus d’informations, voir [clause d’adhésion](../../../language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Sélection (projections)  
 La clause `select` produit les résultats de la requête et spécifie la « forme » ou le type de chaque élément retourné. Par exemple, spécifiez si les résultats doivent contenir des objets `Customer` complets, un seul membre, un sous-ensemble de membres ou un type de résultat complètement différent basé sur un calcul ou une création d’objet. Quand la clause `select` produit autre chose qu’une copie de l’élément source, l’opération est appelée *projection*. L’utilisation de projections pour transformer les données est une puissante capacité d’expressions de requête LINQ. Pour plus d’informations, consultez [Transformations de données avec LINQ (C#)](./data-transformations-with-linq.md) et [select, clause](../../../language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Voir aussi

- [Expressions de requête LINQ](../../../linq/index.md)
- [Procédure pas à pas : écriture de requêtes en C#](./walkthrough-writing-queries-linq.md)
- [Mots-clés de requête (LINQ)](../../../language-reference/keywords/query-keywords.md)
- [Types anonymes](../../classes-and-structs/anonymous-types.md)
