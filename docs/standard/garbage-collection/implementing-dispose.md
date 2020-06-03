---
title: Implémenter une méthode Dispose
ms.date: 05/27/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
ms.openlocfilehash: a16034b074b518b25244c47a7d00cb484e145c6e
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84307018"
---
# <a name="implement-a-dispose-method"></a>Implémenter une méthode Dispose

L’implémentation de la <xref:System.IDisposable.Dispose%2A> méthode est principalement destinée à libérer des ressources non managées utilisées par votre code. Lors de l’utilisation de membres d’instance qui sont des <xref:System.IDisposable> implémentations, il est courant d’appeler en cascade <xref:System.IDisposable.Dispose%2A> . Il existe des raisons supplémentaires pour l’implémentation de <xref:System.IDisposable.Dispose%2A> , telles que l’annulation d’une opération précédemment effectuée. Par exemple, la libération de la mémoire qui a été allouée, la suppression d’un élément d’une collection qui a été ajoutée, le signalement de la libération d’un verrou acquis, et ainsi de suite.

Le [garbage collector .net](index.md) n’alloue pas ou ne libère pas de mémoire non managée. Le modèle de suppression d’un objet, appelé modèle de suppression, impose un ordre sur la durée de vie d’un objet. Le modèle de suppression est utilisé pour les objets qui implémentent l' <xref:System.IDisposable> interface et est courant lors de l’interaction avec les handles de fichiers et de canaux, les handles de Registre, les handles d’attente ou les pointeurs vers des blocs de mémoire non managée. Cela est dû au fait que le garbage collector ne peut pas récupérer les objets non managés.

Pour garantir que les ressources sont toujours nettoyées de manière appropriée, une <xref:System.IDisposable.Dispose%2A> méthode doit être idempotent, de sorte qu’elle peut être appelée plusieurs fois sans lever d’exception. En outre, les appels suivants de <xref:System.IDisposable.Dispose%2A> ne doivent rien faire.

L’exemple de code fourni pour la <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> méthode montre comment garbage collection peut provoquer l’exécution d’un finaliseur, alors qu’une référence non managée à l’objet ou à ses membres est toujours en cours d’utilisation. Il peut être judicieux d’utiliser <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> pour rendre l’objet inéligible pour garbage collection du début de la routine actuelle jusqu’au point où cette méthode est appelée.

## <a name="safe-handles"></a>Handles sécurisés

L’écriture de code pour le finaliseur d’un objet est une tâche complexe qui peut provoquer des problèmes si elle n’est pas effectuée correctement. Par conséquent, nous vous recommandons de construire des objets <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> au lieu d'implémenter un finaliseur.

Un <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> est un type managé abstrait qui encapsule un <xref:System.IntPtr?displayProperty=nameWithType> qui identifie une ressource non managée. Sur Windows, il peut identifier un handle sur UNIX, un descripteur de fichier. Il fournit toute la logique nécessaire pour s’assurer que cette ressource est libérée une seule fois, lorsque la `SafeHandle` est supprimée de ou lorsque toutes les références à `SafeHandle` ont été supprimées et que l' `SafeHandle` instance est finalisée.

<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>Est une classe de base abstraite. Les classes dérivées fournissent des instances spécifiques pour différents genres de handles. Ces classes dérivées valident les valeurs de qui <xref:System.IntPtr?displayProperty=nameWithType> sont considérées comme non valides et comment libérer le handle. Par exemple, <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> dérive de `SafeHandle` à Wrap `IntPtrs` qui identifient les descripteurs/descripteurs de fichiers ouverts et substitue sa <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle?displayProperty=nameWithType> méthode pour le fermer (via la `close` fonction sur UNIX ou `CloseHandle` Function sur Windows). La plupart des API dans les bibliothèques .NET qui créent une ressource non managée l’encapsulent dans un `SafeHandle` et le renvoient en `SafeHandle` fonction des besoins, plutôt que de transmettre le pointeur brut. Dans les situations où vous interagissez avec un composant non managé et récupérez un `IntPtr` pour une ressource non managée, vous pouvez créer votre propre `SafeHandle` type pour l’encapsuler. Par conséquent, peu de types n' `SafeHandle` ont pas besoin d’implémenter des finaliseurs ; la plupart des implémentations de modèle jetables finissent par encapsuler d’autres ressources managées, dont certaines peuvent être des `SafeHandle` s.

Les classes dérivées suivantes de l'espace de noms <xref:Microsoft.Win32.SafeHandles> fournissent des handles sécurisés :

- La classe <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle> et <xref:Microsoft.Win32.SafeHandles.SafePipeHandle>, pour les fichiers, les fichiers mappés en mémoire et les canaux.
- La classe <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle>, pour les vues de la mémoire.
- Les classes <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle> et <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> pour les constructions de chiffrement.
- La classe <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> pour les clés de Registre.
- La classe <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle>, pour les handles d'attente.

