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
ms.openlocfilehash: 05d9ad4766584b59cca7c31f49b737d4696a9921
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053538"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="b23ed-102">Procédure : afficher des liens de style web avec le contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b23ed-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="b23ed-103">Les formulaires Windows <xref:System.Windows.Forms.RichTextBox> contrôle peut afficher des liens Web en couleur et souligné.</span><span class="sxs-lookup"><span data-stu-id="b23ed-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="b23ed-104">Vous pouvez écrire du code qui ouvre une fenêtre de navigateur affichant le site Web spécifié dans le texte du lien lorsque l’utilisateur clique sur le lien.</span><span class="sxs-lookup"><span data-stu-id="b23ed-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="b23ed-105">Pour lier à une page Web avec le contrôle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="b23ed-105">To link to a Web page with the RichTextBox control</span></span>  
  
1. <span data-ttu-id="b23ed-106">Définir le <xref:System.Windows.Forms.RichTextBox.Text%2A> en une chaîne qui inclut une URL valide (par exemple, « http://www.microsoft.com/»).</span><span class="sxs-lookup"><span data-stu-id="b23ed-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "http://www.microsoft.com/").</span></span>  
  
2. <span data-ttu-id="b23ed-107">Assurez-vous que le <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> propriété est définie sur `true` (la valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="b23ed-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>  
  
3. <span data-ttu-id="b23ed-108">Créer une nouvelle instance globale de la <xref:System.Diagnostics.Process> objet.</span><span class="sxs-lookup"><span data-stu-id="b23ed-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>  
  
4. <span data-ttu-id="b23ed-109">Écrire un gestionnaire d’événements pour le <xref:System.Windows.Forms.RichTextBox.LinkClicked> événement qui envoie le navigateur le texte souhaité.</span><span class="sxs-lookup"><span data-stu-id="b23ed-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>  
  
     <span data-ttu-id="b23ed-110">Dans l’exemple ci-dessous, le <xref:System.Windows.Forms.RichTextBox.LinkClicked> événement ouvre une instance d’Internet Explorer à l’URL spécifiée dans le <xref:System.Windows.Forms.RichTextBox.Text%2A> propriété de la <xref:System.Windows.Forms.RichTextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="b23ed-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="b23ed-111">Cet exemple suppose un formulaire avec un <xref:System.Windows.Forms.RichTextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="b23ed-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b23ed-112">Dans l’appel la <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> (méthode), vous rencontrerez un <xref:System.Security.SecurityException> exception si vous exécutez le code dans un contexte de confiance partielle en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="b23ed-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="b23ed-113">Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="b23ed-113">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
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
  
     <span data-ttu-id="b23ed-114">(Visual C++) Vous devez initialiser le processus `p`, ce que vous pouvez faire en incluant l’instruction suivante dans le constructeur de votre formulaire :</span><span class="sxs-lookup"><span data-stu-id="b23ed-114">(Visual C++) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     <span data-ttu-id="b23ed-115">(Visual C#, Visual C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="b23ed-115">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="b23ed-116">Il est important d’arrêter immédiatement le processus que vous avez créé une fois que vous avez fini de travailler avec lui.</span><span class="sxs-lookup"><span data-stu-id="b23ed-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="b23ed-117">Qui fait référence au code présenté ci-dessus, votre code pour arrêter le processus peut ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="b23ed-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b23ed-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b23ed-118">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="b23ed-119">RichTextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="b23ed-119">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="b23ed-120">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b23ed-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
