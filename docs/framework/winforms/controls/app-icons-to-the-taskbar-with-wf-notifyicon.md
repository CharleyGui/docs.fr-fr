---
title: Ajouter des icônes d’application à la barre des tâches avec le composant NotifyIcon
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TrayIcon
helpviewer_keywords:
- status area icons
- icons [Windows Forms], adding to taskbar
- NotifyIcon component
- taskbar [Windows Forms], adding icons
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
ms.openlocfilehash: 46b50ecaabe75dba08fea922d7b5639031692269
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746248"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="bbf5c-102">Comment : ajouter des icônes d’application à la barre des tâches à l’aide du composant NotifyIcon Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bbf5c-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>

<span data-ttu-id="bbf5c-103">Le composant Windows Forms <xref:System.Windows.Forms.NotifyIcon> affiche une icône unique dans la zone de notification d’état de la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="bbf5c-104">Pour afficher plusieurs icônes dans la zone d’État, vous devez avoir plusieurs composants de <xref:System.Windows.Forms.NotifyIcon> dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="bbf5c-105">Pour définir l’icône affichée pour un contrôle, utilisez la propriété <xref:System.Windows.Forms.NotifyIcon.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="bbf5c-106">Vous pouvez également écrire du code dans le gestionnaire d’événements <xref:System.Windows.Forms.NotifyIcon.DoubleClick> pour qu’un événement se produise lorsque l’utilisateur double-clique sur l’icône.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="bbf5c-107">Par exemple, vous pouvez faire en sorte qu’une boîte de dialogue s’affiche pour permettre à l’utilisateur de configurer le processus en arrière-plan représenté par l’icône.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>

> [!NOTE]
> <span data-ttu-id="bbf5c-108">Le composant <xref:System.Windows.Forms.NotifyIcon> est utilisé à des fins de notification uniquement, pour avertir les utilisateurs qu’une action ou un événement s’est produit ou qu’une modification a été apportée à l’état d’un tri.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="bbf5c-109">Vous devez utiliser des menus, des barres d’outils et d’autres éléments d’interface utilisateur pour l’interaction standard avec les applications.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>

### <a name="to-set-the-icon"></a><span data-ttu-id="bbf5c-110">Pour définir l’icône</span><span class="sxs-lookup"><span data-stu-id="bbf5c-110">To set the icon</span></span>

1. <span data-ttu-id="bbf5c-111">Assignez une valeur à la propriété <xref:System.Windows.Forms.NotifyIcon.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="bbf5c-112">La valeur doit être de type `System.Drawing.Icon` et peut être chargée à partir d’un fichier. ico.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="bbf5c-113">Vous pouvez spécifier le fichier d’icône dans le code ou en cliquant sur le bouton de sélection (![le bouton de sélection (...) dans la Fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.NotifyIcon.Icon%2A> dans la fenêtre **Propriétés** , puis en sélectionnant le fichier dans la boîte de dialogue **ouvrir** qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-113">You can specify the icon file in code or by clicking the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>

2. <span data-ttu-id="bbf5c-114">Affectez à la propriété <xref:System.Windows.Forms.NotifyIcon.Visible%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>

3. <span data-ttu-id="bbf5c-115">Affectez à la propriété <xref:System.Windows.Forms.NotifyIcon.Text%2A> une chaîne d’info-bulle appropriée.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>

     <span data-ttu-id="bbf5c-116">Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’icône est le dossier **Mes documents** .</span><span class="sxs-lookup"><span data-stu-id="bbf5c-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="bbf5c-117">Cet emplacement est utilisé, car vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce dossier.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="bbf5c-118">Le choix de cet emplacement permet également aux utilisateurs disposant d’un niveau d’accès minimal au système d’exécuter l’application en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="bbf5c-119">L’exemple suivant requiert un formulaire avec un contrôle <xref:System.Windows.Forms.NotifyIcon> déjà ajouté.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="bbf5c-120">Elle nécessite également un fichier d’icône nommé `Icon.ico`.</span><span class="sxs-lookup"><span data-stu-id="bbf5c-120">It also requires an icon file named `Icon.ico`.</span></span>

    ```vb
    ' You should replace the bold icon in the sample below
    ' with an icon of your own choosing.
    NotifyIcon1.Icon = New _
       System.Drawing.Icon(System.Environment.GetFolderPath _
       (System.Environment.SpecialFolder.Personal) _
       & "\Icon.ico")
    NotifyIcon1.Visible = True
    NotifyIcon1.Text = "Antivirus program"
    ```

    ```csharp
    // You should replace the bold icon in the sample below
    // with an icon of your own choosing.
    // Note the escape character used (@) when specifying the path.
    notifyIcon1.Icon =
       new System.Drawing.Icon (System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.Personal)
       + @"\Icon.ico");
    notifyIcon1.Visible = true;
    notifyIcon1.Text = "Antivirus program";
    ```

    ```cpp
    // You should replace the bold icon in the sample below
    // with an icon of your own choosing.
    notifyIcon1->Icon = gcnew
       System::Drawing::Icon(String::Concat
       (System::Environment::GetFolderPath
       (System::Environment::SpecialFolder::Personal),
       "\\Icon.ico"));
    notifyIcon1->Visible = true;
    notifyIcon1->Text = "Antivirus program";
    ```

## <a name="see-also"></a><span data-ttu-id="bbf5c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbf5c-121">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="bbf5c-122">Guide pratique pour associer un menu contextuel à un composant NotifyIcon Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bbf5c-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [<span data-ttu-id="bbf5c-123">NotifyIcon, composant</span><span class="sxs-lookup"><span data-stu-id="bbf5c-123">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="bbf5c-124">Vue d’ensemble du composant NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="bbf5c-124">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
