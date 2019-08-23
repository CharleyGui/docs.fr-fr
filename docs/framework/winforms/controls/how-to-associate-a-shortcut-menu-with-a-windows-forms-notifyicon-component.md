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
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Procédure : associer un menu contextuel à un composant NotifyIcon Windows Forms
> [!NOTE]
> Bien <xref:System.Windows.Forms.MenuStrip> que <xref:System.Windows.Forms.ContextMenuStrip> et remplacent et ajoutent des <xref:System.Windows.Forms.ContextMenu> fonctionnalités aux contrôles et des <xref:System.Windows.Forms.MainMenu> versions <xref:System.Windows.Forms.ContextMenu> antérieures, et sont conservés pour la <xref:System.Windows.Forms.MainMenu> compatibilité descendante et l’utilisation future si tel est votre choix.  
  
 Le <xref:System.Windows.Forms.NotifyIcon> composant affiche une icône dans la zone de notification d’état de la barre des tâches. En règle générale, les applications vous permettent de cliquer avec le bouton droit sur cette icône pour envoyer des commandes à l’application qu’elle représente. En associant un <xref:System.Windows.Forms.ContextMenu> composant <xref:System.Windows.Forms.NotifyIcon> au composant, vous pouvez ajouter cette fonctionnalité à vos applications.  
  
> [!NOTE]
> Si vous souhaitez que votre application soit réduite au démarrage tout en affichant une instance du <xref:System.Windows.Forms.NotifyIcon> composant dans la barre des tâches, affectez à <xref:System.Windows.Forms.FormWindowState.Minimized> la <xref:System.Windows.Forms.Form.WindowState%2A> propriété du formulaire principal la valeur <xref:System.Windows.Forms.NotifyIcon> et vérifiez <xref:System.Windows.Forms.NotifyIcon.Visible%2A> que la propriété du composant a la valeur `true`.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Pour associer un menu contextuel au composant NotifyIcon au moment du design  
  
1. Ajoutez un <xref:System.Windows.Forms.NotifyIcon> composant à votre formulaire et définissez les propriétés importantes, telles que les <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriétés et <xref:System.Windows.Forms.NotifyIcon.Visible%2A> .  
  
     Pour plus d'informations, voir [Procédure : Ajoutez des icônes d’application à la barre des tâches avec](app-icons-to-the-taskbar-with-wf-notifyicon.md)le composant NotifyIcon Windows Forms.  
  
2. Ajoutez un <xref:System.Windows.Forms.ContextMenu> composant à votre Windows Form.  
  
     Ajoutez des éléments de menu au menu contextuel représentant les commandes que vous souhaitez rendre disponibles au moment de l’exécution. Il s’agit également d’un bon moment pour ajouter des améliorations de menu à ces éléments de menu, comme les touches d’accès.  
  
3. Affectez à la <xref:System.Windows.Forms.NotifyIcon> propriétéducomposantlemenucontextuelquevousavezajouté.<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>  
  
     Une fois cette propriété définie, le menu contextuel s’affiche lorsque l’utilisateur clique sur l’icône dans la barre des tâches.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Pour associer un menu contextuel au composant NotifyIcon par programmation  
  
1. Créez une instance de la <xref:System.Windows.Forms.NotifyIcon> classe et une <xref:System.Windows.Forms.ContextMenu> classe, avec tous les paramètres de propriété nécessaires pour l’application<xref:System.Windows.Forms.NotifyIcon.Icon%2A> ( <xref:System.Windows.Forms.NotifyIcon.Visible%2A> et les propriétés <xref:System.Windows.Forms.NotifyIcon> du composant, les éléments de <xref:System.Windows.Forms.ContextMenu> menu du composant).  
  
2. Affectez à la <xref:System.Windows.Forms.NotifyIcon> propriétéducomposantlemenucontextuelquevousavezajouté.<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>  
  
     Une fois cette propriété définie, le menu contextuel s’affiche lorsque l’utilisateur clique sur l’icône dans la barre des tâches.  
  
    > [!NOTE]
    > L’exemple de code suivant crée une structure de menu de base. Vous devrez personnaliser les options de menu en fonction de celles qui correspondent à l’application que vous développez. En outre, vous souhaiterez peut-être écrire du code <xref:System.Windows.Forms.MenuItem.Click> pour gérer les événements de ces éléments de menu.  
  
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
> Vous devez initialiser `notifyIcon1` et `contextMenu1,` effectuer cette opération en incluant les instructions suivantes dans le constructeur de votre formulaire:  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Guide pratique : Ajouter des icônes d’application à la barre des tâches avec le composant NotifyIcon Windows Forms](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [NotifyIcon, composant](notifyicon-component-windows-forms.md)
- [Vue d’ensemble du composant NotifyIcon](notifyicon-component-overview-windows-forms.md)
