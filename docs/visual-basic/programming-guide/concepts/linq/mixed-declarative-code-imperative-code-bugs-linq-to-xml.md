---
title: Bogues mixtes code déclaratif/code impératif (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
ms.openlocfilehash: e5526a64805b19ea293d3ef28636738923d03662
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84361071"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a>Bogues mixtes code déclaratif/code impératif (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] contient diverses méthodes qui vous permettent de modifier directement une arborescence XML. Vous pouvez ajouter des éléments, supprimer des éléments, modifier le contenu d'un élément, ajouter des attributs, et ainsi de suite. Cette interface de programmation est décrite dans [modification d’arborescences XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md). Si vous itérez au sein de l'un des axes, tels que <xref:System.Xml.Linq.XContainer.Elements%2A>, et que vous modifiez l'arborescence XML à mesure que vous parcourez l'axe, vous pouvez constater des bogues étranges.  
  
 Ce problème porte parfois le nom de « problème Halloween ».  
  
## <a name="definition-of-the-problem"></a>Définition du problème  
 Lorsque vous écrivez du code qui itère au sein d’une collection avec LINQ, vous écrivez du code dans un style déclaratif. Cela correspond davantage à décrire *ce que* vous voulez obtenir, plutôt que *comment* vous voulez l’obtenir. Si vous écrivez du code qui 1) obtient le premier élément, 2) le teste pour une certaine condition, 3) le modifie et 4) le replace dans la liste, il s'agit de code impératif. Vous indiquez à l’ordinateur *comment* faire ce que vous voulez faire.  
  
 Le mélange de ces styles de code dans la même opération entraîne des problèmes. Tenez compte des éléments suivants :  
  
 Supposez que vous avez une liste liée avec trois éléments (a, b et c) :  
  
 `a -> b -> c`  
  
 Maintenant, supposez que vous souhaitez vous déplacer dans la liste liée et ajouter trois nouveaux éléments (a', b' et c'). Vous souhaitez que la liste liée résultante ressemble à ceci :  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Vous écrivez donc du code qui itère au sein de la liste et, pour chaque élément, ajoute un nouvel élément juste après. Votre code verra d'abord l'élément `a` et insérera `a'` après lui. Ensuite, votre code passera au nœud suivant dans la liste, qui sera alors `a'` ! Il ajoutera joyeusement un nouvel élément à la liste, `a''`.  
  
 Comment résoudre ce problème dans le monde réel ? Et bien, vous pourriez effectuer une copie de la liste liée d'origine et créer une toute nouvelle liste. Ou si vous écrivez du code entièrement impératif, vous pourriez rechercher le premier élément, ajouter le nouvel élément, puis avancer de deux pas dans la liste liée, en passant « par-dessus » l'élément que vous venez d'ajouter.  
  
## <a name="adding-while-iterating"></a>Ajout lors de l'itération  
 Supposez par exemple que vous souhaitez écrire du code qui, pour chaque élément d'une arborescence, crée un élément dupliqué :  
  
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
  
## <a name="deleting-while-iterating"></a>Suppression lors de l'itération  
 Si vous souhaitez supprimer tous les nœuds à un certain niveau, vous pourriez être tenté d'écrire du code ressemblant à celui-ci :  
  
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
  
 Toutefois, ce code ne fait pas ce que vous voulez. Dans cette situation, après que vous avez supprimé le premier élément, A, il est supprimé de l'arborescence XML contenue dans la racine et le code dans la méthode Elements qui effectue l'itération ne peut trouver l'élément suivant.  
  
 Le code ci-dessus génère la sortie suivante :  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 La solution consiste à nouveau à appeler <xref:System.Linq.Enumerable.ToList%2A> afin de matérialiser la collection, comme suit :  
  
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
  
 Ce code produit la sortie suivante :  
  
```xml  
<Root />  
```  
  
 En guise d'alternative, vous pouvez éliminer l'itération en appelant <xref:System.Xml.Linq.XElement.RemoveAll%2A> sur l'élément parent :  
  
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
  
## <a name="why-cant-linq-automatically-handle-this"></a>Pourquoi LINQ ne peut-il gérer cela automatiquement ?  
 Une approche consisterait à toujours tout placer en mémoire au lieu d'effectuer une évaluation différée. Toutefois, cela serait très coûteux en termes de performances et d'utilisation de la mémoire. En fait, si LINQ (et LINQ to XML) devait suivre cette approche, cela échouerait dans les situations de monde réel.  
  
 Une autre approche possible consisterait à placer une certaine syntaxe de transaction dans LINQ et à faire en sorte que le compilateur tente d'analyser le code et de déterminer si une collection spécifique nécessite une matérialisation. Toutefois, tenter de déterminer tout le code qui a des effets secondaires est une tâche incroyablement complexe. Examinons le code ci-dessous.  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 Un tel code d'analyse devrait analyser les méthodes TestSomeCondition et DoMyProjection, et toutes les méthodes appelées par ces méthodes, pour déterminer si du code a des effets secondaires. Mais le code d'analyse ne pourrait pas simplement rechercher le code qui aurait des effets secondaires. Il lui faudrait sélectionner uniquement le code ayant des effets secondaires sur les éléments enfants de `root` dans cette situation.  
  
 LINQ to XML ne tente pas d'effectuer une telle analyse.  
  
 Il vous incombe d'éviter ce genre de problèmes.  
  
## <a name="guidance"></a>Assistance  
 En premier lieu, ne mélangez pas de code déclaratif et impératif.  
  
 Même si vous connaissez exactement la sémantique de vos collections et la sémantique des méthodes qui modifient l'arborescence XML, si vous écrivez du code intelligent qui évite ces catégories de problèmes, votre code devra être maintenu par d'autres développeurs dans le futur et ils n'auront peut-être pas la même vision du problème que vous. Si vous combinez des styles de codage déclaratifs et impératifs, votre code sera plus fragile.  
  
 Si vous écrivez du code qui matérialise une collection afin d'éviter ces problèmes, ajoutez des commentaires appropriés à votre code de sorte que les programmeurs de maintenance comprennent le problème.   
  
 En second lieu, si les performances et autres considérations le permettent, utilisez uniquement du code déclaratif. Ne modifiez pas votre arborescence XML existante. Générez-en une nouvelle.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Visual Basic (Advanced LINQ to XML Programming)](advanced-linq-to-xml-programming.md)
