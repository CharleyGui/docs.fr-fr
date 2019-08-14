---
title: 'Procédure pas à pas : application d’un style au contenu WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: 32ca9658ddf4ab6e8690f29797b7ac7b09df2ca7
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69012955"
---
# <a name="walkthrough-style-wpf-content"></a>Procédure pas à pas : Contenu WPF du style

Cette procédure pas à pas montre comment appliquer des styles à un contrôle WPF (Windows Presentation Foundation) hébergé sur un Windows Form.

 Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :

- créer le projet ;

- créer le type de contrôle WPF ;

- appliquer un style au contrôle WPF.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas nécessite Visual Studio.

## <a name="create-the-project"></a>Créer le projet

Ouvrez Visual Studio et créez un projet d’application Windows Forms dans Visual Basic ou un C# visuel `StylingWpfContent`nommé.

> [!NOTE]
> Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.

## <a name="create-the-wpf-control-types"></a>Créer les types de contrôles WPF

Une fois que vous avez ajouté un type de contrôle WPF au projet, vous pouvez l'héberger dans un contrôle <xref:System.Windows.Forms.Integration.ElementHost>.

1. Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution. Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`. Pour plus d’informations, consultez [Procédure pas à pas : Création d’un contenu WPF sur Windows Forms au moment](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)de la conception.

2. En mode Design, assurez-vous que `UserControl1` est sélectionné. Pour plus d'informations, voir [Procédure : Sélectionner et déplacer des éléments sur la](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100))aire de conception.

3. Dans la fenêtre **Propriétés** , affectez à <xref:System.Windows.FrameworkElement.Width%2A> `200`la valeur des <xref:System.Windows.FrameworkElement.Height%2A> propriétés et la valeur.

4. Ajoutez un <xref:System.Windows.Controls.Button?displayProperty=nameWithType> <xref:System.Windows.Controls.UserControl> contrôle au et <xref:System.Windows.Controls.ContentControl.Content%2A> affectez la valeur **Cancel**à la propriété.

5. Ajoutez un deuxième <xref:System.Windows.Controls.Button?displayProperty=nameWithType> contrôle <xref:System.Windows.Controls.UserControl> à et <xref:System.Windows.Controls.ContentControl.Content%2A> affectez la valeur **OK**à la propriété.

6. Générez le projet.

## <a name="apply-a-style-to-a-wpf-control"></a>Appliquer un style à un contrôle WPF

Vous pouvez appliquer différents styles à un contrôle WPF pour modifier son apparence et son comportement.

1. Ouvrez `Form1` dans le Concepteur Windows Forms.

1. Dans la **boîte à outils**, double `UserControl1` -cliquez sur pour créer `UserControl1` une instance de sur le formulaire.

     Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.

1. Dans le panneau des `elementHost1`balises actives, cliquez sur modifier le **contenu hébergé** dans la liste déroulante.

     `UserControl1` s'ouvre dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

1. En mode XAML, insérez le code XAML suivant après la balise d'ouverture `<UserControl>`.

     Ce code XAML crée un dégradé avec une bordure de dégradé contrastée. Quand l'utilisateur clique sur le contrôle, les dégradés sont modifiés pour générer une apparence de bouton enfoncé. Pour plus d’informations, consultez [Application d’un style et création de modèles](../../wpf/controls/styling-and-templating.md).

   ```xaml
   <UserControl.Resources>
    <LinearGradientBrush x:Key="NormalBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#FFF" Offset="0.0"/>
        <GradientStop Color="#CCC" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#BBB" Offset="0.0"/>
        <GradientStop Color="#EEE" Offset="0.1"/>
        <GradientStop Color="#EEE" Offset="0.9"/>
        <GradientStop Color="#FFF" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="NormalBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="BorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#444" Offset="0.0"/>
        <GradientStop Color="#888" Offset="1.0"/>
    </LinearGradientBrush>

    <Style x:Key="SimpleButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="Background" Value="{StaticResource NormalBrush}"/>
        <Setter Property="BorderBrush" Value="{StaticResource NormalBorderBrush}"/>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="{x:Type Button}">
                    <Grid x:Name="Grid">
                        <Border x:Name="Border" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}"/>
                        <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}" RecognizesAccessKey="True"/>
                    </Grid>
                    <ControlTemplate.Triggers>
                        <Trigger Property="IsPressed" Value="true">
                            <Setter Property="Background" Value="{StaticResource PressedBrush}" TargetName="Border"/>
                            <Setter Property="BorderBrush" Value="{StaticResource PressedBorderBrush}" TargetName="Border"/>
                        </Trigger>
                    </ControlTemplate.Triggers>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
   </UserControl.Resources>
   ```

1. Appliquez le style `SimpleButton` défini à l’étape précédente au bouton Annuler en insérant le code XAML suivant dans l’étiquette `<Button>` du bouton Annuler.

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   Votre déclaration de bouton ressemble au code XAML suivant:

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. Générez le projet.

1. Ouvrez `Form1` dans le Concepteur Windows Forms.

1. Le nouveau style est appliqué au contrôle de bouton.

1. Dans le menu Déboguer, sélectionnez **Démarrer** le débogage pour exécuter l’application.

1. Cliquez sur les boutons OK et Annuler et observez les différences.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migration et interopérabilité](../../wpf/advanced/migration-and-interoperability.md)
- [Utilisation de contrôles WPF](using-wpf-controls.md)
- [Concevoir en XAML dans Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Vue d’ensemble du langage XAML (WPF)](../../wpf/advanced/xaml-overview-wpf.md)
- [Application d’un style et création de modèles](../../wpf/controls/styling-and-templating.md)
