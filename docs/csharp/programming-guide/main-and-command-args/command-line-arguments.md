---
title: Arguments de ligne de commande - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: d6775263e6f1afb227aa263b01d60f5181da74f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093508"
---
# <a name="command-line-arguments-c-programming-guide"></a>Arguments de ligne de commande (Guide de programmation C#)

Vous pouvez envoyer des arguments à la méthode `Main` en définissant la méthode de l’une des manières suivantes :

[!code-csharp[csProgGuideMain#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#2)]  

[!code-csharp[csProgGuideMain#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#3)]

> [!NOTE]
> Pour activer les arguments `Main` de la ligne de commande dans la `Main` méthode d’une application Windows Forms, vous devez modifier manuellement la signature de dans *program.cs*. Le code généré par le Concepteur Windows Forms crée un `Main` sans paramètre d’entrée. Vous pouvez également utiliser <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> ou <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> pour accéder aux arguments de ligne de commande à partir de n’importe quel emplacement d’une application console ou Windows.

Le paramètre de la méthode `Main` est un tableau <xref:System.String> qui représente les arguments de ligne de commande. En général, vous déterminez s’il existe des arguments en testant la propriété `Length`, par exemple :

[!code-csharp[csProgGuideMain#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#4)]

Vous pouvez également convertir les arguments de chaîne en types numériques à l’aide de la classe <xref:System.Convert> ou de la méthode `Parse`. Par exemple, l’instruction suivante convertit `string` en nombre `long` en utilisant la méthode <xref:System.Int64.Parse%2A> :

```csharp
long num = Int64.Parse(args[0]);
```

Il est également possible d’utiliser le type C# `long`, qui sert d’alias à `Int64` :

```csharp
long num = long.Parse(args[0]);
```

Vous pouvez également utiliser la méthode `ToInt64` de la classe `Convert` pour obtenir le même résultat :

```csharp
long num = Convert.ToInt64(s);
```

Pour plus d’informations, consultez <xref:System.Int64.Parse%2A> et <xref:System.Convert>.

## <a name="example"></a> Exemple

L’exemple suivant montre comment utiliser des arguments de ligne de commande dans une application console. L’application prend un argument au moment de l’exécution, le convertit en entier, puis calcule la factorielle du nombre. Si aucun argument n’est fourni, l’application affiche un message pour expliquer comment le programme doit être utilisé.

Pour compiler et exécuter l’application à partir d’une invite de commandes, procédez comme suit :

1. Coller le code suivant dans n’importe quel éditeur de texte, puis enregistrer le fichier comme un fichier texte avec le nom *Factorial.cs*.

     [!code-csharp[csProgGuideMain#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#16)]

2. Dans l’écran **Démarrer** ou le menu **Démarrer**, ouvrez une fenêtre **Invite de commandes développeur** Visual Studio, puis accédez au dossier qui contient le fichier que vous venez de créer.

3. Entrez la commande suivante pour compiler l’application.
  
     `csc Factorial.cs`  
  
     Si votre application n’a pas d’erreurs de compilation, un fichier exécutable qui s’appelle *Factorial.exe* est créé.
  
4. Entrez la commande suivante pour calculer la factorielle de 3 :
  
     `Factorial 3`  
  
5. Cette commande génère la sortie suivante : `The factorial of 3 is 6.`

> [!NOTE]
> Quand vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [page Déboguer du Concepteur de projet](/visualstudio/ide/reference/debug-page-project-designer).

## <a name="see-also"></a>Voir aussi

- <xref:System.Environment?displayProperty=nameWithType>
- [Guide de programmation C#](../index.md)
- [Main() et arguments de ligne de commande](index.md)
- [Comment afficher les arguments de la ligne de commande](how-to-display-command-line-arguments.md)
- [Valeurs de retour Main()](main-return-values.md)
- [Classes](../classes-and-structs/classes.md)
