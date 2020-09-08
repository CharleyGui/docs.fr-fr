---
title: Bogues mixtes de code déclaratif/impératif-LINQ to XML
description: Découvrez comment reconnaître et éviter les problèmes qui peuvent se produire lorsque le code itère le long d’un axe en apportant des modifications.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 280bb62d15ff28d1fd09ca2d0c52c0a0c36d7282
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553276"
---
# <a name="mixed-declarativeimperative-code-bugs-linq-to-xml"></a>Bogues mixtes de code déclaratif/impératif (LINQ to XML)

LINQ to XML contient différentes méthodes qui vous permettent de modifier directement une arborescence XML. Vous pouvez ajouter des éléments, supprimer des éléments, modifier le contenu d'un élément, ajouter des attributs, et ainsi de suite. Cette interface de programmation est décrite dans [modifier des arborescences XML](in-memory-xml-tree-modification-vs-functional-construction.md). Si vous effectuez une itération au sein de l’un des axes, par exemple <xref:System.Xml.Linq.XContainer.Elements%2A> , et que vous modifiez l’arborescence XML à mesure que vous itérez au sein de l’axe, vous pouvez vous retrouver avec des bogues étranges.

Ce problème porte parfois le nom de « problème Halloween ».

Lorsque vous écrivez du code à l’aide de LINQ qui itère au sein d’une collection, vous écrivez du code dans un style déclaratif. C’est plus similaire à décrire *ce* que vous souhaitez, au lieu de *la façon dont* vous souhaitez le faire. Si vous écrivez du code qui 1) obtient le premier élément, 2) le teste pour une certaine condition, 3) le modifie et 4) le replace dans la liste, il s'agit de code impératif. Vous indiquez à l’ordinateur *Comment* faire ce que vous voulez faire.

Le mélange de ces styles de code dans la même opération entraîne des problèmes. Tenez compte des éléments suivants :

Supposez que vous avez une liste liée avec trois éléments (a, b et c) :

> a-> b-> c

