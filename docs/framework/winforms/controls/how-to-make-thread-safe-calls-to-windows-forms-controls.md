---
title: 'Procédure : Effectuer des appels thread-safe à des contrôles Windows Forms'
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
ms.openlocfilehash: 78ad7b16d5220972a61848c0c80cd884afa842d9
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928615"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Procédure : Effectuer des appels thread-safe à des contrôles Windows Forms

Le multithreading peut améliorer les performances des applications de Windows Forms, mais l’accès aux contrôles de Windows Forms n’est pas thread-safe par nature. Le multithreading peut exposer votre code à des bogues très sérieux et complexes. Au moins deux threads manipulant un contrôle peuvent forcer le contrôle dans un état incohérent et provoquer des conditions de concurrence, des blocages, des blocages et des blocages. Si vous implémentez le multithreading dans votre application, veillez à appeler les contrôles inter-threads de façon thread-safe. Pour plus d’informations, consultez [meilleures pratiques pour le threading managé](../../../standard/threading/managed-threading-best-practices.md). 

Il existe deux façons d’appeler sans risque un contrôle Windows Forms à partir d’un thread qui n’a pas créé ce contrôle. Vous pouvez utiliser la <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> méthode pour appeler un délégué créé dans le thread principal, qui à son tour appelle le contrôle. Ou vous pouvez implémenter un <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, qui utilise un modèle piloté par les événements pour séparer le travail effectué dans le thread d’arrière-plan de la création de rapports sur les résultats. 

## <a name="unsafe-cross-thread-calls"></a>Appels inter-threads non sécurisés

Il est risqué d’appeler un contrôle directement à partir d’un thread qui ne l’a pas créé. L’extrait de code suivant illustre un appel non sécurisé au <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> contrôle. Le `Button1_Click` gestionnaire d’événements crée un `WriteTextUnsafe` nouveau thread, qui définit directement la propriété <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> du thread principal. 

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

Le débogueur Visual Studio détecte ces appels de threads non sécurisés en <xref:System.InvalidOperationException> déclenchant un avec **le message, opération inter-threads non valide. Contrôle «» accessible à partir d’un thread autre que le thread sur lequel il a été créé.** Se <xref:System.InvalidOperationException> produit toujours pour les appels inter-threads non sécurisés pendant le débogage de Visual Studio et peut se produire au moment de l’exécution de l’application. Vous devez résoudre le problème, mais vous pouvez désactiver l’exception en affectant <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> à `false`la propriété la valeur.

## <a name="safe-cross-thread-calls"></a>Appels inter-threads sécurisés 

Les exemples de code suivants illustrent deux façons d’appeler sans risque un contrôle Windows Forms à partir d’un thread qui n’a pas créé ce dernier : 

1. La <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> méthode, qui appelle un délégué du thread principal pour appeler le contrôle. 
2. <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> Composant, qui offre un modèle piloté par les événements. 

Dans les deux exemples, le thread d’arrière-plan se met en veille pendant une seconde pour simuler le travail effectué dans ce thread. 

Vous pouvez générer et exécuter ces exemples comme des applications .NET Framework à C# partir de la ligne de commande ou Visual Basic. Pour plus d’informations, consultez génération à partir de la [ligne de commande avec CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [Build à partir de la ligne de commande (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

À compter de .net Core 3,0, vous pouvez également générer et exécuter les exemples en tant qu’applications Windows .net core à partir d’un dossier qui a un  *\<nom de dossier* Windows Forms .net Core > fichier de projet. csproj. 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Exemple : Utiliser la méthode Invoke avec un délégué

L’exemple suivant illustre un modèle permettant de garantir des appels thread-safe à un contrôle Windows Forms. Elle interroge la <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> propriété, qui compare l’ID de thread de création du contrôle à l’ID de thread appelant. Si les ID de thread sont identiques, il appelle le contrôle directement. Si les ID de thread sont différents, il appelle <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> la méthode avec un délégué du thread principal, qui effectue l’appel réel au contrôle.

Le `SafeCallDelegate` permet de définir <xref:System.Windows.Forms.TextBox> la propriété <xref:System.Windows.Forms.TextBox.Text%2A> du contrôle. La `WriteTextSafe` méthode interroge <xref:System.Windows.Forms.Control.InvokeRequired%2A>. Si <xref:System.Windows.Forms.Control.InvokeRequired%2A> retourne `true`, passe`WriteTextSafe` àla<xref:System.Windows.Forms.Control.Invoke%2A> méthode pour effectuer l’appel réel au contrôle. `SafeCallDelegate` Si <xref:System.Windows.Forms.Control.InvokeRequired%2A> retourne `false`, `WriteTextSafe` définit directement.<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> Le `Button1_Click` gestionnaire d’événements crée le nouveau thread et exécute `WriteTextSafe` la méthode. 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Exemple : Utiliser un gestionnaire d’événements BackgroundWorker

Un moyen simple d’implémenter le multithreading consiste <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> à utiliser le composant, qui utilise un modèle piloté par les événements. Le thread d’arrière- <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> plan exécute l’événement, qui n’interagit pas avec le thread principal. Le thread principal exécute les <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> gestionnaires <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> d’événements et, qui peuvent appeler les contrôles du thread principal.

Pour effectuer un appel thread-safe à l' <xref:System.ComponentModel.BackgroundWorker>aide de, créez une méthode dans le thread d’arrière-plan pour effectuer le travail et <xref:System.ComponentModel.BackgroundWorker.DoWork> liez-la à l’événement. Créez une autre méthode dans le thread principal pour signaler les résultats du travail en arrière-plan et liez- <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> le <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> à l’événement ou. Pour démarrer le thread d’arrière- <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>plan, appelez. 

L’exemple utilise le <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> gestionnaire d’événements pour définir <xref:System.Windows.Forms.TextBox> la propriété <xref:System.Windows.Forms.TextBox.Text%2A> du contrôle. Pour obtenir un exemple d' <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> utilisation de l' <xref:System.ComponentModel.BackgroundWorker>événement, consultez. 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.BackgroundWorker>
- [Guide pratique : Exécuter une opération en arrière-plan](how-to-run-an-operation-in-the-background.md)
- [Guide pratique pour Implémenter un formulaire qui utilise une opération d’arrière-plan](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Développez des contrôles de Windows Forms personnalisés avec le .NET Framework](developing-custom-windows-forms-controls.md)
