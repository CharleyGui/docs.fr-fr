---
title: 'Procédure : ajouter des contrôles sans interface utilisateur à des Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
ms.openlocfilehash: bc1f844e5a2cf4d4f3b64ebf20e935f36ff85e12
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987088"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>Procédure : ajouter des contrôles sans interface utilisateur à des Windows Forms

Un contrôle (ou un composant) qui fournit des fonctionnalités à votre application. Contrairement à d’autres contrôles, les composants ne fournissent pas d’interface utilisateur à l’utilisateur et n’ont donc pas besoin d’être affichés sur l’aire de Concepteur Windows Forms. Lorsqu’un composant est ajouté à un formulaire, le Concepteur Windows Forms affiche un plateau redimensionnable en bas du formulaire où tous les composants sont affichés. Une fois qu’un contrôle a été ajouté à la barre d’état des composants, vous pouvez sélectionner le composant et définir ses propriétés comme vous le feriez pour n’importe quel autre contrôle sur le formulaire.

## <a name="add-a-component-to-a-windows-form"></a>Ajouter un composant à un Windows Form

1. Ouvrez le formulaire dans Visual Studio. Pour plus d’informations, consultez [Guide pratique pour Affichez Windows Forms dans le](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))concepteur.

2. Dans la **boîte à outils**, cliquez sur un composant et faites-le glisser vers votre formulaire.

     Votre composant apparaît dans la barre d’état des composants.

En outre, les composants peuvent être ajoutés à un formulaire au moment de l’exécution. Il s’agit d’un scénario courant, en particulier parce que les composants n’ont pas d’expression visuelle, contrairement aux contrôles qui ont une interface utilisateur. Dans l’exemple ci-dessous <xref:System.Windows.Forms.Timer> , un composant est ajouté au moment de l’exécution. (Notez que Visual Studio contient plusieurs minuteries; dans ce cas, utilisez un composant Windows Forms <xref:System.Windows.Forms.Timer> . Pour plus d’informations sur les différents minuteries dans Visual Studio, consultez [Présentation des minuteries basées sur un serveur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)

> [!CAUTION]
> Les composants ont souvent des propriétés spécifiques au contrôle qui doivent être définies pour que le composant fonctionne correctement. Dans le cas du <xref:System.Windows.Forms.Timer> composant ci-dessous, vous définissez la `Interval` propriété. Lorsque vous ajoutez des composants à votre projet, veillez à définir les propriétés nécessaires pour ce composant.

## <a name="add-a-component-to-a-windows-form-programmatically"></a>Ajouter par programme un composant à un Windows Form

1. Créez une instance de la <xref:System.Windows.Forms.Timer> classe dans le code.

2. Définissez la `Interval` propriété pour déterminer l’intervalle entre les graduations de la minuterie.

3. Configurez toutes les autres propriétés nécessaires pour votre composant.

     Le code suivant illustre la création d’un <xref:System.Windows.Forms.Timer> avec son `Interval` jeu de propriétés.

    ```vb
    Public Sub CreateTimer()
       Dim timerKeepTrack As New System.Windows.Forms.Timer
       timerKeepTrack.Interval = 1000
    End Sub
    ```

    ```csharp
    public void createTimer()
    {
       System.Windows.Forms.Timer timerKeepTrack = new
           System.Windows.Forms.Timer();
       timerKeepTrack.Interval = 1000;
    }
    ```

    ```cpp
    public:
       void createTimer()
       {
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew
             System::Windows::Forms::Timer();
          timerKeepTrack->Interval = 1000;
       }
    ```

    > [!IMPORTANT]
    > Vous pouvez exposer votre ordinateur local à un risque de sécurité sur le réseau en référençant un UserControl malveillant. Cela ne serait qu’une préoccupation dans le cas d’une personne malveillante qui crée un contrôle personnalisé nuisible, puis de l’ajouter par erreur à votre projet.

## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms](index.md)
- [Guide pratique : Ajouter des contrôles à Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Guide pratique : Ajouter des contrôles ActiveX à Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [Placement de contrôles dans les Windows Forms](putting-controls-on-windows-forms.md)
- [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
- [Classement par fonction des contrôles Windows Forms](windows-forms-controls-by-function.md)
