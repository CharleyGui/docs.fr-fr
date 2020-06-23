---
title: Effectuer des appels thread-safe aux contrôles
ms.date: 02/19/2019
description: Apprenez à implémenter le multithreading dans votre application en appelant des contrôles inter-threads de façon thread-safe.
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
ms.openlocfilehash: b5f4de7bd3d8d89de98dbe27e2dbf360763670d0
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904180"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Comment : effectuer des appels thread-safe à des contrôles Windows Forms

Le multithreading peut améliorer les performances des applications de Windows Forms, mais l’accès aux contrôles de Windows Forms n’est pas thread-safe par nature. Le multithreading peut exposer votre code à des bogues très sérieux et complexes. Au moins deux threads manipulant un contrôle peuvent forcer le contrôle dans un état incohérent et provoquer des conditions de concurrence, des blocages, des blocages et des blocages. Si vous implémentez le multithreading dans votre application, veillez à appeler les contrôles inter-threads de façon thread-safe. Pour plus d’informations, consultez [meilleures pratiques pour le threading managé](../../../standard/threading/managed-threading-best-practices.md).

Il existe deux façons d’appeler sans risque un contrôle Windows Forms à partir d’un thread qui n’a pas créé ce contrôle. Vous pouvez utiliser la <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> méthode pour appeler un délégué créé dans le thread principal, qui à son tour appelle le contrôle. Ou vous pouvez implémenter un <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> , qui utilise un modèle piloté par les événements pour séparer le travail effectué dans le thread d’arrière-plan de la création de rapports sur les résultats.

## <a name="unsafe-cross-thread-calls"></a>Appels inter-threads non sécurisés

Il est risqué d’appeler un contrôle directement à partir d’un thread qui ne l’a pas créé. L’extrait de code suivant illustre un appel non sécurisé au <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> contrôle. Le `Button1_Click` Gestionnaire d’événements crée un nouveau `WriteTextUnsafe` thread, qui définit directement la propriété du thread principal <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> .

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

Le débogueur Visual Studio détecte ces appels de threads non sécurisés en déclenchant un <xref:System.InvalidOperationException> avec le message, **opération inter-threads non valide. Contrôle «» accessible à partir d’un thread autre que le thread sur lequel il a été créé.** <xref:System.InvalidOperationException>Se produit toujours pour les appels inter-threads non sécurisés pendant le débogage de Visual Studio et peut se produire au moment de l’exécution de l’application. Vous devez résoudre le problème, mais vous pouvez désactiver l’exception en affectant <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> à la propriété la valeur `false` .

## <a name="safe-cross-thread-calls"></a>Appels inter-threads sécurisés

Les exemples de code suivants illustrent deux façons d’appeler sans risque un contrôle Windows Forms à partir d’un thread qui n’a pas créé ce dernier :

1. La <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> méthode, qui appelle un délégué du thread principal pour appeler le contrôle.
2. <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>Composant, qui offre un modèle piloté par les événements.

Dans les deux exemples, le thread d’arrière-plan se met en veille pendant une seconde pour simuler le travail effectué dans ce thread.

Vous pouvez générer et exécuter ces exemples comme des applications .NET Framework à partir de la ligne de commande C# ou Visual Basic. Pour plus d’informations, consultez génération à partir de la [ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [génération à partir de la ligne de commande (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

À compter de .NET Core 3,0, vous pouvez également générer et exécuter les exemples en tant qu’applications Windows .NET Core à partir d’un dossier qui contient un fichier projet .NET Core Windows Forms * \<folder name> . csproj* .

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Exemple : utilisation de la méthode Invoke avec un délégué

L’exemple suivant illustre un modèle permettant de garantir des appels thread-safe à un contrôle Windows Forms. Elle interroge la <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> propriété, qui compare l’ID de thread de création du contrôle à l’ID de thread appelant. Si les ID de thread sont identiques, il appelle le contrôle directement. Si les ID de thread sont différents, il appelle la <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> méthode avec un délégué du thread principal, qui effectue l’appel réel au contrôle.

Le `SafeCallDelegate` permet de définir la <xref:System.Windows.Forms.TextBox> propriété du contrôle <xref:System.Windows.Forms.TextBox.Text%2A> . La `WriteTextSafe` méthode interroge <xref:System.Windows.Forms.Control.InvokeRequired%2A> . Si <xref:System.Windows.Forms.Control.InvokeRequired%2A> retourne `true` , `WriteTextSafe` passe `SafeCallDelegate` à la <xref:System.Windows.Forms.Control.Invoke%2A> méthode pour effectuer l’appel réel au contrôle. Si <xref:System.Windows.Forms.Control.InvokeRequired%2A> retourne `false` , `WriteTextSafe` définit <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> directement. Le `Button1_Click` Gestionnaire d’événements crée le nouveau thread et exécute la `WriteTextSafe` méthode.

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Exemple : utilisation d’un gestionnaire d’événements BackgroundWorker

Un moyen simple d’implémenter le multithreading consiste à utiliser le <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> composant, qui utilise un modèle piloté par les événements. Le thread d’arrière-plan exécute l' <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> événement, qui n’interagit pas avec le thread principal. Le thread principal exécute les <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> gestionnaires d’événements et, qui peuvent appeler les contrôles du thread principal.

Pour effectuer un appel thread-safe à l’aide de <xref:System.ComponentModel.BackgroundWorker> , créez une méthode dans le thread d’arrière-plan pour effectuer le travail et liez-la à l' <xref:System.ComponentModel.BackgroundWorker.DoWork> événement. Créez une autre méthode dans le thread principal pour signaler les résultats du travail en arrière-plan et liez-le à l' <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> événement ou. Pour démarrer le thread d’arrière-plan, appelez <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType> .

L’exemple utilise le <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> Gestionnaire d’événements pour définir la <xref:System.Windows.Forms.TextBox> propriété du contrôle <xref:System.Windows.Forms.TextBox.Text%2A> . Pour obtenir un exemple d’utilisation de l' <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> événement, consultez <xref:System.ComponentModel.BackgroundWorker> .

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.BackgroundWorker>
- [Comment : exécuter une opération en arrière-plan](how-to-run-an-operation-in-the-background.md)
- [Comment : implémenter un formulaire qui utilise une opération d’arrière-plan](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Développez des contrôles de Windows Forms personnalisés avec le .NET Framework](developing-custom-windows-forms-controls.md)