Maintenant, supposez que vous souhaitez vous déplacer dans la liste liée et ajouter trois nouveaux éléments (a', b' et c'). Vous souhaitez que la liste liée résultante ressemble à ceci :

 > a-> a'-> b-> b'-> c-> c'

Vous écrivez donc du code qui itère au sein de la liste et, pour chaque élément, ajoute un nouvel élément juste après. Votre code verra d'abord l'élément `a` et insérera `a'` après lui. Maintenant, votre code passera au nœud suivant dans la liste, ce qui signifie `a'` qu’il ajoute un nouvel élément entre a et b à la liste.

Comment pourriez-vous le résoudre ? Et bien, vous pourriez effectuer une copie de la liste liée d'origine et créer une toute nouvelle liste. Ou, si vous écrivez du code purement impératif, vous pouvez trouver le premier élément, ajouter le nouvel élément, puis avancer deux fois dans la liste liée, en avançant l’élément que vous venez d’ajouter.

## <a name="example-adding-while-iterating"></a>Exemple : ajout en cours d’itération

Par exemple, supposons que vous souhaitiez écrire du code pour créer un doublon de chaque élément dans une arborescence :

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    root.Add(new XElement(e.Name, (string)e));
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    root.Add(New XElement(e.Name, e.Value))
Next
```

Ce code entre dans une boucle infinie. L'instruction `foreach` itère au sein de l'axe `Elements()` et ajoute de nouveaux éléments à l'élément `doc`. Elle finit par itérer également au sein des éléments qu'elle vient d'ajouter. Et puisqu'elle alloue de nouveaux objets à chaque itération de la boucle, elle finira par consommer toute la mémoire disponible.

Vous pouvez résoudre ce problème en extrayant la collection en mémoire à l’aide de l’opérateur de requête standard <xref:System.Linq.Enumerable.ToList%2A>, comme suit :

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements().ToList())
    root.Add(new XElement(e.Name, (string)e));
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    root.Add(New XElement(e.Name, e.Value))
Next
Console.WriteLine(root)
```

À présent, le code fonctionne. Il en résulte l'arborescence XML suivante :

```xml
<Root>
  <A>1</A>
  <B>2</B>
  <C>3</C>
  <A>1</A>
  <B>2</B>
  <C>3</C>
</Root>
```

## <a name="example-deleting-while-iterating"></a>Exemple : suppression lors de l’itération

Si vous souhaitez supprimer tous les nœuds à un certain niveau, vous pourriez être tenté d'écrire du code ressemblant à celui-ci :

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    e.Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    e.Remove()
Next
Console.WriteLine(root)
```

Toutefois, cela ne fait pas ce que vous voulez. Dans ce cas, une fois que vous avez supprimé le premier élément, A, il est supprimé de l’arborescence XML contenue dans la racine et le code dans la méthode Elements qui effectue l’itération ne peut pas trouver l’élément suivant.

Cet exemple produit la sortie suivante :

```xml
<Root>
  <B>2</B>
  <C>3</C>
</Root>
```

La solution consiste à nouveau à appeler <xref:System.Linq.Enumerable.ToList%2A> afin de matérialiser la collection, comme suit :

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements().ToList())
    e.Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    e.Remove()
Next
Console.WriteLine(root)
```

Cet exemple produit la sortie suivante :

```xml
<Root />
```

En guise d'alternative, vous pouvez éliminer l'itération en appelant <xref:System.Xml.Linq.XElement.RemoveAll%2A> sur l'élément parent :

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
root.RemoveAll();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
root.RemoveAll()
Console.WriteLine(root)
```

## <a name="example-why-linq-cant-automatically-handle-these-issues"></a>Exemple : pourquoi LINQ ne peut pas gérer automatiquement ces problèmes

Une approche consisterait à toujours tout placer en mémoire au lieu d'effectuer une évaluation différée. Toutefois, cela serait très coûteux en termes de performances et d'utilisation de la mémoire. En fait, si LINQ, et LINQ to XML, devaient adopter cette approche, cela échouerait dans les situations réelles.

Une autre approche possible consisterait à placer une certaine syntaxe de transaction dans LINQ et à faire en sorte que le compilateur tente d’analyser le code pour déterminer si une collection particulière devait être matérialisée. Toutefois, tenter de déterminer tout le code qui a des effets secondaires est une tâche incroyablement complexe. Considérez le code suivant :

```csharp
var z =
    from e in root.Elements()
    where TestSomeCondition(e)
    select DoMyProjection(e);
```

```vb
Dim z = _
    From e In root.Elements() _
    Where (TestSomeCondition(e)) _
    Select DoMyProjection(e)
```

Un tel code d'analyse devrait analyser les méthodes TestSomeCondition et DoMyProjection, et toutes les méthodes appelées par ces méthodes, pour déterminer si du code a des effets secondaires. Mais le code d'analyse ne pourrait pas simplement rechercher le code qui aurait des effets secondaires. Il lui faudrait sélectionner uniquement le code ayant des effets secondaires sur les éléments enfants de `root` dans cette situation.

LINQ to XML n’essaie pas d’effectuer une telle analyse. C’est à vous d’éviter ces problèmes.

## <a name="example-use-declarative-code-to-generate-a-new-xml-tree-rather-than-modify-the-existing-tree"></a>Exemple : utiliser du code déclaratif pour générer une nouvelle arborescence XML au lieu de modifier l’arborescence existante

Pour éviter de tels problèmes, ne mélangez pas de code déclaratif et impératif, même si vous connaissez exactement la sémantique de vos collections et la sémantique des méthodes qui modifient l’arborescence XML. Si vous écrivez du code qui évite les problèmes, votre code devra être maintenu par d’autres développeurs à l’avenir, et ils ne seront peut-être pas aussi clairs pour les problèmes. Si vous combinez des styles de codage déclaratifs et impératifs, votre code sera plus fragile.  Si vous écrivez du code qui matérialise une collection afin d'éviter ces problèmes, ajoutez des commentaires appropriés à votre code de sorte que les programmeurs de maintenance comprennent le problème. 

Si les performances et autres considérations le permettent, utilisez uniquement du code déclaratif. Ne modifiez pas votre arborescence XML existante. Au lieu de cela, générez-en un nouveau, comme indiqué dans l’exemple suivant :

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
XElement newRoot = new XElement("Root",
    root.Elements(),
    root.Elements()
);
Console.WriteLine(newRoot);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
Dim newRoot As XElement = New XElement("Root", _
    root.Elements(), root.Elements())
Console.WriteLine(newRoot)
```
