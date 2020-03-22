---
title: Mise en œuvre de IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 4151a680050f234d450d8de5e67a767c54e8df68
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266909"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Procédure pas à pas : implémentation d'IEnumerable(Of T) en Visual Basic
L’interface <xref:System.Collections.Generic.IEnumerable%601> est implémentée par des classes qui peuvent retourner une séquence de valeurs un élément à la fois. L’avantage de retourner des données un élément à la fois est que vous n’avez pas à charger l’ensemble complet de données en mémoire pour travailler avec elle. Vous n’avez qu’à utiliser suffisamment de mémoire pour charger un seul élément à partir des données. Les classes `IEnumerable(T)` qui implémenter l’interface peuvent être utilisées avec `For Each` des boucles ou des requêtes LINQ.  
  
 Par exemple, considérez une application qui doit lire un fichier texte volumineux et retourner chaque ligne du fichier qui correspond à des critères de recherche particuliers. L’application utilise une requête LINQ pour retourner les lignes du fichier qui correspondent aux critères spécifiés. Pour interroger le contenu du fichier à l’aide d’une requête LINQ, l’application peut charger le contenu du fichier dans un tableau ou une collection. Cependant, le chargement de l’ensemble du fichier dans un tableau ou une collection consommerait beaucoup plus de mémoire que nécessaire. La requête linQ pourrait plutôt interroger le contenu du fichier en utilisant une classe enumérable, ne retournant que les valeurs qui correspondent aux critères de recherche. Les requêtes qui ne renvoient que quelques valeurs correspondantes consommeraient beaucoup moins de mémoire.  
  
 Vous pouvez créer une classe <xref:System.Collections.Generic.IEnumerable%601> qui implémente l’interface pour exposer les données sources comme des données enumérables. Votre classe qui `IEnumerable(T)` implémente l’interface <xref:System.Collections.Generic.IEnumerator%601> nécessitera une autre classe qui implémente l’interface pour itérer à travers les données source. Ces deux classes vous permettent de retourner des éléments de données séquentiellement en tant que type spécifique.  
  
 Dans cette procédure pas à pas, vous allez `IEnumerable(Of String)` créer une classe qui `IEnumerator(Of String)` implémente l’interface et une classe qui implémente l’interface pour lire un fichier texte une ligne à la fois.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Création de la classe Enumerable  
  
**Créer le projet de classe enumerable**

1. Dans Visual Basic, sur le menu **du fichier,** pointez vers **New** puis cliquez sur **Project**.

1. Dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, vérifiez que **Windows** est sélectionné. Sélectionnez **Bibliothèque de classes** dans le volet **Modèles**. Dans la zone **Nom**, tapez `StreamReaderEnumerable`, puis cliquez sur **OK**. Le nouveau projet est affiché.

1. Dans **Solution Explorer**, cliquez à droite sur le fichier Class1.vb et cliquez sur **Rename**. Renommez le fichier `StreamReaderEnumerable.vb` et appuyez sur Entrée. Quand vous renommez le fichier, la classe est également renommée `StreamReaderEnumerable`. Cette classe va implémenter l’interface `IEnumerable(Of String)`.

1. Cliquez à droite sur le projet StreamReaderEnumerable, pointez **d’ajouter,** puis cliquez sur **Nouvel article**. Sélectionnez le modèle **de classe.** Dans la zone **Name** (Nom), entrez `StreamReaderEnumerator.vb` et cliquez sur **OK**.

 La première classe de ce projet est la classe `IEnumerable(Of String)` enumerable et mettra en œuvre l’interface. Cette interface générique <xref:System.Collections.IEnumerable> implémente l’interface et garantit que `String`les consommateurs de cette classe peuvent accéder à des valeurs tapées comme .  
  
**Ajouter le code pour implémenter IEnumerable**

1. Ouvrez le fichier StreamReaderEnumerable.vb.

2. Sur la `Public Class StreamReaderEnumerable`ligne après , tapez ce qui suit et appuyez sur ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic remplit automatiquement la classe avec les `IEnumerable(Of String)` membres qui sont requis par l’interface.
  
3. Cette classe enumerable lira les lignes d’un fichier texte une ligne à la fois. Ajoutez le code suivant à la classe pour exposer un constructeur public qui prend un chemin de fichier comme paramètre d’entrée.

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. Votre mise <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> en œuvre de la méthode de l’interface `IEnumerable(Of String)` retournera une nouvelle instance de la `StreamReaderEnumerator` classe. La mise `GetEnumerator` en œuvre de la méthode de l’interface `IEnumerable` peut être faite, `Private`car vous devez exposer uniquement les membres de l’interface. `IEnumerable(Of String)` Remplacez le code généré `GetEnumerator` par Visual Basic pour les méthodes par le code suivant.

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**Ajouter le code pour implémenter IEnumerator**

1. Ouvrez le fichier StreamReaderEnumerator.vb.

2. Sur la `Public Class StreamReaderEnumerator`ligne après , tapez ce qui suit et appuyez sur ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic remplit automatiquement la classe avec les `IEnumerator(Of String)` membres qui sont requis par l’interface.

3. La classe d’enumérateur ouvre le fichier texte et exécute le fichier I/O pour lire les lignes du fichier. Ajoutez le code suivant à la classe pour exposer un constructeur public qui prend un chemin de fichier comme paramètre d’entrée et ouvrir le fichier texte pour la lecture.

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. Les `Current` propriétés `IEnumerator(Of String)` pour `IEnumerator` les deux et les interfaces `String`retournent l’élément actuel à partir du fichier texte comme un . La mise `Current` en œuvre de la propriété de l’interface `IEnumerator` peut être faite, `Private`car vous devez exposer uniquement les membres de l’interface. `IEnumerator(Of String)` Remplacez le code généré `Current` par Visual Basic pour les propriétés par le code suivant.

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. La `MoveNext` méthode `IEnumerator` de l’interface navigue vers l’élément suivant dans le `Current` fichier texte et met à jour la valeur qui est retournée par la propriété. S’il n’y a `MoveNext` plus `False`d’éléments à lire, la méthode revient; sinon `MoveNext` la `True`méthode revient . Ajoutez le code suivant à la méthode `MoveNext` .

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. La `Reset` méthode `IEnumerator` de l’interface oriente l’itérateur vers le début du fichier texte et efface la valeur actuelle de l’élément. Ajoutez le code suivant à la méthode `Reset` .

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. La `Dispose` méthode `IEnumerator` de l’interface garantit que toutes les ressources non mentées sont libérées avant que l’itérateur ne soit détruit. La poignée de fichier `StreamReader` qui est utilisée par l’objet est une ressource non gérée et doit être fermée avant que l’instance d’itérateur soit détruite. Remplacez le code généré `Dispose` par Visual Basic pour la méthode par le code suivant.

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a>À l’aide de l’itérateur d’échantillon

 Vous pouvez utiliser une classe enumérable dans votre code avec `IEnumerable`des structures `For Next` de contrôle qui nécessitent un objet qui implémente, comme une boucle ou une requête LINQ. L’exemple suivant `StreamReaderEnumerable` montre le dans une requête LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Flux de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For Each...Next (instruction)](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
