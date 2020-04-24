---
title: 'Procédure pas à pas : Contenu WPF de style'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07241d41e3fbf270a76bd241765bfa369ee265d5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646332"
---
# <a name="walkthrough-style-wpf-content"></a>Procédure pas à pas : Contenu WPF de style

Cet article vous montre comment appliquer le style à un contrôle de la Windows Presentation Foundation (WPF) hébergé sur un formulaire Windows.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas nécessite Visual Studio.

## <a name="create-the-project"></a>Créer le projet

Ouvrez Visual Studio et créez un nouveau projet d’application de formulaires Windows dans Visual Basic ou Visual C . `StylingWpfContent`

> [!NOTE]
> Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.

## <a name="create-the-wpf-control-types"></a>Créer les types de contrôle WPF

Une fois que vous avez ajouté un type de contrôle WPF au projet, vous pouvez l'héberger dans un contrôle <xref:System.Windows.Forms.Integration.ElementHost>.

1. Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution. Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`. Pour plus d’informations, voir [Procédure pas à pas: Créer du nouveau contenu WPF sur les formulaires Windows à Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. En mode Design, assurez-vous que `UserControl1` est sélectionné.

3. Dans la fenêtre **Propriétés,** <xref:System.Windows.FrameworkElement.Width%2A> définissez la valeur de la et <xref:System.Windows.FrameworkElement.Height%2A> des propriétés à **200**.

4. Ajoutez <xref:System.Windows.Controls.Button?displayProperty=nameWithType> un contrôle <xref:System.Windows.Controls.UserControl> à la et <xref:System.Windows.Controls.ContentControl.Content%2A> définissez la valeur de la propriété à **annuler**.

5. Ajouter un <xref:System.Windows.Controls.Button?displayProperty=nameWithType> deuxième <xref:System.Windows.Controls.UserControl> contrôle à la <xref:System.Windows.Controls.ContentControl.Content%2A> et définir la valeur de la propriété à **OK**.

6. Créez le projet.

## <a name="apply-a-style-to-a-wpf-control"></a>Appliquer un style à un contrôle WPF

Vous pouvez appliquer différents styles à un contrôle WPF pour modifier son apparence et son comportement.

1. Ouvrez `Form1` dans le Concepteur Windows Forms.

1. Dans la **boîte à** `UserControl1` outils , double-clic pour créer une instance de `UserControl1` sur le formulaire.

   Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.

1. Dans le panneau `elementHost1`d’étiquette intelligent pour , cliquez sur **Edit Contenu hébergé** de la liste d’abandon.

   `UserControl1`s’ouvre dans le WPF Designer.

1. En mode XAML, insérez le code XAML suivant après l’étiquette d’ouverture `<UserControl>`. Ce code XAML crée un dégradé avec une bordure de dégradé contrastée. Quand l'utilisateur clique sur le contrôle, les dégradés sont modifiés pour générer une apparence de bouton enfoncé. Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

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

1. Appliquer `SimpleButton` le style défini dans l’étape précédente sur le bouton `<Button>` Annuler en insérant le XAML suivant dans l’étiquette du bouton **Annuler.**

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   Votre déclaration de bouton ressemblera à la XAML suivante :

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. Créez le projet.

1. Ouvrez `Form1` dans le Concepteur Windows Forms.

1. Le nouveau style est appliqué au contrôle de bouton.

1. Dans le menu **Debug,** sélectionnez **Start Debugging** pour exécuter l’application.

1. Cliquez **sur** les boutons OK et **Annuler** et afficher les différences.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migration et interopérabilité](../../wpf/advanced/migration-and-interoperability.md)
- [Utilisation de contrôles WPF](using-wpf-controls.md)
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
