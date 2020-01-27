---
title: Afficher des liens de style Web avec le contrôle RichTextBox
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
ms.openlocfilehash: 78a07a250744018f121b03f2973b1661ed6bf764
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745528"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="11552-102">Comment : afficher des liens de style Web avec le contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11552-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="11552-103">Le contrôle Windows Forms <xref:System.Windows.Forms.RichTextBox> peut afficher des liens Web en couleur et soulignés.</span><span class="sxs-lookup"><span data-stu-id="11552-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="11552-104">Vous pouvez écrire du code qui ouvre une fenêtre de navigateur qui affiche le site Web spécifié dans le texte du lien lorsque l’utilisateur clique sur le lien.</span><span class="sxs-lookup"><span data-stu-id="11552-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="11552-105">Pour créer un lien vers une page Web avec le contrôle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="11552-105">To link to a Web page with the RichTextBox control</span></span>

1. <span data-ttu-id="11552-106">Affectez <xref:System.Windows.Forms.RichTextBox.Text%2A> à la propriété une chaîne qui contient une URL valide (par exemple,"http://www.microsoft.com/").</span><span class="sxs-lookup"><span data-stu-id="11552-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "http://www.microsoft.com/").</span></span>

2. <span data-ttu-id="11552-107">Assurez-vous que la propriété <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> est définie sur `true` (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="11552-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>

3. <span data-ttu-id="11552-108">Créez une nouvelle instance globale de l’objet <xref:System.Diagnostics.Process>.</span><span class="sxs-lookup"><span data-stu-id="11552-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>

4. <span data-ttu-id="11552-109">Écrivez un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.RichTextBox.LinkClicked> qui envoie le texte souhaité au navigateur.</span><span class="sxs-lookup"><span data-stu-id="11552-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>

    <span data-ttu-id="11552-110">Dans l’exemple ci-dessous, l’événement <xref:System.Windows.Forms.RichTextBox.LinkClicked> ouvre une instance d’Internet Explorer à l’URL spécifiée dans la propriété <xref:System.Windows.Forms.RichTextBox.Text%2A> du contrôle <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="11552-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="11552-111">Cet exemple suppose un formulaire avec un contrôle <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="11552-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="11552-112">Lors de l’appel de la méthode <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>, vous rencontrerez une exception <xref:System.Security.SecurityException> si vous exécutez le code dans un contexte de confiance partielle en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="11552-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="11552-113">Pour plus d'informations, consultez [Code Access Security Basics](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="11552-113">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

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

    <span data-ttu-id="11552-114">(Visuel C++) Vous devez initialiser le processus `p`, ce que vous pouvez faire en incluant l’instruction suivante dans le constructeur de votre formulaire :</span><span class="sxs-lookup"><span data-stu-id="11552-114">(Visual C++) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    <span data-ttu-id="11552-115">(Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="11552-115">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

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

    <span data-ttu-id="11552-116">Il est important d’arrêter immédiatement le processus que vous avez créé une fois que vous avez fini de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="11552-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="11552-117">En vous référant au code présenté ci-dessus, votre code pour arrêter le processus peut se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="11552-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="11552-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11552-118">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="11552-119">RichTextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="11552-119">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="11552-120">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11552-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
