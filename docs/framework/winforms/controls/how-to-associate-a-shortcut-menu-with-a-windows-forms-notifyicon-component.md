---
title: Associer un menu raccourci à la composante NotifyIcon
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], for background processes
- NotifyIcon component [Windows Forms], associating shortcut menus
- shortcut menus [Windows Forms], for background processes
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
ms.openlocfilehash: 15a4a06726de348745e5eef03217d693db496a42
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182262"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="a79e8-102">Comment : associer un menu contextuel à un composant NotifyIcon Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a79e8-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
> <span data-ttu-id="a79e8-103">Bien <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> que et remplacer et <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> ajouter des fonctionnalités <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> et des contrôles des versions précédentes, et sont conservés à la fois pour la compatibilité vers l’arrière et l’utilisation future si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="a79e8-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="a79e8-104">Le <xref:System.Windows.Forms.NotifyIcon> composant affiche une icône dans la zone de notification d’état de la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="a79e8-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="a79e8-105">Généralement, les applications vous permettent de cliquer à droite sur cette icône pour envoyer des commandes à l’application qu’elle représente.</span><span class="sxs-lookup"><span data-stu-id="a79e8-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="a79e8-106">En associant <xref:System.Windows.Forms.ContextMenu> un <xref:System.Windows.Forms.NotifyIcon> composant au composant, vous pouvez ajouter cette fonctionnalité à vos applications.</span><span class="sxs-lookup"><span data-stu-id="a79e8-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a79e8-107">Si vous souhaitez que votre application soit réduite au <xref:System.Windows.Forms.NotifyIcon> minimum au démarrage tout en affichant <xref:System.Windows.Forms.Form.WindowState%2A> une <xref:System.Windows.Forms.FormWindowState.Minimized> instance du <xref:System.Windows.Forms.NotifyIcon> composant <xref:System.Windows.Forms.NotifyIcon.Visible%2A> dans la barre des tâches, définissez la propriété du formulaire principal et assurez-vous que la propriété du composant est réglée à `true`.</span><span class="sxs-lookup"><span data-stu-id="a79e8-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="a79e8-108">Associer un menu raccourci au composant NotifyIcon au moment de la conception</span><span class="sxs-lookup"><span data-stu-id="a79e8-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1. <span data-ttu-id="a79e8-109">Ajoutez <xref:System.Windows.Forms.NotifyIcon> un composant à votre formulaire et définissez <xref:System.Windows.Forms.NotifyIcon.Icon%2A> <xref:System.Windows.Forms.NotifyIcon.Visible%2A> les propriétés importantes, telles que la propriété et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="a79e8-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="a79e8-110">Pour plus d’informations, voir [Comment : Ajouter des icônes d’application à la taskBar avec le composant Windows Forms NotifyIcon](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="a79e8-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2. <span data-ttu-id="a79e8-111">Ajoutez <xref:System.Windows.Forms.ContextMenu> un composant à votre formulaire Windows.</span><span class="sxs-lookup"><span data-stu-id="a79e8-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="a79e8-112">Ajoutez des éléments de menu au menu raccourci représentant les commandes que vous souhaitez mettre à disposition à l’heure de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a79e8-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="a79e8-113">C’est également le bon moment pour ajouter des améliorations de menu à ces éléments de menu, tels que les clés d’accès.</span><span class="sxs-lookup"><span data-stu-id="a79e8-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3. <span data-ttu-id="a79e8-114">Réglez <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> la <xref:System.Windows.Forms.NotifyIcon> propriété du composant au menu raccourci que vous avez ajouté.</span><span class="sxs-lookup"><span data-stu-id="a79e8-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="a79e8-115">Avec cet ensemble de propriété, le menu raccourci sera affiché lorsque l’icône sur la barre des tâches est cliqué.</span><span class="sxs-lookup"><span data-stu-id="a79e8-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="a79e8-116">Associer un menu raccourci à la composante NotifyIcon programmatique</span><span class="sxs-lookup"><span data-stu-id="a79e8-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1. <span data-ttu-id="a79e8-117">Créez une instance <xref:System.Windows.Forms.NotifyIcon> de <xref:System.Windows.Forms.ContextMenu> la classe et d’une classe,<xref:System.Windows.Forms.NotifyIcon.Icon%2A> <xref:System.Windows.Forms.NotifyIcon.Visible%2A> avec tous <xref:System.Windows.Forms.NotifyIcon> les paramètres de <xref:System.Windows.Forms.ContextMenu> propriété nécessaires pour l’application (et les propriétés pour le composant, les éléments de menu pour le composant).</span><span class="sxs-lookup"><span data-stu-id="a79e8-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2. <span data-ttu-id="a79e8-118">Réglez <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> la <xref:System.Windows.Forms.NotifyIcon> propriété du composant au menu raccourci que vous avez ajouté.</span><span class="sxs-lookup"><span data-stu-id="a79e8-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="a79e8-119">Avec cet ensemble de propriété, le menu raccourci sera affiché lorsque l’icône sur la barre des tâches est cliqué.</span><span class="sxs-lookup"><span data-stu-id="a79e8-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a79e8-120">L’exemple de code suivant crée une structure de menu de base.</span><span class="sxs-lookup"><span data-stu-id="a79e8-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="a79e8-121">Vous devrez personnaliser les choix de menu à ceux qui correspondent à l’application que vous développez.</span><span class="sxs-lookup"><span data-stu-id="a79e8-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="a79e8-122">En outre, vous voudrez écrire <xref:System.Windows.Forms.MenuItem.Click> du code pour gérer les événements pour ces éléments de menu.</span><span class="sxs-lookup"><span data-stu-id="a79e8-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
    ```vb  
    Public ContextMenu1 As New ContextMenu  
    Public NotifyIcon1 As New NotifyIcon  
  
    Public Sub CreateIconMenuStructure()  
       ' Add menu items to shortcut menu.  
       ContextMenu1.MenuItems.Add("&Open Application")  
       ContextMenu1.MenuItems.Add("S&uspend Application")  
       ContextMenu1.MenuItems.Add("E&xit")  
  
       ' Set properties of NotifyIcon component.  
       NotifyIcon1.Icon = New System.Drawing.Icon _
          (System.Environment.GetFolderPath _
          (System.Environment.SpecialFolder.Personal)  _
          & "\Icon.ico")  
       NotifyIcon1.Text = "Right-click me!"  
       NotifyIcon1.Visible = True  
       NotifyIcon1.ContextMenu = ContextMenu1  
    End Sub  
    ```  
  
```csharp  
public NotifyIcon notifyIcon1 = new NotifyIcon();  
public ContextMenu contextMenu1 = new ContextMenu();  
  
public void createIconMenuStructure()  
{  
   // Add menu items to shortcut menu.  
   contextMenu1.MenuItems.Add("&Open Application");  
   contextMenu1.MenuItems.Add("S&uspend Application");  
   contextMenu1.MenuItems.Add("E&xit");  
  
   // Set properties of NotifyIcon component.  
   notifyIcon1.Icon = new System.Drawing.Icon  
      (System.Environment.GetFolderPath  
      (System.Environment.SpecialFolder.Personal)  
      + @"\Icon.ico");  
   notifyIcon1.Visible = true;  
   notifyIcon1.Text = "Right-click me!";  
   notifyIcon1.Visible = true;  
   notifyIcon1.ContextMenu = contextMenu1;  
}  
```  
  
```cpp  
public:  
   System::Windows::Forms::NotifyIcon ^ notifyIcon1;  
   System::Windows::Forms::ContextMenu ^ contextMenu1;  
  
   void createIconMenuStructure()  
   {  
      // Add menu items to shortcut menu.  
      contextMenu1->MenuItems->Add("&Open Application");  
      contextMenu1->MenuItems->Add("S&uspend Application");  
      contextMenu1->MenuItems->Add("E&xit");  
  
      // Set properties of NotifyIcon component.  
      notifyIcon1->Icon = gcnew System::Drawing::Icon  
          (String::Concat(System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::Personal),  
          "\\Icon.ico"));  
      notifyIcon1->Text = "Right-click me!";  
      notifyIcon1->Visible = true;  
      notifyIcon1->ContextMenu = contextMenu1;  
   }  
```  
  
> [!NOTE]
> <span data-ttu-id="a79e8-123">Vous devez `notifyIcon1` initialiser et `contextMenu1,` ce que vous pouvez faire en incluant les instructions suivantes dans le constructeur de votre formulaire :</span><span class="sxs-lookup"><span data-stu-id="a79e8-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="a79e8-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a79e8-124">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="a79e8-125">Comment : ajouter des icônes d’application à la barre des tâches à l’aide du composant NotifyIcon Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a79e8-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [<span data-ttu-id="a79e8-126">NotifyIcon, composant</span><span class="sxs-lookup"><span data-stu-id="a79e8-126">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="a79e8-127">Vue d'ensemble du composant NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="a79e8-127">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
