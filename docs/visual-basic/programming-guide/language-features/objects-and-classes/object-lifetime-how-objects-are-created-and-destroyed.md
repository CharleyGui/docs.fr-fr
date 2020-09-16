---
title: 'Durée de vie d’un objet : création et destruction des objets'
ms.date: 07/20/2015
f1_keywords:
- vb.Constructor
helpviewer_keywords:
- destructors, object lifetime
- Sub Finalize destructor
- objects [Visual Basic], destroying
- lifetime [Visual Basic], objects
- Sub New constructor, object lifetime
- Finalize method [Visual Basic], object lifetime
- objects [Visual Basic], creating
- Class_Terminate
- Dispose method [Visual Basic], object lifetime
- Class_Initialize
- object creation [Visual Basic], object lifetime
- parameterized constructors
- objects [Visual Basic], lifetime
- objects [Visual Basic], garbage collection
- constructors [Visual Basic], object lifetime
- Sub Dispose destructor
- garbage collection [Visual Basic], Visual Basic
ms.assetid: f1ee8458-b156-44e0-9a8a-5dd171648cd8
ms.openlocfilehash: a32a5d075b5b1d02632c80216e7c2c12920bf4a2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544139"
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>Durée de vie d'un objet : création et destruction des objets (Visual Basic)

Une instance de classe (objet) est créée à l'aide du mot clé `New`. Des tâches d’initialisation doivent souvent être exécutées sur les nouveaux objets préalablement à leur utilisation. Ces tâches d’initialisation consistent généralement à ouvrir des fichiers, à se connecter à des bases de données et à lire des valeurs de clés de Registre. Visual Basic contrôle l’initialisation de nouveaux objets à l’aide de procédures appelées *constructeurs* (méthodes spéciales qui autorisent le contrôle sur l’initialisation).

Dès lors qu'un objet est hors de portée, il est libéré par le CLR (Common Language Runtime). Visual Basic contrôle la mise en version des ressources système à l’aide de procédures appelées *destructeurs*. Ensemble, constructeurs et destructeurs facilitent la création de bibliothèques de classes robustes et prévisibles.

## <a name="using-constructors-and-destructors"></a>Utilisation des constructeurs et des destructeurs

Les constructeurs et les destructeurs contrôlent la création et la destruction d'objets. Les `Sub New` `Sub Finalize` procédures et de Visual Basic initialiser et détruire des objets ; elles remplacent les `Class_Initialize` `Class_Terminate` méthodes et utilisées dans Visual Basic 6,0 et versions antérieures.

### <a name="sub-new"></a>Sub New

Le constructeur `Sub New` ne peut s'exécuter qu'une seule fois lors de la création d'une classe. Il ne peut pas être appelé explicitement ailleurs que dans la première ligne de code d'un autre constructeur de la même classe ou d'une classe dérivée. De plus, le code figurant dans la méthode `Sub New` s'exécute toujours avant tout autre code présent dans une classe. Visual Basic crée implicitement un `Sub New` constructeur au moment de l’exécution si vous ne définissez pas explicitement une `Sub New` procédure pour une classe.

Pour créer un constructeur pour une classe, créez une procédure nommée `Sub New` n'importe où dans la définition de la classe. Pour créer un constructeur paramétrable, spécifiez les noms et les types de données des arguments de `Sub New` comme vous le feriez pour spécifier les arguments d’une autre procédure, comme dans le code suivant :

