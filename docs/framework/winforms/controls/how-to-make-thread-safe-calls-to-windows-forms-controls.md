---
title: Faire des appels sans fil aux contrôles
ms.date: 02/19/2019
dev_langs:
- csharp
- vb
f1_keywords:
- EHInvalidOperation.WinForms.IllegalCrossThreadCall
helpviewer_keywords:
- thread safety [Windows Forms], calling controls [Windows Forms]
- calling controls [Windows Forms], thread safety [Windows Forms]
- CheckForIllegalCrossThreadCalls property [Windows Forms]
- Windows Forms controls [Windows Forms], multithreading
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], cross-thread calls
- controls [Windows Forms], multithreading
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
ms.openlocfilehash: 365b1acb693b9ff2be603a3e659ed8d846a7696a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142002"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Comment : Faire des appels sans fil vers les commandes de formulaires Windows

Multithreading peut améliorer les performances des applications Windows Forms, mais l’accès aux contrôles Windows Forms n’est pas intrinsèquement sans fil. Multithreading peut exposer votre code à des bogues très graves et complexes. Deux fils ou plus manipulant un contrôle peuvent forcer le contrôle dans un état incohérent et conduire à des conditions de course, des impasses, et des gels ou des pendaisons. Si vous implémentez la multithreading dans votre application, assurez-vous d’appeler des commandes de fil croisé d’une manière sans fil. Pour plus d’informations, voir [Managed threading best practices](../../../standard/threading/managed-threading-best-practices.md).

Il existe deux façons d’appeler en toute sécurité un contrôle des formulaires Windows à partir d’un thread qui n’a pas créé ce contrôle. Vous pouvez <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> utiliser la méthode pour appeler un délégué créé dans le thread principal, qui à son tour appelle le contrôle. Ou, vous pouvez <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>implémenter un , qui utilise un modèle axé sur les événements pour séparer les travaux effectués dans le thread de fond de rapports sur les résultats.

## <a name="unsafe-cross-thread-calls"></a>Appels croisés dangereux

Il est dangereux d’appeler un contrôle directement à partir d’un thread qui ne l’a pas créé. L’extrait de code suivant illustre un <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> appel dangereux au contrôle. Le `Button1_Click` gestionnaire d’événements crée un nouveau `WriteTextUnsafe` thread, qui définit directement la propriété du <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> thread principal.

```csharp
private void Button1_Click(object sender, EventArgs e)
{
    thread2 = new Thread(new ThreadStart(WriteTextUnsafe));
    thread2.Start();
}
private void WriteTextUnsafe()
{
    textBox1.Text = "This text was set unsafely.";
}
```

```vb
Private Sub Button1_Click(ByVal sender As Object, e As EventArgs) Handles Button1.Click
    Thread2 = New Thread(New ThreadStart(AddressOf WriteTextUnsafe))
    Thread2.Start()
End Sub

Private Sub WriteTextUnsafe()
    TextBox1.Text = "This text was set unsafely."
End Sub
```

Le debugger Visual Studio détecte ces appels <xref:System.InvalidOperationException> de thread dangereux en soulevant un avec le message, **opération Cross-thread non valide. Contrôle "" accessible à partir d’un thread autre que le fil sur qui il a été créé.** Le <xref:System.InvalidOperationException> se produit toujours pour les appels de fil croisé dangereux pendant le débogage Visual Studio, et peut se produire à l’heure d’exécution de l’application. Vous devez résoudre le problème, mais vous pouvez <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> désactiver `false`l’exception en fixant la propriété à .

## <a name="safe-cross-thread-calls"></a>Appels transversaux sûrs

Les exemples de code suivants démontrent deux façons d’appeler en toute sécurité un contrôle des formulaires Windows à partir d’un thread qui ne l’a pas créé :

1. La <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> méthode, qui appelle un délégué du fil principal pour appeler le contrôle.
2. Un <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> composant, qui offre un modèle axé sur l’événement.

Dans les deux exemples, le fil d’arrière-plan dort pendant une seconde pour simuler le travail effectué dans ce fil.

Vous pouvez créer et exécuter ces exemples sous forme d’applications cadres .NET de la ligne de commande C ou Visual Basic. Pour plus d’informations, voir [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [Build from the command line (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

En commençant par .NET Core 3.0, vous pouvez également construire et exécuter les exemples comme Windows .NET Core applications à partir d’un dossier qui a un nom de dossier .NET Core Windows Forms * \<>.csproj* fichier de projet.

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Exemple : Utilisez la méthode Invoke avec un délégué

L’exemple suivant montre un modèle pour assurer des appels sans fil vers un contrôle des formulaires Windows. Il interroge <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> la propriété, qui compare l’ID de fil de création du contrôle à l’ID de thread d’appel. Si les ID de fil sont les mêmes, il appelle le contrôle directement. Si les ID de fil sont <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> différents, il appelle la méthode avec un délégué du thread principal, ce qui rend l’appel réel au contrôle.

Le `SafeCallDelegate` permet <xref:System.Windows.Forms.TextBox> de définir <xref:System.Windows.Forms.TextBox.Text%2A> la propriété du contrôle. La `WriteTextSafe` méthode <xref:System.Windows.Forms.Control.InvokeRequired%2A>interroge . Si <xref:System.Windows.Forms.Control.InvokeRequired%2A> `true`les `WriteTextSafe` retours, passe la `SafeCallDelegate` <xref:System.Windows.Forms.Control.Invoke%2A> méthode pour faire l’appel réel au contrôle. Si <xref:System.Windows.Forms.Control.InvokeRequired%2A> `false`les `WriteTextSafe` retours , définit le <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> directement. Le `Button1_Click` gestionnaire d’événements crée `WriteTextSafe` le nouveau thread et exécute la méthode.

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Exemple : Utilisez un gestionnaire d’événements BackgroundWorker

Un moyen facile d’implémenter <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> la multithreading est avec le composant, qui utilise un modèle axé sur l’événement. Le fil d’arrière-plan exécute l’événement, <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> qui n’interagit pas avec le thread principal. Le fil principal <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> exécute les gestionnaires et d’événements, qui peuvent appeler les commandes du thread principal.

Pour faire un appel sans <xref:System.ComponentModel.BackgroundWorker>fil en utilisant, créer une méthode dans le <xref:System.ComponentModel.BackgroundWorker.DoWork> fil d’arrière-plan pour faire le travail, et lier à l’événement. Créez une autre méthode dans le thread principal pour signaler les <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> résultats du travail d’arrière-plan, et lier à l’événement ou à l’événement. Pour démarrer le fil <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>d’arrière-plan, appelez .

L’exemple <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> utilise le gestionnaire <xref:System.Windows.Forms.TextBox> d’événements pour définir la propriété du <xref:System.Windows.Forms.TextBox.Text%2A> contrôle. Par exemple en <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> utilisant <xref:System.ComponentModel.BackgroundWorker>l’événement, voir .

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.BackgroundWorker>
- [Comment : Exécuter une opération en arrière-plan](how-to-run-an-operation-in-the-background.md)
- [Comment : Mettre en œuvre un formulaire qui utilise une opération de fond](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Développer des contrôles Windows Forms personnalisés avec le cadre .NET](developing-custom-windows-forms-controls.md)
