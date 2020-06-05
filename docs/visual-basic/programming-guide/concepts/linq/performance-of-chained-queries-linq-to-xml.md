---
title: Performances des requêtes chaînées (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 6b87f2744f663ebd45dceb036dcaac71b80765fc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396387"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a>Performances des requêtes chaînées (LINQ to XML) (Visual Basic)

L'un des principaux avantages de LINQ (et LINQ to XML) est que les requêtes chaînées peuvent offrir la même performance qu'une requête unique plus grande et plus complexe.

Une requête chaînée est une requête qui utilise une autre requête comme source. Par exemple, dans le code simple suivant, `query2` utilise `query1` comme source :

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

Cet exemple produit la sortie suivante :

```console
4
```

Cette requête chaînée offre le même profil de performance que l'itération sur une liste liée.

- L'axe <xref:System.Xml.Linq.XContainer.Elements%2A> offre essentiellement la même performance qu'une itération sur une liste liée. <xref:System.Xml.Linq.XContainer.Elements%2A> est implémenté en tant qu'itérateur avec exécution différée. Cela signifie qu'en plus de l'itération sur la liste liée, il effectue certaines tâches comme l'allocation de l'objet itérateur et le suivi de l'état d'exécution. Ces tâches peuvent être divisées en deux catégories : les tâches effectuées lors de la configuration de l'itérateur et les tâches effectuées à chaque itération. Les tâches de configuration représentent une part réduite et fixe du travail, tandis que les tâches effectuées à chaque itération sont proportionnelles au nombre d'éléments de la collection source.

- Dans `query1`, la clause `Where` indique que la requête doit appeler la méthode <xref:System.Linq.Enumerable.Where%2A>. Cette méthode est également implémentée en tant qu'itérateur. Les tâches de configuration se composent de l'instanciation du délégué qui fera référence à l'expression, en plus de la configuration normale d'un itérateur. A chaque itération, le délégué est appelé pour exécuter le prédicat. Les tâches de configuration et les tâches effectuées à chaque itération sont similaires aux tâches effectuées lors de l'itération sur l'axe.

- Dans `query1`, la clause select indique que la requête doit appeler la méthode <xref:System.Linq.Enumerable.Select%2A>. Cette méthode fournit le même profil de performance que la méthode <xref:System.Linq.Enumerable.Where%2A>.

- Dans `query2`, la clause `Where` et la `Select` clause ont toutes deux le même profil de performance que dans `query1`.

 L'itération sur `query2` est donc directement proportionnelle au nombre d'éléments de la source de la première requête, en d'autres termes, elle suit un algorithme linéaire.

## <a name="see-also"></a>Voir aussi

- [Performances (LINQ to XML) (Visual Basic)](performance-linq-to-xml.md)
