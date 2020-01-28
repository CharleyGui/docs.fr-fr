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
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>Comment : ajouter des icônes d’application à la barre des tâches à l’aide du composant NotifyIcon Windows Forms

Le composant Windows Forms <xref:System.Windows.Forms.NotifyIcon> affiche une icône unique dans la zone de notification d’état de la barre des tâches. Pour afficher plusieurs icônes dans la zone d’État, vous devez avoir plusieurs composants de <xref:System.Windows.Forms.NotifyIcon> dans votre formulaire. Pour définir l’icône affichée pour un contrôle, utilisez la propriété <xref:System.Windows.Forms.NotifyIcon.Icon%2A>. Vous pouvez également écrire du code dans le gestionnaire d’événements <xref:System.Windows.Forms.NotifyIcon.DoubleClick> pour qu’un événement se produise lorsque l’utilisateur double-clique sur l’icône. Par exemple, vous pouvez faire en sorte qu’une boîte de dialogue s’affiche pour permettre à l’utilisateur de configurer le processus en arrière-plan représenté par l’icône.

> [!NOTE]
> Le composant <xref:System.Windows.Forms.NotifyIcon> est utilisé à des fins de notification uniquement, pour avertir les utilisateurs qu’une action ou un événement s’est produit ou qu’une modification a été apportée à l’état d’un tri. Vous devez utiliser des menus, des barres d’outils et d’autres éléments d’interface utilisateur pour l’interaction standard avec les applications.

### <a name="to-set-the-icon"></a>Pour définir l’icône

1. Assignez une valeur à la propriété <xref:System.Windows.Forms.NotifyIcon.Icon%2A>. La valeur doit être de type `System.Drawing.Icon` et peut être chargée à partir d’un fichier. ico. Vous pouvez spécifier le fichier d’icône dans le code ou en cliquant sur le bouton de sélection (![le bouton de sélection (...) dans la Fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.NotifyIcon.Icon%2A> dans la fenêtre **Propriétés** , puis en sélectionnant le fichier dans la boîte de dialogue **ouvrir** qui s’affiche.

2. Affectez à la propriété <xref:System.Windows.Forms.NotifyIcon.Visible%2A> la valeur `true`.

3. Affectez à la propriété <xref:System.Windows.Forms.NotifyIcon.Text%2A> une chaîne d’info-bulle appropriée.

     Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’icône est le dossier **Mes documents** . Cet emplacement est utilisé, car vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce dossier. Le choix de cet emplacement permet également aux utilisateurs disposant d’un niveau d’accès minimal au système d’exécuter l’application en toute sécurité. L’exemple suivant requiert un formulaire avec un contrôle <xref:System.Windows.Forms.NotifyIcon> déjà ajouté. Elle nécessite également un fichier d’icône nommé `Icon.ico`.

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

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Guide pratique pour associer un menu contextuel à un composant NotifyIcon Windows Forms](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [NotifyIcon, composant](notifyicon-component-windows-forms.md)
- [Vue d’ensemble du composant NotifyIcon](notifyicon-component-overview-windows-forms.md)
