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
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Comment : associer un menu contextuel à un composant NotifyIcon Windows Forms
> [!NOTE]
> Bien <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> que et remplacer et <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> ajouter des fonctionnalités <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> et des contrôles des versions précédentes, et sont conservés à la fois pour la compatibilité vers l’arrière et l’utilisation future si vous le souhaitez.  
  
 Le <xref:System.Windows.Forms.NotifyIcon> composant affiche une icône dans la zone de notification d’état de la barre des tâches. Généralement, les applications vous permettent de cliquer à droite sur cette icône pour envoyer des commandes à l’application qu’elle représente. En associant <xref:System.Windows.Forms.ContextMenu> un <xref:System.Windows.Forms.NotifyIcon> composant au composant, vous pouvez ajouter cette fonctionnalité à vos applications.  
  
> [!NOTE]
> Si vous souhaitez que votre application soit réduite au <xref:System.Windows.Forms.NotifyIcon> minimum au démarrage tout en affichant <xref:System.Windows.Forms.Form.WindowState%2A> une <xref:System.Windows.Forms.FormWindowState.Minimized> instance du <xref:System.Windows.Forms.NotifyIcon> composant <xref:System.Windows.Forms.NotifyIcon.Visible%2A> dans la barre des tâches, définissez la propriété du formulaire principal et assurez-vous que la propriété du composant est réglée à `true`.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Associer un menu raccourci au composant NotifyIcon au moment de la conception  
  
1. Ajoutez <xref:System.Windows.Forms.NotifyIcon> un composant à votre formulaire et définissez <xref:System.Windows.Forms.NotifyIcon.Icon%2A> <xref:System.Windows.Forms.NotifyIcon.Visible%2A> les propriétés importantes, telles que la propriété et les propriétés.  
  
     Pour plus d’informations, voir [Comment : Ajouter des icônes d’application à la taskBar avec le composant Windows Forms NotifyIcon](app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
2. Ajoutez <xref:System.Windows.Forms.ContextMenu> un composant à votre formulaire Windows.  
  
     Ajoutez des éléments de menu au menu raccourci représentant les commandes que vous souhaitez mettre à disposition à l’heure de l’exécution. C’est également le bon moment pour ajouter des améliorations de menu à ces éléments de menu, tels que les clés d’accès.  
  
3. Réglez <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> la <xref:System.Windows.Forms.NotifyIcon> propriété du composant au menu raccourci que vous avez ajouté.  
  
     Avec cet ensemble de propriété, le menu raccourci sera affiché lorsque l’icône sur la barre des tâches est cliqué.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Associer un menu raccourci à la composante NotifyIcon programmatique  
  
1. Créez une instance <xref:System.Windows.Forms.NotifyIcon> de <xref:System.Windows.Forms.ContextMenu> la classe et d’une classe,<xref:System.Windows.Forms.NotifyIcon.Icon%2A> <xref:System.Windows.Forms.NotifyIcon.Visible%2A> avec tous <xref:System.Windows.Forms.NotifyIcon> les paramètres de <xref:System.Windows.Forms.ContextMenu> propriété nécessaires pour l’application (et les propriétés pour le composant, les éléments de menu pour le composant).  
  
2. Réglez <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> la <xref:System.Windows.Forms.NotifyIcon> propriété du composant au menu raccourci que vous avez ajouté.  
  
     Avec cet ensemble de propriété, le menu raccourci sera affiché lorsque l’icône sur la barre des tâches est cliqué.  
  
    > [!NOTE]
    > L’exemple de code suivant crée une structure de menu de base. Vous devrez personnaliser les choix de menu à ceux qui correspondent à l’application que vous développez. En outre, vous voudrez écrire <xref:System.Windows.Forms.MenuItem.Click> du code pour gérer les événements pour ces éléments de menu.  
  
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
> Vous devez `notifyIcon1` initialiser et `contextMenu1,` ce que vous pouvez faire en incluant les instructions suivantes dans le constructeur de votre formulaire :  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Comment : ajouter des icônes d’application à la barre des tâches à l’aide du composant NotifyIcon Windows Forms](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [NotifyIcon, composant](notifyicon-component-windows-forms.md)
- [Vue d'ensemble du composant NotifyIcon](notifyicon-component-overview-windows-forms.md)