[!code-vb[VbVbalrOOP#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#42)]

Les constructeurs sont souvent surchargés, comme dans le code suivant :

[!code-vb[VbVbalrOOP#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#116)]

Quand vous définissez une classe dérivée d'une autre classe, la première ligne d'un constructeur doit être un appel au constructeur de la classe de base, à moins que celle-ci contienne un constructeur accessible qui n'accepte aucun paramètre. Un appel à la classe de base contenant le constructeur ci-dessus, par exemple, serait `MyBase.New(s)`. Sinon, `MyBase.New` est facultatif et le runtime Visual Basic l’appelle implicitement.

Une fois que vous avez écrit le code destiné à appeler le constructeur de l'objet parent, vous pouvez ajouter du code d'initialisation supplémentaire à la procédure `Sub New`. `Sub New` peut accepter des arguments quand elle est appelée en tant que constructeur paramétrable. Ces paramètres sont passés à partir de la procédure appelant le constructeur, par exemple, `Dim AnObject As New ThisClass(X)`.

### <a name="sub-finalize"></a>Sub Finalize

Avant de libérer des objets, le CLR appelle automatiquement la méthode `Finalize` pour les objets qui définissent une procédure `Sub Finalize`. La méthode `Finalize` peut contenir du code qui doit s'exécuter juste avant la destruction d'un objet. Tel est le cas du code destiné à fermer les fichiers et à enregistrer les informations d'état. L'exécution de `Sub Finalize` pouvant occasionner une légère baisse des performances, ne définissez une méthode `Sub Finalize` que si vous avez besoin de libérer des objets explicitement.

> [!NOTE]
> Le garbage collector du CLR ne supprime pas (et ne peut pas) les objets *non managés*, les objets que le système d’exploitation exécute directement, en dehors de l’environnement CLR. Ceci s'explique par le fait que la méthode de suppression des objets non managés varie en fonction de leur type. Ces informations ne sont pas directement associées à l'objet non managé ; elles doivent se trouver dans la documentation relative à l'objet. Une classe qui utilise des objets non managés doit les supprimer dans sa méthode `Finalize`.

Le destructeur `Finalize` est une méthode protégée qui ne peut être appelée qu'à partir de la classe à laquelle elle appartient ou de classes dérivées. Étant donné que le système appelle `Finalize` automatiquement quand un objet est détruit, il n’est pas conseillé d’appeler `Finalize` explicitement en dehors de l’implémentation de `Finalize` d’une classe dérivée.

Contrairement à `Class_Terminate`, qui s'exécute dès qu'un objet a la valeur nothing, il s'écoule généralement un certain laps de temps entre le moment où un objet est hors de portée et le moment où Visual Basic appelle le destructeur `Finalize`. Visual Basic .NET autorise un deuxième type de destructeur, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> , qui peut être appelé explicitement à tout moment pour libérer immédiatement des ressources.

> [!NOTE]
> Un destructeur `Finalize` ne doit pas lever d'exceptions, car elles ne peuvent pas être gérées par l'application et peuvent provoquer l'arrêt de l'application.

### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>Fonctionnement des méthodes New et Finalize dans une hiérarchie de classes

Chaque fois qu'une instance de classe est créée, le CLR (Common Language Runtime) tente d'exécuter une procédure nommée `New`, si elle existe dans cet objet. `New` est un type de procédure appelée `constructor` qui sert à initialiser les nouveaux objets avant l'exécution de tout autre code contenu dans un objet. Un constructeur `New` permet d'ouvrir des fichiers, de se connecter à des bases de données, d'initialiser des variables et de gérer d'autres tâches à effectuer préalablement à l'utilisation d'un objet.

Quand une instance de classe dérivée est créée, le constructeur `Sub New` de la classe de base s'exécute en premier, suivie des constructeurs des classes dérivées. Cela s'explique par le fait que la première ligne de code d'un constructeur `Sub New` utilise la syntaxe `MyBase.New()` pour appeler le constructeur de la classe qui le précède immédiatement dans la hiérarchie de classes. Le constructeur `Sub New` est ensuite appelé pour chaque classe de la hiérarchie de classes jusqu'à ce que le constructeur de la classe de base ait été atteint. À ce stade, le code contenu dans le constructeur de la classe de base s'exécute, suivi du code contenu dans chaque constructeur de toutes les classes dérivées, tandis que le code contenu dans les classes les plus dérivées est exécuté en dernier.

![Capture d’écran montrant les constructeurs et l’héritage de la hiérarchie de classes.](./media/object-lifetime-how-objects-are-created-and-destroyed/subnew-constructor-inheritance.gif)

Quand un objet n'est plus utile, le CLR appelle la méthode <xref:System.Object.Finalize%2A> pour cet objet avant de libérer sa mémoire. La méthode <xref:System.Object.Finalize%2A> est appelée `destructor`, car elle effectue des tâches de nettoyage, comme l’enregistrement des informations d’état, la fermeture des fichiers et des connexions aux bases de données, ainsi que les autres tâches à effectuer avant de libérer l’objet.

![Capture d’écran montrant le destructeur de méthode Finalize.](./media/object-lifetime-how-objects-are-created-and-destroyed/finalize-method-destructor.gif)

## <a name="idisposable-interface"></a>Interface IDisposable

Les instances de classe contrôlent souvent les ressources non gérées par le CLR, comme les handles Windows et les connexions de base de données. Ces ressources doivent être supprimées dans la méthode `Finalize` de la classe, afin qu'elles soient libérées au moment où l'objet est détruit par le récupérateur de mémoire. Cependant, celui-ci ne détruit les objets qu’à partir du moment où le CLR a besoin de mémoire supplémentaire. Autrement dit, la libération des ressources peut prendre un certain temps après que l'objet est hors de portée.

Pour compléter l'action du récupérateur de mémoire, vos classes peuvent fournir un mécanisme de gestion active des ressources système si elles implémentent l'interface <xref:System.IDisposable>. <xref:System.IDisposable> dispose d'une méthode, <xref:System.IDisposable.Dispose%2A>, que les clients doivent appeler quand ils cessent d'utiliser un objet. Vous pouvez utiliser la méthode <xref:System.IDisposable.Dispose%2A> pour libérer immédiatement des ressources et effectuer certaines tâches, comme la fermeture des fichiers et des connexions de base de données. Contrairement au destructeur `Finalize`, la méthode <xref:System.IDisposable.Dispose%2A> n'est pas appelée automatiquement. Les clients d’une classe doivent appeler <xref:System.IDisposable.Dispose%2A> explicitement quand vous voulez libérer immédiatement des ressources.

### <a name="implementing-idisposable"></a>Implémentation de IDisposable

Une classe qui implémente l'interface <xref:System.IDisposable> doit inclure les sections de code suivantes :

- Un champ de suivi permettant de déterminer si l'objet a été supprimé :

  ```vb
  Protected disposed As Boolean = False
  ```

- Une surcharge de la méthode <xref:System.IDisposable.Dispose%2A> qui libère les ressources de la classe. Cette méthode doit être appelée par les méthodes <xref:System.IDisposable.Dispose%2A> et `Finalize` de la classe de base :

  ```vb
  Protected Overridable Sub Dispose(ByVal disposing As Boolean)
      If Not Me.disposed Then
          If disposing Then
              ' Insert code to free managed resources.
          End If
          ' Insert code to free unmanaged resources.
      End If
      Me.disposed = True
  End Sub
  ```

- Une implémentation de <xref:System.IDisposable.Dispose%2A> qui contient uniquement le code suivant :

  ```vb
  Public Sub Dispose() Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)
  End Sub
  ```

- Une substitution de la méthode `Finalize` qui contient uniquement le code suivant :

  ```vb
  Protected Overrides Sub Finalize()
      Dispose(False)
      MyBase.Finalize()
  End Sub
  ```

### <a name="deriving-from-a-class-that-implements-idisposable"></a>Dérivation d'une classe qui implémente IDisposable

Une classe dérivée d'une classe de base qui implémente l'interface <xref:System.IDisposable> n'a pas besoin de substituer les méthodes de base à moins qu'elle utilise des ressources supplémentaires dont la suppression s'avère nécessaire. Dans ce cas, la classe dérivée doit substituer la méthode `Dispose(disposing)` de la classe de base pour supprimer les ressources de la classe dérivée. Cette substitution doit appeler la méthode `Dispose(disposing)` de la classe de base.

```vb
Protected Overrides Sub Dispose(ByVal disposing As Boolean)
    If Not Me.disposed Then
        If disposing Then
            ' Insert code to free managed resources.
        End If
        ' Insert code to free unmanaged resources.
    End If
    MyBase.Dispose(disposing)
End Sub
```

Une classe dérivée ne doit pas substituer les méthodes <xref:System.IDisposable.Dispose%2A> et `Finalize` de la classe de base. Quand ces méthodes sont appelées à partir d'une instance de la classe dérivée, l'implémentation de ces méthodes au niveau de la classe de base appelle la substitution de la méthode `Dispose(disposing)` de la classe dérivée.

## <a name="garbage-collection-and-the-finalize-destructor"></a>Garbage collection et destructeur Finalize

Le .NET Framework utilise le système de *garbage collection de suivi des références* pour libérer périodiquement les ressources inutilisées. Visual Basic 6,0 et les versions antérieures utilisaient un système différent appelé *décompte de références* pour gérer les ressources. Même si les deux systèmes remplissent la même fonction automatiquement, des différences importantes existent entre les deux.

Le CLR détruit périodiquement des objets quand le système considère qu’ils ne sont plus nécessaires. Les objets sont libérés plus rapidement quand les ressources système viennent à manquer et moins souvent dans le cas contraire. Compte tenu du décalage qui existe entre le moment où un objet est hors de portée et le moment où le CLR le libère, contrairement aux objets dans Visual Basic 6.0 et les versions antérieures, il est impossible de déterminer exactement à quel moment l'objet sera détruit. Dans ce cas, les objets sont considérés comme ayant une *durée de vie non déterministe*. Dans la plupart des cas, la durée de vie non déterministe ne change pas la façon dont vous écrivez les applications, à condition de ne pas perdre de vue que le destructeur `Finalize` ne peut pas s'exécuter immédiatement à partir du moment où un objet est hors de portée.

Les systèmes de garbage collection se distinguent aussi en ce qui concerne l’utilisation de `Nothing`. Pour tirer parti du comptage de références dans Visual Basic 6.0 et les versions antérieures, les programmeurs attribuaient parfois aux variables objets la valeur `Nothing` pour libérer les références contenues dans ces variables. Si la variable contenait la dernière référence à l’objet, les ressources de l’objet étaient libérées immédiatement. Dans les versions ultérieures de Visual Basic, même si dans certains cas cette procédure est toujours utile, son exécution ne conduit jamais l’objet référencé à libérer immédiatement ses ressources. Pour libérer immédiatement des ressources, utilisez la méthode <xref:System.IDisposable.Dispose%2A> de l’objet, si elle est disponible. Le seul cas où vous devez affecter la valeur `Nothing` à une variable est quand sa durée de vie est plus longue que le temps dont a besoin le récupérateur de mémoire pour détecter les objets orphelins.

## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable.Dispose%2A>
- [Initialisation et suppression des composants](/previous-versions/visualstudio/visual-studio-2013/ws9dc6t6(v=vs.120))
- [Nouvel opérateur](../../../language-reference/operators/new-operator.md)
- [Nettoyage des ressources non managées](../../../../standard/garbage-collection/unmanaged.md)
- [Nothing](../../../language-reference/nothing.md)
