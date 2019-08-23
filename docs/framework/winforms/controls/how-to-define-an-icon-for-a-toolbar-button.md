---
title: 'Procédure : définir une icône pour un bouton de barre d’outils'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- buttons [Windows Forms], icons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: 84db98b4-8566-49ce-b2c8-1fd66a5eb3a0
ms.openlocfilehash: 2b85f734a5f8b31531cfe48f87681d98304db09b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929629"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a><span data-ttu-id="b7c5e-102">Procédure : définir une icône pour un bouton de barre d’outils</span><span class="sxs-lookup"><span data-stu-id="b7c5e-102">How to: Define an Icon for a ToolBar Button</span></span>
> [!NOTE]
> <span data-ttu-id="b7c5e-103">Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="b7c5e-104"><xref:System.Windows.Forms.ToolBar>les boutons peuvent afficher des icônes pour faciliter leur identification par les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="b7c5e-105">Pour ce faire, il suffit d’ajouter des <xref:System.Windows.Forms.ToolBar> images au composant [ImageList](imagelist-component-windows-forms.md) , puis d' <xref:System.Windows.Forms.ImageList> associer le composant au contrôle.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-105">This is achieved through adding images to the [ImageList Component](imagelist-component-windows-forms.md) component and then associating the <xref:System.Windows.Forms.ImageList> component with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a><span data-ttu-id="b7c5e-106">Pour définir par programmation une icône pour un bouton de barre d’outils</span><span class="sxs-lookup"><span data-stu-id="b7c5e-106">To set an icon for a toolbar button programmatically</span></span>  
  
1. <span data-ttu-id="b7c5e-107">Dans une procédure, instanciez <xref:System.Windows.Forms.ImageList> un composant et <xref:System.Windows.Forms.ToolBar> un contrôle.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-107">In a procedure, instantiate an <xref:System.Windows.Forms.ImageList> component and a <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2. <span data-ttu-id="b7c5e-108">Dans la même procédure, assignez une image <xref:System.Windows.Forms.ImageList> au composant.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-108">In the same procedure, assign an image to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
3. <span data-ttu-id="b7c5e-109">Dans la même procédure, assignez le <xref:System.Windows.Forms.ImageList> contrôle <xref:System.Windows.Forms.ToolBar> au contrôle et assignez la <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> propriété des boutons de la barre d’outils individuels.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-109">In the same procedure, assign the <xref:System.Windows.Forms.ImageList> control to the <xref:System.Windows.Forms.ToolBar> control and assign the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of the individual toolbar buttons.</span></span>  
  
     <span data-ttu-id="b7c5e-110">Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’image est le dossier **Mes documents** .</span><span class="sxs-lookup"><span data-stu-id="b7c5e-110">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="b7c5e-111">En effet, vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-111">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="b7c5e-112">Cela permet également aux utilisateurs avec des niveaux d’accès minimum au système d’exécuter l’application en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-112">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="b7c5e-113">L’exemple ci-dessous suppose qu’un formulaire <xref:System.Windows.Forms.PictureBox> avec un contrôle a déjà été ajouté.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-113">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
     <span data-ttu-id="b7c5e-114">En suivant les étapes ci-dessus, vous devez avoir un code écrit similaire à celui qui est affiché ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-114">Following the steps above, you should have written code similar to that displayed below.</span></span>  
  
    ```vb  
    Public Sub InitializeMyToolBar()  
    ' Instantiate an ImageList component and a ToolBar control.  
       Dim ToolBar1 as New ToolBar  
       Dim ImageList1 as New ImageList  
    ' Assign an image to the ImageList component.  
    ' You should replace the bold image  
    ' in the sample below with an icon of your own choosing.  
       Dim myImage As System.Drawing.Image = _   
          Image.FromFile Image.FromFile _  
          (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.Personal) _  
          & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    ' Create a ToolBarButton.  
       Dim ToolBarButton1 As New ToolBarButton()  
    ' Add the ToolBarButton to the ToolBar.  
       ToolBar1.Buttons.Add(toolBarButton1)  
    ' Assign an ImageList to the ToolBar.  
       ToolBar1.ImageList = ImageList1  
    ' Assign the ImageIndex property of the ToolBarButton.  
       ToolBarButton1.ImageIndex = 0  
    End Sub  
    ```  
  
    ```csharp  
    public void InitializeMyToolBar()  
    {  
       // Instantiate an ImageList component and a ToolBar control.  
       ToolBar toolBar1 = new  ToolBar();   
       ImageList imageList1 = new ImageList();  
       // Assign an image to the ImageList component.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       Image myImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
       // Create a ToolBarButton.  
       ToolBarButton toolBarButton1 = new ToolBarButton();  
       // Add the ToolBarButton to the ToolBar.  
       toolBar1.Buttons.Add(toolBarButton1);  
       // Assign an ImageList to the ToolBar.  
       toolBar1.ImageList = imageList1;  
       // Assign ImageIndex property of the ToolBarButton.  
       toolBarButton1.ImageIndex = 0;  
    }  
    ```  
  
    ```cpp  
    public:  
       void InitializeMyToolBar()  
       {  
          // Instantiate an ImageList component and a ToolBar control.  
          ToolBar ^ toolBar1 = gcnew  ToolBar();   
          ImageList ^ imageList1 = gcnew ImageList();  
          // Assign an image to the ImageList component.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          Image ^ myImage = Image::FromFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
          // Create a ToolBarButton.  
          ToolBarButton ^ toolBarButton1 = gcnew ToolBarButton();  
          // Add the ToolBarButton to the ToolBar.  
          toolBar1->Buttons->Add(toolBarButton1);  
          // Assign an ImageList to the ToolBar.  
          toolBar1->ImageList = imageList1;  
          // Assign ImageIndex property of the ToolBarButton.  
          toolBarButton1->ImageIndex = 0;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b7c5e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7c5e-115">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="b7c5e-116">Guide pratique pour Déclencher des événements de menu pour les boutons de barre d’outils</span><span class="sxs-lookup"><span data-stu-id="b7c5e-116">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="b7c5e-117">ToolBar, contrôle</span><span class="sxs-lookup"><span data-stu-id="b7c5e-117">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="b7c5e-118">ImageList, composant</span><span class="sxs-lookup"><span data-stu-id="b7c5e-118">ImageList Component</span></span>](imagelist-component-windows-forms.md)
