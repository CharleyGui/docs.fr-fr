---
title: Lien vers un objet ou une page Web à l’aide du contrôle LinkLabel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Windows Forms, linking to objects
- Web page link control
- linking [Windows Forms], to other forms
- Windows Forms, linking to Web pages
- links [Windows Forms], to other forms
- LinkLabel control [Windows Forms], linking to object or Web page
- LinkLabel control [Windows Forms], examples
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
ms.openlocfilehash: 1669a9d6aba39b02d228c735701ca4e31c8f8291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745207"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a><span data-ttu-id="8dacf-102">Comment : créer un lien vers un objet ou une page Web à l'aide du contrôle LinkLabel Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8dacf-102">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>

<span data-ttu-id="8dacf-103">Le contrôle Windows Forms <xref:System.Windows.Forms.LinkLabel> vous permet de créer des liens de style Web sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="8dacf-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to create Web-style links on your form.</span></span> <span data-ttu-id="8dacf-104">Lorsque vous cliquez sur le lien, vous pouvez modifier sa couleur pour indiquer que le lien a été visité.</span><span class="sxs-lookup"><span data-stu-id="8dacf-104">When the link is clicked, you can change its color to indicate the link has been visited.</span></span> <span data-ttu-id="8dacf-105">Pour plus d’informations sur la modification de la couleur, consultez [Comment : modifier l’apparence du contrôle Windows Forms LinkLabel](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span><span class="sxs-lookup"><span data-stu-id="8dacf-105">For more information on changing the color, see [How to: Change the Appearance of the Windows Forms LinkLabel Control](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span></span>

## <a name="linking-to-another-form"></a><span data-ttu-id="8dacf-106">Lier à un autre formulaire</span><span class="sxs-lookup"><span data-stu-id="8dacf-106">Linking to Another Form</span></span>

#### <a name="to-link-to-another-form-with-a-linklabel-control"></a><span data-ttu-id="8dacf-107">Pour créer un lien vers un autre formulaire avec un contrôle LinkLabel</span><span class="sxs-lookup"><span data-stu-id="8dacf-107">To link to another form with a LinkLabel control</span></span>

1. <span data-ttu-id="8dacf-108">Affectez à la propriété <xref:System.Windows.Forms.LinkLabel.Text%2A> une légende appropriée.</span><span class="sxs-lookup"><span data-stu-id="8dacf-108">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>

2. <span data-ttu-id="8dacf-109">Définissez la propriété <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> pour déterminer la partie de la légende qui sera indiquée comme lien.</span><span class="sxs-lookup"><span data-stu-id="8dacf-109">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span> <span data-ttu-id="8dacf-110">La façon dont il est indiqué dépend des propriétés relatives à l’apparence de l’étiquette de lien.</span><span class="sxs-lookup"><span data-stu-id="8dacf-110">How it is indicated depends on the appearance-related properties of the link label.</span></span> <span data-ttu-id="8dacf-111">La valeur <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> est représentée par un objet <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> contenant deux nombres, la position du caractère de départ et le nombre de caractères.</span><span class="sxs-lookup"><span data-stu-id="8dacf-111">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented by a <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> object containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="8dacf-112">La propriété <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> peut être définie dans le Fenêtre Propriétés ou dans le code d’une manière similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="8dacf-112">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property can be set in the Properties window or in code in a manner similar to the following:</span></span>

    ```vb
    ' In this code example, the link area has been set to begin
    ' at the first character and extend for eight characters.
    ' You may need to modify this based on the text entered in Step 1.
    LinkLabel1.LinkArea = New LinkArea(0, 8)
    ```

    ```csharp
    // In this code example, the link area has been set to begin
    // at the first character and extend for eight characters.
    // You may need to modify this based on the text entered in Step 1.
    linkLabel1.LinkArea = new LinkArea(0,8);
    ```

    ```cpp
    // In this code example, the link area has been set to begin
    // at the first character and extend for eight characters.
    // You may need to modify this based on the text entered in Step 1.
    linkLabel1->LinkArea = LinkArea(0,8);
    ```

3. <span data-ttu-id="8dacf-113">Dans le gestionnaire d’événements <xref:System.Windows.Forms.LinkLabel.LinkClicked>, appelez la méthode <xref:System.Windows.Forms.Form.Show%2A> pour ouvrir un autre formulaire dans le projet, puis affectez à la propriété <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="8dacf-113">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, invoke the <xref:System.Windows.Forms.Form.Show%2A> method to open another form in the project, and set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8dacf-114">Une instance de la classe <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> contient une référence au contrôle <xref:System.Windows.Forms.LinkLabel> sur lequel l’utilisateur a cliqué. il n’est donc pas nécessaire d’effectuer un cast de l’objet `sender`.</span><span class="sxs-lookup"><span data-stu-id="8dacf-114">An instance of the <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> class carries a reference to the <xref:System.Windows.Forms.LinkLabel> control that was clicked, so there is no need to cast the `sender` object.</span></span>

    ```vb
    Protected Sub LinkLabel1_LinkClicked(ByVal Sender As System.Object, _
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _
       Handles LinkLabel1.LinkClicked
       ' Show another form.
       Dim f2 As New Form()
       f2.Show
       LinkLabel1.LinkVisited = True
    End Sub
    ```

    ```csharp
    protected void linkLabel1_LinkClicked(object sender, System. Windows.Forms.LinkLabelLinkClickedEventArgs e)
    {
       // Show another form.
       Form f2 = new Form();
       f2.Show();
       linkLabel1.LinkVisited = true;
    }
    ```

    ```cpp
    private:
       void linkLabel1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)
       {
          // Show another form.
          Form ^ f2 = new Form();
          f2->Show();
          linkLabel1->LinkVisited = true;
       }
    ```

