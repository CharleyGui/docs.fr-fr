---
title: 'Procédure : associer un menu contextuel à un composant NotifyIcon Windows Forms'
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
ms.openlocfilehash: bf5602d0526fdd97f0cc14382339095a793f13c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922770"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="95550-102">Procédure : associer un menu contextuel à un composant NotifyIcon Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95550-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
> <span data-ttu-id="95550-103">Bien <xref:System.Windows.Forms.MenuStrip> que <xref:System.Windows.Forms.ContextMenuStrip> et remplacent et ajoutent des <xref:System.Windows.Forms.ContextMenu> fonctionnalités aux contrôles et des <xref:System.Windows.Forms.MainMenu> versions <xref:System.Windows.Forms.ContextMenu> antérieures, et sont conservés pour la <xref:System.Windows.Forms.MainMenu> compatibilité descendante et l’utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="95550-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="95550-104">Le <xref:System.Windows.Forms.NotifyIcon> composant affiche une icône dans la zone de notification d’état de la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="95550-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="95550-105">En règle générale, les applications vous permettent de cliquer avec le bouton droit sur cette icône pour envoyer des commandes à l’application qu’elle représente.</span><span class="sxs-lookup"><span data-stu-id="95550-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="95550-106">En associant un <xref:System.Windows.Forms.ContextMenu> composant <xref:System.Windows.Forms.NotifyIcon> au composant, vous pouvez ajouter cette fonctionnalité à vos applications.</span><span class="sxs-lookup"><span data-stu-id="95550-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95550-107">Si vous souhaitez que votre application soit réduite au démarrage tout en affichant une instance du <xref:System.Windows.Forms.NotifyIcon> composant dans la barre des tâches, affectez à <xref:System.Windows.Forms.FormWindowState.Minimized> la <xref:System.Windows.Forms.Form.WindowState%2A> propriété du formulaire principal la valeur <xref:System.Windows.Forms.NotifyIcon> et vérifiez <xref:System.Windows.Forms.NotifyIcon.Visible%2A> que la propriété du composant a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="95550-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="95550-108">Pour associer un menu contextuel au composant NotifyIcon au moment du design</span><span class="sxs-lookup"><span data-stu-id="95550-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1. <span data-ttu-id="95550-109">Ajoutez un <xref:System.Windows.Forms.NotifyIcon> composant à votre formulaire et définissez les propriétés importantes, telles que les <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriétés et <xref:System.Windows.Forms.NotifyIcon.Visible%2A> .</span><span class="sxs-lookup"><span data-stu-id="95550-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="95550-110">Pour plus d'informations, voir [Procédure : Ajoutez des icônes d’application à la barre des tâches avec](app-icons-to-the-taskbar-with-wf-notifyicon.md)le composant NotifyIcon Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="95550-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2. <span data-ttu-id="95550-111">Ajoutez un <xref:System.Windows.Forms.ContextMenu> composant à votre Windows Form.</span><span class="sxs-lookup"><span data-stu-id="95550-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="95550-112">Ajoutez des éléments de menu au menu contextuel représentant les commandes que vous souhaitez rendre disponibles au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="95550-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="95550-113">Il s’agit également d’un bon moment pour ajouter des améliorations de menu à ces éléments de menu, comme les touches d’accès.</span><span class="sxs-lookup"><span data-stu-id="95550-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3. <span data-ttu-id="95550-114">Affectez à la <xref:System.Windows.Forms.NotifyIcon> propriétéducomposantlemenucontextuelquevousavezajouté.<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A></span><span class="sxs-lookup"><span data-stu-id="95550-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="95550-115">Une fois cette propriété définie, le menu contextuel s’affiche lorsque l’utilisateur clique sur l’icône dans la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="95550-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="95550-116">Pour associer un menu contextuel au composant NotifyIcon par programmation</span><span class="sxs-lookup"><span data-stu-id="95550-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1. <span data-ttu-id="95550-117">Créez une instance de la <xref:System.Windows.Forms.NotifyIcon> classe et une <xref:System.Windows.Forms.ContextMenu> classe, avec tous les paramètres de propriété nécessaires pour l’application<xref:System.Windows.Forms.NotifyIcon.Icon%2A> ( <xref:System.Windows.Forms.NotifyIcon.Visible%2A> et les propriétés <xref:System.Windows.Forms.NotifyIcon> du composant, les éléments de <xref:System.Windows.Forms.ContextMenu> menu du composant).</span><span class="sxs-lookup"><span data-stu-id="95550-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2. <span data-ttu-id="95550-118">Affectez à la <xref:System.Windows.Forms.NotifyIcon> propriétéducomposantlemenucontextuelquevousavezajouté.<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A></span><span class="sxs-lookup"><span data-stu-id="95550-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="95550-119">Une fois cette propriété définie, le menu contextuel s’affiche lorsque l’utilisateur clique sur l’icône dans la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="95550-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="95550-120">L’exemple de code suivant crée une structure de menu de base.</span><span class="sxs-lookup"><span data-stu-id="95550-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="95550-121">Vous devrez personnaliser les options de menu en fonction de celles qui correspondent à l’application que vous développez.</span><span class="sxs-lookup"><span data-stu-id="95550-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="95550-122">En outre, vous souhaiterez peut-être écrire du code <xref:System.Windows.Forms.MenuItem.Click> pour gérer les événements de ces éléments de menu.</span><span class="sxs-lookup"><span data-stu-id="95550-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
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
> <span data-ttu-id="95550-123">Vous devez initialiser `notifyIcon1` et `contextMenu1,` effectuer cette opération en incluant les instructions suivantes dans le constructeur de votre formulaire:</span><span class="sxs-lookup"><span data-stu-id="95550-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="95550-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95550-124">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="95550-125">Guide pratique : Ajouter des icônes d’application à la barre des tâches avec le composant NotifyIcon Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95550-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [<span data-ttu-id="95550-126">NotifyIcon, composant</span><span class="sxs-lookup"><span data-stu-id="95550-126">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="95550-127">Vue d’ensemble du composant NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="95550-127">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
