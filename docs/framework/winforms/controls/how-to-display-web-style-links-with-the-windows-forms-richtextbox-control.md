---
title: 'Procédure : afficher des liens de style web avec le contrôle RichTextBox Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
ms.openlocfilehash: ce71981f7b233d3e168689c766128646eed3e981
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046187"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>Procédure : afficher des liens de style web avec le contrôle RichTextBox Windows Forms

Le contrôle <xref:System.Windows.Forms.RichTextBox> Windows Forms peut afficher des liens Web en couleur et soulignés. Vous pouvez écrire du code qui ouvre une fenêtre de navigateur qui affiche le site Web spécifié dans le texte du lien lorsque l’utilisateur clique sur le lien.

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>Pour créer un lien vers une page Web avec le contrôle RichTextBox

1. Affectez <xref:System.Windows.Forms.RichTextBox.Text%2A> à la propriété une chaîne qui contient une URL valide (par exemple,"http://www.microsoft.com/").

2. Assurez- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> vous que la propriété `true` a la valeur (valeur par défaut).

3. Créez une nouvelle instance globale de l' <xref:System.Diagnostics.Process> objet.

4. Écrivez un gestionnaire d’événements pour <xref:System.Windows.Forms.RichTextBox.LinkClicked> l’événement qui envoie le texte souhaité au navigateur.

    Dans l’exemple ci-dessous <xref:System.Windows.Forms.RichTextBox.LinkClicked> , l’événement ouvre une instance d’Internet Explorer à l’URL spécifiée <xref:System.Windows.Forms.RichTextBox.Text%2A> dans la propriété <xref:System.Windows.Forms.RichTextBox> du contrôle. Cet exemple suppose un formulaire avec un <xref:System.Windows.Forms.RichTextBox> contrôle.

    > [!IMPORTANT]
    > Lors de l' <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> appel de la méthode, vous <xref:System.Security.SecurityException> rencontrerez une exception si vous exécutez le code dans un contexte de confiance partielle en raison de privilèges insuffisants. Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../misc/code-access-security-basics.md).

    ```vb
    Public p As New System.Diagnostics.Process
    Private Sub RichTextBox1_LinkClicked _
       (ByVal sender As Object, ByVal e As _
       System.Windows.Forms.LinkClickedEventArgs) _
       Handles RichTextBox1.LinkClicked
          ' Call Process.Start method to open a browser
          ' with link text as URL.
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)
    End Sub
    ```

    ```csharp
    public System.Diagnostics.Process p = new System.Diagnostics.Process();

    private void richTextBox1_LinkClicked(object sender,
    System.Windows.Forms.LinkClickedEventArgs e)
    {
       // Call Process.Start method to open a browser
       // with link text as URL.
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);
    }
    ```

    ```cpp
    public:
       System::Diagnostics::Process ^ p;

    private:
       void richTextBox1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkClickedEventArgs ^  e)
       {
          // Call Process.Start method to open a browser
          // with link text as URL.
          p = System::Diagnostics::Process::Start("IExplore.exe",
             e->LinkText);
       }
    ```

    (Visuel C++) Vous devez initialiser le `p`processus, ce que vous pouvez faire en incluant l’instruction suivante dans le constructeur de votre formulaire:

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    (Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.

    ```csharp
    this.richTextBox1.LinkClicked += new
       System.Windows.Forms.LinkClickedEventHandler
       (this.richTextBox1_LinkClicked);
    ```

    ```cpp
    this->richTextBox1->LinkClicked += gcnew
       System::Windows::Forms::LinkClickedEventHandler
       (this, &Form1::richTextBox1_LinkClicked);
    ```

    Il est important d’arrêter immédiatement le processus que vous avez créé une fois que vous avez fini de l’utiliser. En vous référant au code présenté ci-dessus, votre code pour arrêter le processus peut se présenter comme suit:

    ```vb
    Public Sub StopWebProcess()
       p.Kill()
    End Sub
    ```

    ```csharp
    public void StopWebProcess()
    {
       p.Kill();
    }
    ```

    ```cpp
    public: void StopWebProcess()
    {
       p->Kill();
    }
    ```

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, contrôle](richtextbox-control-windows-forms.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