## <a name="dispose-and-disposebool"></a>Dispose () et dispose (bool)

L'interface <xref:System.IDisposable> requiert l'implémentation d'une méthode unique sans paramètre, <xref:System.IDisposable.Dispose%2A>. En outre, toute classe non scellée doit avoir une `Dispose(bool)` méthode de surcharge supplémentaire à implémenter :

- `public`Implémentation non virtuelle ( `NonInheritable` en Visual Basic) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> qui n’a aucun paramètre.

- `protected virtual`Méthode ( `Overridable` en Visual Basic) `Dispose` dont la signature est :

  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]

  > [!IMPORTANT]
  > Le `disposing` paramètre doit être `false` lorsqu’il est appelé à partir d’un finaliseur, et lorsqu’il est `true` appelé à partir de la <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> méthode. En d’autres termes, il est quand il est appelé de façon `true` déterministe et lorsqu’il n’est `false` pas appelé de manière déterministe.

### <a name="the-dispose-method"></a>La méthode Dispose ()

Étant donné que le `public` , non virtuel ( `NonInheritable` en Visual Basic), la `Dispose` méthode sans paramètre est appelée par un consommateur du type, son objectif est de libérer des ressources non managées, d’effectuer un nettoyage général et d’indiquer que le finaliseur, s’il en existe un, ne doit pas s’exécuter. La libération de la mémoire réelle associée à un objet géré est toujours le domaine du [garbage collector](index.md). De ce fait, son implémentation standard est la suivante :

[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]

La méthode `Dispose` effectue le nettoyage de tous les objets, le récupérateur de mémoire n'a plus donc besoin d'appeler la remplacement de <xref:System.Object.Finalize%2A?displayProperty=nameWithType> des objets. Par conséquent, l'appel à la méthode <xref:System.GC.SuppressFinalize%2A> empêche le récupérateur de mémoire d'exécuter le finaliseur. Si le type n'a pas de finaliseur, l'appel à <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> n'a aucun effet. Notez que le nettoyage réel est effectué par la `Dispose(bool)` surcharge de méthode.

### <a name="the-disposebool-method-overload"></a>Surcharge de la méthode Dispose (bool)

Dans la surcharge, le `disposing` paramètre est un <xref:System.Boolean> qui indique si l’appel de méthode provient d’une <xref:System.IDisposable.Dispose%2A> méthode (sa valeur est `true` ) ou d’un finaliseur (sa valeur est `false` ).

Le corps de la méthode se compose de deux blocs de code :

- Un bloc qui libère les ressources non managées. Ce bloc s'exécute indépendamment de la valeur du paramètre `disposing`.
- Un bloc conditionnel qui libère les ressources managées. Ce bloc s'exécute si la valeur de `disposing` est `true`. Les ressources managées qu'il libère peuvent inclure :

  - **Objets managés qui implémentent <xref:System.IDisposable>.** Le bloc conditionnel peut être utilisé pour appeler leur <xref:System.IDisposable.Dispose%2A> implémentation (dispose en cascade). Si vous avez utilisé une classe dérivée de <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> pour encapsuler votre ressource non managée, vous devez appeler l' <xref:System.Runtime.InteropServices.SafeHandle.Dispose?displayProperty=nameWithType> implémentation ici.

  - **Objets managés qui consomment de grandes quantités de mémoire ou consomment des ressources rares.** Affectez des références d’objets managés volumineux à `null` pour les rendre plus susceptibles d’être inaccessibles. Cela les libère plus rapidement que s’ils étaient récupérés de façon non déterministe.

Si l’appel de méthode provient d’un finaliseur, seul le code qui libère les ressources non managées doit s’exécuter. L’implémenteur est chargé de s’assurer que le chemin d’accès faux n’interagit pas avec les objets managés qui ont pu être récupérés. Cela est important, car l’ordre dans lequel le garbage collector détruit les objets managés pendant la finalisation n’est pas déterministe.

## <a name="cascade-dispose-calls"></a>Appels de suppression en cascade

Si votre classe possède un champ ou une propriété et que son type implémente <xref:System.IDisposable> , la classe conteneur elle-même doit également implémenter <xref:System.IDisposable> . Une classe qui instancie une <xref:System.IDisposable> implémentation et la stocke en tant que membre d’instance est également responsable de son nettoyage. Cela permet de s’assurer que les types jetables référencés ont la possibilité de procéder à un nettoyage déterministe à l’aide de la <xref:System.IDisposable.Dispose%2A> méthode. Dans cet exemple, la classe est `sealed` (ou `NotInheritable` dans Visual Basic).

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/disposable1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/disposable1.vb#1)]

## <a name="implement-the-dispose-pattern"></a>Implémenter le modèle de suppression

Toutes les classes non-sealed ou (classes Visual Basic non modifiées comme `NotInheritable` ) doivent être considérées comme une classe de base potentielle, car elles peuvent être héritées. Si vous implémentez le modèle de suppression pour une classe de base potentielle quelconque, vous devez fournir les éléments suivants :