## <a name="linking-to-a-web-page"></a><span data-ttu-id="8dacf-115">Liaison à une page Web</span><span class="sxs-lookup"><span data-stu-id="8dacf-115">Linking to a Web Page</span></span>

<span data-ttu-id="8dacf-116">Le contrôle <xref:System.Windows.Forms.LinkLabel> peut également être utilisé pour afficher une page Web avec le navigateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8dacf-116">The <xref:System.Windows.Forms.LinkLabel> control can also be used to display a Web page with the default browser.</span></span>

#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a><span data-ttu-id="8dacf-117">Pour démarrer Internet Explorer et établir un lien vers une page Web avec un contrôle LinkLabel</span><span class="sxs-lookup"><span data-stu-id="8dacf-117">To start Internet Explorer and link to a Web page with a LinkLabel control</span></span>

1. <span data-ttu-id="8dacf-118">Affectez à la propriété <xref:System.Windows.Forms.LinkLabel.Text%2A> une légende appropriée.</span><span class="sxs-lookup"><span data-stu-id="8dacf-118">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>

2. <span data-ttu-id="8dacf-119">Définissez la propriété <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> pour déterminer la partie de la légende qui sera indiquée comme lien.</span><span class="sxs-lookup"><span data-stu-id="8dacf-119">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>

3. <span data-ttu-id="8dacf-120">Dans le gestionnaire d’événements <xref:System.Windows.Forms.LinkLabel.LinkClicked>, au milieu d’un bloc de gestion des exceptions, appelez une deuxième procédure qui affecte à la propriété <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> la valeur `true` et utilise la méthode <xref:System.Diagnostics.Process.Start%2A> pour démarrer le navigateur par défaut avec une URL.</span><span class="sxs-lookup"><span data-stu-id="8dacf-120">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, in the midst of an exception-handling block, call a second procedure that sets the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true` and uses the <xref:System.Diagnostics.Process.Start%2A> method to start the default browser with a URL.</span></span> <span data-ttu-id="8dacf-121">Pour utiliser la méthode <xref:System.Diagnostics.Process.Start%2A> vous devez ajouter une référence à l’espace de noms <xref:System.Diagnostics?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8dacf-121">To use the <xref:System.Diagnostics.Process.Start%2A> method you need to add a reference to the <xref:System.Diagnostics?displayProperty=nameWithType> namespace.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="8dacf-122">Si le code ci-dessous est exécuté dans un environnement de confiance partielle (par exemple, sur un lecteur partagé), le compilateur JIT échoue lorsque la méthode `VisitLink` est appelée.</span><span class="sxs-lookup"><span data-stu-id="8dacf-122">If the code below is run in a partial-trust environment (such as on a shared drive), the JIT compiler fails when the `VisitLink` method is called.</span></span> <span data-ttu-id="8dacf-123">L’instruction `System.Diagnostics.Process.Start` provoque une demande de liaison qui échoue.</span><span class="sxs-lookup"><span data-stu-id="8dacf-123">The `System.Diagnostics.Process.Start` statement causes a link demand that fails.</span></span> <span data-ttu-id="8dacf-124">En interceptant l’exception lorsque la méthode `VisitLink` est appelée, le code ci-dessous garantit que si le compilateur JIT échoue, l’erreur est gérée correctement.</span><span class="sxs-lookup"><span data-stu-id="8dacf-124">By catching the exception when the `VisitLink` method is called, the code below ensures that if the JIT compiler fails, the error is handled gracefully.</span></span>

    ```vb
    Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, _
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _
       Handles LinkLabel1.LinkClicked
       Try
          VisitLink()
       Catch ex As Exception
          ' The error message
          MessageBox.Show("Unable to open link that was clicked.")
       End Try
    End Sub

    Sub VisitLink()
       ' Change the color of the link text by setting LinkVisited
       ' to True.
       LinkLabel1.LinkVisited = True
       ' Call the Process.Start method to open the default browser
       ' with a URL:
       System.Diagnostics.Process.Start("http://www.microsoft.com")
    End Sub
    ```

    ```csharp
    private void linkLabel1_LinkClicked(object sender, System.Windows.Forms.LinkLabelLinkClickedEventArgs e)
    {
       try
       {
          VisitLink();
       }
       catch (Exception ex )
       {
          MessageBox.Show("Unable to open link that was clicked.");
       }
    }

    private void VisitLink()
    {
       // Change the color of the link text by setting LinkVisited
       // to true.
       linkLabel1.LinkVisited = true;
       //Call the Process.Start method to open the default browser
       //with a URL:
       System.Diagnostics.Process.Start("http://www.microsoft.com");
    }
    ```

    ```cpp
    private:
       void linkLabel1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)
       {
          try
          {
             VisitLink();
          }
          catch (Exception ^ ex)
          {
             MessageBox::Show("Unable to open link that was clicked.");
          }
       }
    private:
       void VisitLink()
       {
          // Change the color of the link text by setting LinkVisited
          // to true.
          linkLabel1->LinkVisited = true;
          // Call the Process.Start method to open the default browser
          // with a URL:
          System::Diagnostics::Process::Start("http://www.microsoft.com");
       }
    ```

## <a name="see-also"></a><span data-ttu-id="8dacf-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8dacf-125">See also</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8dacf-126">Vue d'ensemble du contrôle LinkLabel</span><span class="sxs-lookup"><span data-stu-id="8dacf-126">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="8dacf-127">Guide pratique pour modifier l'apparence du contrôle LinkLabel Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8dacf-127">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [<span data-ttu-id="8dacf-128">LinkLabel, contrôle</span><span class="sxs-lookup"><span data-stu-id="8dacf-128">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
