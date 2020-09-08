---
title: Performances des requêtes chaînées-LINQ to XML
description: En savoir plus sur les requêtes chaînées peuvent être exécutées, ainsi qu’une requête unique plus grande et plus complexe.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: c1dae1eaf008a1f17c6884ef6b8e67d042719ad9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552500"
---
# <a name="performance-of-chained-queries-linq-to-xml"></a>Performances des requêtes chaînées (LINQ to XML)

L’un des principaux avantages de LINQ (et LINQ to XML) est que les requêtes chaînées peuvent être exécutées ainsi qu’une requête unique plus grande et plus complexe que les requêtes chaînées.

Une requête chaînée est une requête qui utilise une autre requête comme source. Par exemple, dans le code simple suivant, `query2` utilise `query1` comme source :

```csharp
XElement root = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    new XElement("Child", 3),
    new XElement("Child", 4)
);

var query1 = from x in root.Elements("Child")
             where (int)x >= 3
             select x;

var query2 = from e in query1
             where (int)e % 2 == 0
             select e;

foreach (var i in query2)
    Console.WriteLine("{0}", (int)i);
```

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

Cet exemple produit la sortie suivante :

```output
4
```

Cette requête chaînée offre le même profil de performance que l'itération sur une liste liée.

- L'axe <xref:System.Xml.Linq.XContainer.Elements%2A> offre essentiellement la même performance qu'une itération sur une liste liée. <xref:System.Xml.Linq.XContainer.Elements%2A> est implémenté en tant qu'itérateur avec exécution différée. Cela signifie qu'en plus de l'itération sur la liste liée, il effectue certaines tâches comme l'allocation de l'objet itérateur et le suivi de l'état d'exécution. Ces tâches peuvent être divisées en deux catégories : les tâches effectuées lors de la configuration de l'itérateur et les tâches effectuées à chaque itération. Les tâches de configuration représentent une part réduite et fixe du travail, tandis que les tâches effectuées à chaque itération sont proportionnelles au nombre d'éléments de la collection source.
- Dans `query1` , la `where` clause ( `Where` en Visual Basic) entraîne l’appel de la méthode par la requête <xref:System.Linq.Enumerable.Where%2A> . Cette méthode est également implémentée en tant qu'itérateur. Les tâches de configuration se composent de l'instanciation du délégué qui fera référence à l'expression, en plus de la configuration normale d'un itérateur. A chaque itération, le délégué est appelé pour exécuter le prédicat. Le travail d’installation et le travail effectué lors de chaque itération sont similaires au travail effectué lors de l’itération sur l’axe.
- Dans `query1`, la clause select indique que la requête doit appeler la méthode <xref:System.Linq.Enumerable.Select%2A>. Cette méthode fournit le même profil de performance que la méthode <xref:System.Linq.Enumerable.Where%2A>.
- Dans `query2` , la `where` clause ( `Where` en Visual Basic) et la `select` clause ont le même profil de performance que dans `query1` .

L'itération sur `query2` est donc directement proportionnelle au nombre d'éléments de la source de la première requête, en d'autres termes, elle suit un algorithme linéaire.

Pour plus d’informations sur les itérateurs, consultez [yield](../../csharp/language-reference/keywords/yield.md).

Pour obtenir un didacticiel plus détaillé sur le chaînage des requêtes, consultez [Didacticiel : chaînes de requêtes (C#)](chain-queries-example.md).
