---
title: 'Procédure : organiser les formulaires enfants MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
ms.openlocfilehash: 7e4d5a80961ae37951251dffa30cb8e75b20be27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955117"
---
# <a name="how-to-arrange-mdi-child-forms"></a><span data-ttu-id="fbd33-102">Procédure : organiser les formulaires enfants MDI</span><span class="sxs-lookup"><span data-stu-id="fbd33-102">How to: Arrange MDI Child Forms</span></span>
<span data-ttu-id="fbd33-103">Les applications comportent souvent des commandes de menu qui permettent de disposer en mosaïque ou en cascade les formulaires MDI enfants ouverts, ou encore de les réorganiser.</span><span class="sxs-lookup"><span data-stu-id="fbd33-103">Often, applications will have menu commands for actions such as Tile, Cascade, and Arrange, which control the layout of the open MDI child forms.</span></span> <span data-ttu-id="fbd33-104">Vous pouvez utiliser la méthode <xref:System.Windows.Forms.Form.LayoutMdi%2A> avec l'une des valeurs de l'énumération <xref:System.Windows.Forms.MdiLayout> pour réorganiser les formulaires enfants dans un formulaire MDI parent.</span><span class="sxs-lookup"><span data-stu-id="fbd33-104">You can use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method with one of the <xref:System.Windows.Forms.MdiLayout> enumeration values to rearrange the child forms in an MDI parent form.</span></span>  
  
 <span data-ttu-id="fbd33-105">Les valeurs de l'énumération <xref:System.Windows.Forms.MdiLayout> permettent d'afficher des formulaires enfants en cascade, en mosaïque horizontale ou verticale, ou sous forme d'icônes de formulaires enfants disposées dans la partie inférieure du formulaire MDI.</span><span class="sxs-lookup"><span data-stu-id="fbd33-105">The <xref:System.Windows.Forms.MdiLayout> enumeration values display child forms as cascading, as horizontally or vertically tiled, or as child form icons arranged along the lower portion of the MDI form.</span></span> <span data-ttu-id="fbd33-106">Ces valeurs ont le même effet que les commandes Windows en **cascade**, **afficher les fenêtres côte à**côte, afficher les fenêtres **empilées**et **afficher le bureau**, respectivement.</span><span class="sxs-lookup"><span data-stu-id="fbd33-106">These values have the same effect as the Windows commands **Cascade windows**, **Show windows side by side**, **Show windows stacked**, and **Show the desktop**, respectively.</span></span>  
  
 <span data-ttu-id="fbd33-107">Ces méthodes sont souvent utilisées en tant que gestionnaires d'événements appelés par l'événement <xref:System.Windows.Forms.Control.Click> d'un élément de menu.</span><span class="sxs-lookup"><span data-stu-id="fbd33-107">Often, these methods are used as the event handlers called by a menu item's <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="fbd33-108">Ainsi, un élément de menu présentant le texte « Cascade » peut produire l'effet souhaité dans les fenêtres MDI enfants.</span><span class="sxs-lookup"><span data-stu-id="fbd33-108">In this way, a menu item with the text "Cascade Windows" can have the desired effect on the MDI child windows.</span></span>  
  
### <a name="to-arrange-child-forms"></a><span data-ttu-id="fbd33-109">Pour réorganiser les formulaires enfants</span><span class="sxs-lookup"><span data-stu-id="fbd33-109">To arrange child forms</span></span>  
  
1. <span data-ttu-id="fbd33-110">Dans une méthode, utilisez la méthode <xref:System.Windows.Forms.Form.LayoutMdi%2A> pour définir l'énumération <xref:System.Windows.Forms.MdiLayout> pour le formulaire MDI parent.</span><span class="sxs-lookup"><span data-stu-id="fbd33-110">In a method, use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method to set the <xref:System.Windows.Forms.MdiLayout> enumeration for the MDI parent form.</span></span> <span data-ttu-id="fbd33-111">L'exemple ci-dessous utilise la valeur d'énumération <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> pour les fenêtres enfants du formulaire MDI parent (`Form1`).</span><span class="sxs-lookup"><span data-stu-id="fbd33-111">The following example uses the <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> enumeration value for the child windows of the MDI parent form (`Form1`).</span></span> <span data-ttu-id="fbd33-112">L’énumération est utilisée dans le code lors du gestionnaire d' <xref:System.Windows.Forms.Control.Click> événements pour l’événement de l’élément de menu **fenêtres en cascade** .</span><span class="sxs-lookup"><span data-stu-id="fbd33-112">The enumeration is used in code during the event handler for the <xref:System.Windows.Forms.Control.Click> event of the **Cascade Windows** menu item.</span></span>  
  
    ```vb  
    Protected Sub CascadeWindows_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)  
       Me.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade)  
    End Sub  
    ```  
  
    ```csharp  
    protected void CascadeWindows_Click(object sender, System.EventArgs e){  
       this.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade);  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="fbd33-113">De la même façon, vous pouvez disposer les fenêtres en mosaïque et les afficher sous forme d'icônes en modifiant la valeur d'énumération <xref:System.Windows.Forms.MdiLayout> utilisée.</span><span class="sxs-lookup"><span data-stu-id="fbd33-113">You can also tile windows and arranging windows as icons by changing the <xref:System.Windows.Forms.MdiLayout> enumeration value used.</span></span>  
  
2. <span data-ttu-id="fbd33-114">Si vous utilisez Visual C#, placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d'événements.</span><span class="sxs-lookup"><span data-stu-id="fbd33-114">If you’re using Visual C#, place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fbd33-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbd33-115">See also</span></span>

- [<span data-ttu-id="fbd33-116">Applications d’interface multidocument (MDI, Multiple Document Interface)</span><span class="sxs-lookup"><span data-stu-id="fbd33-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="fbd33-117">Guide pratique pour Créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="fbd33-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="fbd33-118">Guide pratique : Créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="fbd33-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="fbd33-119">Guide pratique pour Déterminer l’enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="fbd33-119">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="fbd33-120">Guide pratique pour Envoyer des données à l’enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="fbd33-120">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
