---
title: Implémentation d’IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: f1f0036c38299f2392f8c8705e67b7bb6b7db068
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058636"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Procédure pas à pas : implémentation d'IEnumerable(Of T) en Visual Basic

L' <xref:System.Collections.Generic.IEnumerable%601> interface est implémentée par les classes qui peuvent retourner une séquence de valeurs un élément à la fois. L’avantage de retourner des données un élément à la fois est que vous n’avez pas besoin de charger l’ensemble complet de données en mémoire pour l’utiliser. Vous devez uniquement utiliser suffisamment de mémoire pour charger un seul élément à partir des données. Les classes qui implémentent l' `IEnumerable(T)` interface peuvent être utilisées avec des `For Each` boucles ou des requêtes LINQ.  
  
 Par exemple, considérez une application qui doit lire un grand fichier texte et retourner chaque ligne du fichier qui correspond aux critères de recherche particuliers. L’application utilise une requête LINQ pour retourner les lignes du fichier qui correspondent aux critères spécifiés. Pour interroger le contenu du fichier à l’aide d’une requête LINQ, l’application peut charger le contenu du fichier dans un tableau ou une collection. Toutefois, le chargement de l’ensemble du fichier dans un tableau ou une collection consomme beaucoup plus de mémoire que nécessaire. La requête LINQ peut à la place interroger le contenu du fichier à l’aide d’une classe énumérable, en retournant uniquement les valeurs qui correspondent aux critères de recherche. Les requêtes qui retournent uniquement quelques valeurs correspondantes consomment beaucoup moins de mémoire.  
  
 Vous pouvez créer une classe qui implémente l' <xref:System.Collections.Generic.IEnumerable%601> interface pour exposer des données sources sous forme de données énumérables. Votre classe qui implémente l' `IEnumerable(T)` interface nécessitera une autre classe qui implémente l' <xref:System.Collections.Generic.IEnumerator%601> interface pour itérer au sein des données sources. Ces deux classes vous permettent de retourner des éléments de données de façon séquentielle sous la forme d’un type spécifique.  
  
 Dans cette procédure pas à pas, vous allez créer une classe qui implémente l' `IEnumerable(Of String)` interface et une classe qui implémente l' `IEnumerator(Of String)` interface pour lire un fichier texte ligne par ligne.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Création de la classe Enumerable  
  
**Créer le projet de classe Enumerable**

1. Dans Visual Basic, dans le menu **fichier** , pointez sur **nouveau** , puis cliquez sur **projet**.

1. Dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, vérifiez que **Windows** est sélectionné. Sélectionnez **Bibliothèque de classes** dans le volet **Modèles**. Dans la zone **Nom**, tapez `StreamReaderEnumerable`, puis cliquez sur **OK**. Le nouveau projet s’affiche.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier Class1. vb, puis cliquez sur **Renommer**. Renommez le fichier `StreamReaderEnumerable.vb` et appuyez sur Entrée. Quand vous renommez le fichier, la classe est également renommée `StreamReaderEnumerable`. Cette classe va implémenter l’interface `IEnumerable(Of String)`.

1. Cliquez avec le bouton droit sur le projet StreamReaderEnumerable, pointez sur **Ajouter**, puis cliquez sur **nouvel élément**. Sélectionnez le modèle de **classe** . Dans la zone **Name** (Nom), entrez `StreamReaderEnumerator.vb` et cliquez sur **OK**.

 La première classe de ce projet est la classe Enumerable et implémente l' `IEnumerable(Of String)` interface. Cette interface générique implémente l' <xref:System.Collections.IEnumerable> interface et garantit que les consommateurs de cette classe peuvent accéder aux valeurs de type `String` .  
  
**Ajouter le code pour implémenter IEnumerable**

1. Ouvrez le fichier StreamReaderEnumerable. vb.

2. Sur la ligne `Public Class StreamReaderEnumerable` qui suit, tapez la commande suivante et appuyez sur entrée.

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic remplit automatiquement la classe avec les membres qui sont requis par l' `IEnumerable(Of String)` interface.
  
3. Cette classe énumérable lit les lignes d’un fichier texte une ligne à la fois. Ajoutez le code suivant à la classe pour exposer un constructeur public qui prend un chemin d’accès de fichier en tant que paramètre d’entrée.

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. Votre implémentation de la <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> méthode de l' `IEnumerable(Of String)` interface retourne une nouvelle instance de la `StreamReaderEnumerator` classe. L’implémentation de la `GetEnumerator` méthode de l' `IEnumerable` interface peut être effectuée `Private` , car vous devez exposer uniquement les membres de l' `IEnumerable(Of String)` interface. Remplacez le code qui Visual Basic généré pour les `GetEnumerator` méthodes par le code suivant.

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**Ajouter le code pour implémenter IEnumerator**

1. Ouvrez le fichier StreamReaderEnumerator. vb.

2. Sur la ligne `Public Class StreamReaderEnumerator` qui suit, tapez la commande suivante et appuyez sur entrée.

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic remplit automatiquement la classe avec les membres qui sont requis par l' `IEnumerator(Of String)` interface.

3. La classe Enumerator ouvre le fichier texte et effectue l’e/s de fichier pour lire les lignes du fichier. Ajoutez le code suivant à la classe pour exposer un constructeur public qui utilise un chemin d’accès de fichier comme paramètre d’entrée et ouvrir le fichier texte pour la lecture.

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. Les `Current` Propriétés des `IEnumerator(Of String)` `IEnumerator` interfaces et retournent l’élément actuel du fichier texte sous forme de `String` . L’implémentation de la `Current` propriété de l' `IEnumerator` interface peut être effectuée `Private` , car vous devez exposer uniquement les membres de l' `IEnumerator(Of String)` interface. Remplacez le code qui Visual Basic généré pour les `Current` propriétés par le code suivant.

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. La `MoveNext` méthode de l' `IEnumerator` interface accède à l’élément suivant dans le fichier texte et met à jour la valeur retournée par la `Current` propriété. S’il n’y a plus d’éléments à lire, la `MoveNext` méthode retourne `False` ; sinon, la `MoveNext` méthode retourne `True` . Ajoutez le code suivant à la méthode `MoveNext` .

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. La `Reset` méthode de l' `IEnumerator` interface indique à l’itérateur de pointer vers le début du fichier texte et efface la valeur de l’élément actuel. Ajoutez le code suivant à la méthode `Reset` .

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. La `Dispose` méthode de l' `IEnumerator` interface garantit que toutes les ressources non managées sont libérées avant la destruction de l’itérateur. Le handle de fichier utilisé par l' `StreamReader` objet est une ressource non managée et doit être fermé avant la destruction de l’instance d’itérateur. Remplacez le code qui Visual Basic généré pour la `Dispose` méthode par le code suivant.

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a>Utilisation de l’exemple d’itérateur

 Vous pouvez utiliser une classe Enumerable dans votre code avec des structures de contrôle qui requièrent un objet qui implémente `IEnumerable` , tel qu’une `For Next` boucle ou une requête LINQ. L’exemple suivant montre le `StreamReaderEnumerable` dans une requête LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../linq/introduction-to-linq.md)
- [Flux de contrôle](index.md)
- [Structures de boucle](loop-structures.md)
- [For Each...Next (instruction)](../../../language-reference/statements/for-each-next-statement.md)
