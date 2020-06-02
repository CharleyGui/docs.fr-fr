---
title: Utilisation d’objets implémentant IDisposable
ms.date: 05/13/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: 87eefe2bd347ba1564b2f06d49bbee3b85efdb97
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287595"
---
# <a name="using-objects-that-implement-idisposable"></a>Utilisation d’objets implémentant IDisposable

Le « garbage collector » de l’common language runtime récupère la mémoire utilisée par les objets managés, mais les types qui utilisent des ressources non managées implémentent l' <xref:System.IDisposable> interface pour permettre la récupération des ressources requises par ces ressources non managées. Une fois que vous avez fini d'utiliser un objet qui implémente <xref:System.IDisposable>, vous devez appeler l'implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> de l'objet. Vous pouvez le faire de deux façons :

- Avec l' `using` instruction C# ( `Using` dans Visual Basic).
- En implémentant un `try/finally` bloc et en appelant le <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> dans le `finally` .

## <a name="the-using-statement"></a>Instruction using

L' [ `using` instruction](../../csharp/language-reference/keywords/using-statement.md) en C# et l' [ `Using` instruction](../../visual-basic/language-reference/statements/using-statement.md) dans Visual Basic simplifient le code que vous devez écrire pour nettoyer un objet. L’instruction `using` obtient une ou plusieurs ressources, exécute les instructions que vous spécifiez, puis supprime automatiquement l’objet. Toutefois, l’instruction `using` est utile uniquement pour les objets utilisés dans la portée de la méthode dans laquelle elles sont construites.

L’exemple suivant utilise l’instruction `using` pour créer et libérer un objet <xref:System.IO.StreamReader?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]

Bien que la <xref:System.IO.StreamReader> classe implémente l' <xref:System.IDisposable> interface, ce qui indique qu’elle utilise une ressource non managée, l’exemple n’appelle pas explicitement la <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> méthode. Quand le compilateur C# ou Visual Basic rencontre l’instruction `using`, il émet en langage intermédiaire qui est équivalent au code suivant contenant explicitement un bloc `try/finally`.

[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]

L’instruction `using` en C# vous permet d’acquérir plusieurs ressources dans une seule instruction, ce qui équivaut en interne à des instructions `using` imbriquées. L'exemple suivant instancie deux objets <xref:System.IO.StreamReader> pour lire le contenu de deux fichiers différents.

[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Bloc try/finally

Au lieu d’encapsuler un bloc `try/finally` dans une instruction `using`, vous pouvez choisir d’implémenter le bloc `try/finally` directement. Il peut s’agir de votre style de codage personnel, ou vous pouvez le faire pour l’une des raisons suivantes :

- Pour inclure un `catch` bloc pour gérer les exceptions levées dans le `try` bloc. Sinon, toutes les exceptions levées dans l' `using` instruction ne sont pas gérées.

- Pour instancier un objet qui implémente <xref:System.IDisposable> dont la portée n'est pas locale au bloc dans lequel elle est déclarée.

L'exemple suivant est similaire à l'exemple précédent, mais il utilise un bloc `try/catch/finally` pour instancier, utiliser et supprimer un objet <xref:System.IO.StreamReader>, ainsi que pour gérer les exceptions levées par le constructeur <xref:System.IO.StreamReader> et sa méthode <xref:System.IO.StreamReader.ReadToEnd%2A>. Le code du `finally` bloc vérifie que l’objet qui implémente <xref:System.IDisposable> n’est pas `null` avant d’appeler la <xref:System.IDisposable.Dispose%2A> méthode. La non-exécution de cette opération peut générer une <xref:System.NullReferenceException> au moment de l'exécution.

[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]

Vous pouvez suivre ce modèle de base si vous choisissez d’implémenter (ou que vous devez implémenter) un bloc `try/finally`, car votre langage de programmation ne prend pas en charge l’instruction `using`, mais autorise des appels directs à la méthode <xref:System.IDisposable.Dispose%2A>.

## <a name="idisposable-instance-members"></a>Membres d’instance IDisposable

Si une classe contient une <xref:System.IDisposable> implémentation en tant que membre d’instance, qu’il s’agisse d’un champ ou d’une propriété, la classe doit également implémenter <xref:System.IDisposable> . Pour plus d’informations, consultez [implémenter une suppression en cascade](implementing-dispose.md#cascade-dispose-calls).

## <a name="see-also"></a>Voir aussi

- [Nettoyage de ressources non managées](unmanaged.md)
- [using, instruction (référence C#)](../../csharp/language-reference/keywords/using-statement.md)
- [Using, instruction (Visual Basic)](../../visual-basic/language-reference/statements/using-statement.md)
