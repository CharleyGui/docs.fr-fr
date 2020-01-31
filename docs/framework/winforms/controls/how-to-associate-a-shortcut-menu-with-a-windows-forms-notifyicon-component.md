---
title: Associer un menu contextuel à un composant NotifyIcon
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
ms.openlocfilehash: 392c04f73feaec201033ad76f9419a0e070bec70
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742051"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Comment : associer un menu contextuel à un composant NotifyIcon Windows Forms
> [!NOTE]
> Bien que <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> remplacent et ajoutent des fonctionnalités aux contrôles <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> des versions précédentes, <xref:System.Windows.Forms.MainMenu> et les <xref:System.Windows.Forms.ContextMenu> sont conservés pour la compatibilité descendante et l’utilisation future si vous le souhaitez.  
  
 Le composant <xref:System.Windows.Forms.NotifyIcon> affiche une icône dans la zone de notification d’état de la barre des tâches. En règle générale, les applications vous permettent de cliquer avec le bouton droit sur cette icône pour envoyer des commandes à l’application qu’elle représente. En associant un composant <xref:System.Windows.Forms.ContextMenu> au composant <xref:System.Windows.Forms.NotifyIcon>, vous pouvez ajouter cette fonctionnalité à vos applications.  
  
> [!NOTE]
> Si vous souhaitez que votre application soit réduite au démarrage tout en affichant une instance du composant <xref:System.Windows.Forms.NotifyIcon> dans la barre des tâches, définissez la propriété <xref:System.Windows.Forms.Form.WindowState%2A> du formulaire principal sur <xref:System.Windows.Forms.FormWindowState.Minimized> et assurez-vous que la propriété <xref:System.Windows.Forms.NotifyIcon.Visible%2A> du composant <xref:System.Windows.Forms.NotifyIcon> est définie sur `true`.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Pour associer un menu contextuel au composant NotifyIcon au moment du design  
  
1. Ajoutez un composant <xref:System.Windows.Forms.NotifyIcon> à votre formulaire et définissez les propriétés importantes, telles que les propriétés <xref:System.Windows.Forms.NotifyIcon.Icon%2A> et <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.  
  
     Pour plus d’informations, consultez [Comment : ajouter des icônes d’application à la barre des tâches avec le composant Windows Forms NotifyIcon](app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
2. Ajoutez un composant <xref:System.Windows.Forms.ContextMenu> à votre Windows Form.  
  
     Ajoutez des éléments de menu au menu contextuel représentant les commandes que vous souhaitez rendre disponibles au moment de l’exécution. Il s’agit également d’un bon moment pour ajouter des améliorations de menu à ces éléments de menu, comme les touches d’accès.  
  
3. Définissez la propriété <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> du composant <xref:System.Windows.Forms.NotifyIcon> sur le menu contextuel que vous avez ajouté.  
  
     Une fois cette propriété définie, le menu contextuel s’affiche lorsque l’utilisateur clique sur l’icône dans la barre des tâches.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Pour associer un menu contextuel au composant NotifyIcon par programmation  
  
1. Créez une instance de la classe <xref:System.Windows.Forms.NotifyIcon> et une classe <xref:System.Windows.Forms.ContextMenu>, avec n’importe quel paramètre de propriété requis pour l’application (propriétés<xref:System.Windows.Forms.NotifyIcon.Icon%2A> et <xref:System.Windows.Forms.NotifyIcon.Visible%2A> pour le composant <xref:System.Windows.Forms.NotifyIcon>, les éléments de menu du composant <xref:System.Windows.Forms.ContextMenu>).  
  
2. Définissez la propriété <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> du composant <xref:System.Windows.Forms.NotifyIcon> sur le menu contextuel que vous avez ajouté.  
  
     Une fois cette propriété définie, le menu contextuel s’affiche lorsque l’utilisateur clique sur l’icône dans la barre des tâches.  
  
    > [!NOTE]
    > L’exemple de code suivant crée une structure de menu de base. Vous devrez personnaliser les options de menu en fonction de celles qui correspondent à l’application que vous développez. En outre, vous souhaiterez peut-être écrire du code pour gérer les événements de <xref:System.Windows.Forms.MenuItem.Click> pour ces éléments de menu.  
  
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
> Vous devez initialiser `notifyIcon1` et `contextMenu1,` ce que vous pouvez faire en incluant les instructions suivantes dans le constructeur de votre formulaire :  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Guide pratique pour ajouter des icônes d’application à la barre des tâches à l’aide du composant NotifyIcon Windows Forms](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [NotifyIcon, composant](notifyicon-component-windows-forms.md)
- [Vue d’ensemble du composant NotifyIcon](notifyicon-component-overview-windows-forms.md)