- Une implémentation de <xref:System.IDisposable.Dispose%2A> qui appelle la méthode `Dispose(bool)`.
- `Dispose(bool)`Méthode qui effectue le nettoyage réel.
- Une classe dérivée de <xref:System.Runtime.InteropServices.SafeHandle> qui encapsule votre ressource managée (recommandée) ou une substitution de la méthode <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. La <xref:System.Runtime.InteropServices.SafeHandle> classe fournit un finaliseur, donc vous n’avez pas besoin d’en écrire un vous-même.

> [!IMPORTANT]
> Une classe de base peut uniquement référencer des objets managés et implémenter le modèle de suppression. Dans ce cas, un finaliseur n’est pas nécessaire. Un finaliseur est requis uniquement si vous référencez directement des ressources non managées.

Voici le modèle général d’implémentation du modèle de suppression d’une classe de base qui utilise un handle sécurisé.

[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]

> [!NOTE]
> L'exemple précédent utilise un objet <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> pour illustrer le modèle, mais il est possible d'utiliser à la place n'importe quel objet dérivé de <xref:System.Runtime.InteropServices.SafeHandle>. Notez que l'exemple n'instancie pas correctement son objet <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>.

Voici le modèle général d’implémentation du modèle de suppression d’une classe de base qui remplace <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.

[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]

> [!TIP]
> En C#, vous créez un [finaliseur](../../csharp/programming-guide/classes-and-structs/destructors.md) en substituant <xref:System.Object.Finalize%2A?displayProperty=nameWithType> . Dans Visual Basic, cette opération s’effectue à l’aide de `Protected Overrides Sub Finalize()` .

## <a name="implement-the-dispose-pattern-for-a-derived-class"></a>Implémenter le modèle de suppression d’une classe dérivée

Une classe dérivée d'une classe qui implémente l'interface <xref:System.IDisposable> ne doit pas implémenter <xref:System.IDisposable>, car l'implémentation de la classe de base de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> est héritée par les classes dérivées. Au lieu de cela, pour nettoyer une classe dérivée, vous devez fournir les éléments suivants :

- `protected override void Dispose(bool)`Méthode qui remplace la méthode de la classe de base et effectue le nettoyage réel de la classe dérivée. Cette méthode doit également appeler la `base.Dispose(bool)` `MyBase.Dispose(bool)` méthode (en Visual Basic) de la classe de base et passer son état de suppression pour l’argument.
- Une classe dérivée de <xref:System.Runtime.InteropServices.SafeHandle> qui encapsule votre ressource managée (recommandée) ou une substitution de la méthode <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. La classe <xref:System.Runtime.InteropServices.SafeHandle> fournit un finaliseur qui vous permet de ne pas avoir à en coder un. Si vous fournissez un finaliseur, il doit appeler la `Dispose(bool)` surcharge avec un `disposing` argument de `false` .

Voici le modèle général d’implémentation du modèle de suppression d’une classe dérivée qui utilise un handle sécurisé :

[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]

> [!NOTE]
> L'exemple précédent utilise un objet <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> pour illustrer le modèle, mais il est possible d'utiliser à la place n'importe quel objet dérivé de <xref:System.Runtime.InteropServices.SafeHandle>. Notez que l'exemple n'instancie pas correctement son objet <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>.

Voici le modèle général d'implémentation du modèle de suppression d'une classe dérivée qui remplace <xref:System.Object.Finalize%2A?displayProperty=nameWithType> :

[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]

## <a name="implement-the-dispose-pattern-with-safe-handles"></a>Implémenter le modèle de suppression avec des Handles sécurisés

L'exemple suivant illustre le modèle de suppression d'une classe de base, `DisposableStreamResource`, qui utilise un handle sécurisé pour encapsuler les ressources non managées. Il définit une classe `DisposableStreamResource` qui utilise <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> pour encapsuler un objet <xref:System.IO.Stream> qui représente un fichier ouvert. La classe comprend également une seule propriété, `Size` , qui retourne le nombre total d’octets dans le flux de fichier.

[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]

## <a name="implement-the-dispose-pattern-for-a-derived-class-with-safe-handles"></a>Implémenter le modèle de suppression d’une classe dérivée avec des Handles sécurisés

L'exemple suivant illustre le modèle de suppression d'une classe dérivée, `DisposableStreamResource2`, qui hérite de la classe `DisposableStreamResource` présentée dans l'exemple précédent. La classe ajoute une méthode supplémentaire, `WriteFileInfo`, et utilise un objet <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> pour encapsuler le handle du fichier accessible en écriture.

[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]

## <a name="see-also"></a>Voir aussi

- <xref:System.GC.SuppressFinalize%2A>
- <xref:System.IDisposable>
- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>
- <xref:Microsoft.Win32.SafeHandles>
- <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>
- [Définir et utiliser des classes et des structs (C++/CLI)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli)
