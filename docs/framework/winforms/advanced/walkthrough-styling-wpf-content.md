---
title: 'Procédure pas à pas : style de contenu WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e52297f51c74fc3dba93c987fd5b9bd5b6801777
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732544"
---
# <a name="walkthrough-style-wpf-content"></a>Procédure pas à pas : style de contenu WPF

Cet article vous explique comment appliquer un style à un contrôle Windows Presentation Foundation (WPF) hébergé sur un Windows Form.

## <a name="prerequisites"></a>Composants requis

Cette procédure pas à pas nécessite Visual Studio.

## <a name="create-the-project"></a>Créer le projet

Ouvrez Visual Studio et créez un projet d’application Windows Forms dans Visual Basic ou un C# visuel nommé `StylingWpfContent`.

> [!NOTE]
> Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.

## <a name="create-the-wpf-control-types"></a>Créer les types de contrôles WPF

Une fois que vous avez ajouté un type de contrôle WPF au projet, vous pouvez l'héberger dans un contrôle <xref:System.Windows.Forms.Integration.ElementHost>.

1. Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution. Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`. Pour plus d’informations, consultez [procédure pas à pas : création de contenu WPF sur Windows Forms au moment du design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. En mode Design, assurez-vous que `UserControl1` est sélectionné.

3. Dans la fenêtre **Propriétés** , affectez la valeur **200**aux propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.

4. Ajoutez un contrôle de <xref:System.Windows.Controls.Button?displayProperty=nameWithType> au <xref:System.Windows.Controls.UserControl> et définissez la valeur de la propriété <xref:System.Windows.Controls.ContentControl.Content%2A> sur **Annuler**.

5. Ajoutez un deuxième contrôle de <xref:System.Windows.Controls.Button?displayProperty=nameWithType> au <xref:System.Windows.Controls.UserControl> et définissez la valeur de la propriété <xref:System.Windows.Controls.ContentControl.Content%2A> sur **OK**.

6. créer le projet ;

## <a name="apply-a-style-to-a-wpf-control"></a>Appliquer un style à un contrôle WPF

Vous pouvez appliquer différents styles à un contrôle WPF pour modifier son apparence et son comportement.

1. Ouvrez `Form1` dans le Concepteur Windows Forms.

1. Dans la **boîte à outils**, double-cliquez sur `UserControl1` pour créer une instance de `UserControl1` sur le formulaire.

   Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.

1. Dans le panneau des balises actives pour `elementHost1`, cliquez sur **modifier le contenu hébergé** dans la liste déroulante.

   `UserControl1` s’ouvre dans le Concepteur WPF.

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

1. Appliquez le style de `SimpleButton` défini à l’étape précédente au bouton Annuler en insérant le code XAML suivant dans la balise `<Button>` du bouton **Annuler** .

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   Votre déclaration de bouton ressemble au code XAML suivant :

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. créer le projet ;

1. Ouvrez `Form1` dans le Concepteur Windows Forms.

1. Le nouveau style est appliqué au contrôle de bouton.

1. Dans le menu **Déboguer** , sélectionnez **Démarrer le débogage** pour exécuter l’application.

1. Cliquez sur les boutons **OK** et **Annuler** et affichez les différences.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migration et interopérabilité](../../wpf/advanced/migration-and-interoperability.md)
- [Utilisation de contrôles WPF](using-wpf-controls.md)
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Vue d’ensemble du langage XAML (WPF)](../../wpf/advanced/xaml-overview-wpf.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
