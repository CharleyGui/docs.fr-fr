---
title: 'Procédure pas à pas : créer un bouton avec XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: a8cc227703e81e5de9dea7e44e10dfecca2cd05c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646465"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>Procédure pas à pas : créer un bouton avec XAML

L’objectif de cette procédure pas à pas est d’apprendre à créer un bouton d’animation pour une utilisation dans une application Windows Presentation Foundation (WPF). Cette procédure pas à pas utilise des styles et un modèle pour créer une ressource bouton personnalisée qui permet la réutilisation du code et la séparation de la logique du bouton de la déclaration de bouton. Cette procédure pas à pas [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]est entièrement écrite en .

> [!IMPORTANT]
> Cette procédure pas à pas vous guide à travers les étapes pour [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] créer l’application en tapant ou en copiant et en collé dans Visual Studio. Si vous préférez apprendre à utiliser un concepteur pour créer la même application, voir [Créer un bouton en utilisant Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).

Le chiffre suivant montre les boutons finis.

![Boutons personnalisés créés en utilisant XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-basic-buttons"></a>Créez des boutons de base

Commençons par créer un nouveau projet et ajouter quelques boutons à la fenêtre.

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Créer un nouveau projet WPF et ajouter des boutons à la fenêtre

1. Démarrez Visual Studio.

2. **Créer un nouveau projet WPF :** Sur le menu **du fichier,** pointez vers **New**, puis cliquez sur **Le projet**. Trouvez le modèle **d’application Windows (WPF)** et nommez le projet "AnimatedButton". Cela créera le squelette de l’application.

3. **Ajoutez des boutons par défaut de base :** Tous les fichiers dont vous avez besoin pour cette procédure pas à pas sont fournis par le modèle. Ouvrez le fichier Window1.xaml en le cliquant doublement dans Solution Explorer. Par défaut, il <xref:System.Windows.Controls.Grid> y a un élément dans Window1.xaml. Retirez <xref:System.Windows.Controls.Grid> l’élément et ajoutez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] quelques boutons à la page en tapant ou en copie et en coller le code surligné ci-dessus à Window1.xaml :

    ```xaml
    <Window x:Class="AnimatedButton.Window1"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      Title="AnimatedButton" Height="300" Width="300"
      Background="Black">
      <!-- Buttons arranged vertically inside a StackPanel. -->
      <StackPanel HorizontalAlignment="Left">
          <Button>Button 1</Button>
          <Button>Button 2</Button>
          <Button>Button 3</Button>
      </StackPanel>
    </Window>
    ```

     Appuyez sur F5 pour exécuter l’application; vous devriez voir un ensemble de boutons qui ressemble à la figure suivante.

     ![Trois boutons de base](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")

     Maintenant que vous avez créé les boutons de base, vous avez fini de travailler dans le fichier Window1.xaml. Le reste de la procédure pas à pas se concentre sur le fichier app.xaml, la définition des styles et un modèle pour les boutons.

## <a name="set-basic-properties"></a>Définir les propriétés de base

Ensuite, nous allons définir quelques propriétés sur ces boutons pour contrôler l’apparence du bouton et la mise en page. Plutôt que de définir les propriétés sur les boutons individuellement, vous utiliserez les ressources pour définir les propriétés bouton pour l’ensemble de l’application. Les ressources d’application sont conceptuellement semblables aux feuilles externes de style en cascade (CSS) pour les pages Web ; cependant, les ressources sont beaucoup plus puissantes que les feuilles de style en cascade (CSS), comme vous le verrez à la fin de cette procédure pas à pas. Pour en savoir plus sur les ressources, consultez [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Utiliser des styles pour définir les propriétés de base sur les boutons

1. **Décrivez un bloc Application.Resources :** Ouvrez app.xaml et ajoutez la balisage surlignée suivante si elle n’est pas déjà là:

    ```xaml
    <Application x:Class="AnimatedButton.App"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      StartupUri="Window1.xaml"
      >
      <Application.Resources>
        <!-- Resources for the entire application can be defined here. -->
      </Application.Resources>
    </Application>
    ```

     La portée des ressources est déterminée par l’endroit où vous définissez la ressource. La définition `Application.Resources` des ressources dans le fichier app.xaml permet d’utiliser la ressource de n’importe où dans l’application. Pour en savoir plus sur la définition de la portée de vos ressources, consultez [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

2. **Créez un style et définissez les valeurs de base des propriétés avec lui :** Ajouter la marque suivante `Application.Resources` au bloc. Cette balisage <xref:System.Windows.Style> crée un qui s’applique à <xref:System.Windows.FrameworkElement.Width%2A> tous les boutons de l’application, en définissant les boutons à 90 et le <xref:System.Windows.FrameworkElement.Margin%2A> à 10:

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     La <xref:System.Windows.Style.TargetType%2A> propriété précise que le style s’applique à tous les objets de type <xref:System.Windows.Controls.Button>. Chacun <xref:System.Windows.Setter> établit une valeur <xref:System.Windows.Style>de propriété différente pour le . Par conséquent, à ce stade, chaque bouton de l’application a une largeur de 90 et une marge de 10.  Si vous appuyez sur F5 pour exécuter l’application, vous voyez la fenêtre suivante.

     ![Boutons avec une largeur de 90 et une marge de 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")

     Il ya beaucoup plus que vous pouvez faire avec les styles, y compris une variété de façons d’affiner ce que les objets sont ciblés, spécifiant des valeurs de propriété complexes, et même en utilisant des styles comme entrée pour d’autres styles. Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

3. **Définissez une valeur de propriété de style à une ressource :** Les ressources permettent un moyen simple de réutiliser des objets et des valeurs communément définis. Il est particulièrement utile de définir des valeurs complexes en utilisant des ressources pour rendre votre code plus modulaire. Ajoutez la balisage surlignée suivante à app.xaml.

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush" StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     Directement sous `Application.Resources` le bloc, vous avez créé une ressource appelée "GrayBlueGradientBrush". Cette ressource définit un gradient horizontal. Cette ressource peut être utilisée comme valeur de propriété de n’importe <xref:System.Windows.Controls.Control.Background%2A> où dans l’application, y compris à l’intérieur du setter de style bouton pour la propriété. Maintenant, tous les boutons <xref:System.Windows.Controls.Control.Background%2A> ont une valeur de propriété de ce gradient.

     Appuyez sur F5 pour exécuter l'application. Il devrait ressembler à ce qui suit.

     ![Boutons avec un arrière-plan dégradé](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")

## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Créer un modèle qui définit l’apparence du bouton

Dans cette section, vous créez un modèle qui personnalise l’apparence (présentation) du bouton. La présentation du bouton est composée de plusieurs objets, y compris des rectangles et d’autres composants pour donner au bouton un look unique.

Jusqu’à présent, le contrôle de l’apparence des boutons dans l’application a été limité à changer les propriétés du bouton. Que faire si vous voulez apporter des changements plus radicaux à l’apparence du bouton? Les modèles permettent un contrôle puissant sur la présentation d’un objet. Étant donné que les modèles peuvent être utilisés dans les styles, vous pouvez appliquer un modèle à tous les objets auxquels le style s’applique (dans cette procédure pas à pas, le bouton).

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Pour utiliser le modèle pour définir l’apparence du bouton

1. **Configurez le modèle :** Parce que <xref:System.Windows.Controls.Button> les <xref:System.Windows.Controls.Control.Template%2A> contrôles comme ont une propriété, vous pouvez définir la <xref:System.Windows.Style> valeur <xref:System.Windows.Setter>de propriété modèle tout comme les autres valeurs de propriété que nous avons mis dans un utilisation d’un . Ajoutez la marque surlignée suivante à votre style de bouton.

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"
        StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
        <Setter Property="Template">
          <Setter.Value>
            <!-- The button template is defined here. -->
          </Setter.Value>
        </Setter>
      </Style>
    </Application.Resources>
    ```

2. **Présentation du bouton Alter :** À ce stade, vous devez définir le modèle. Ajoutez la balisage surlignée ci-après. Cette balisage spécifie deux <xref:System.Windows.Shapes.Rectangle> éléments <xref:System.Windows.Controls.DockPanel>avec des bords arrondis, suivi d’un . Le <xref:System.Windows.Controls.DockPanel> est utilisé <xref:System.Windows.Controls.ContentPresenter> pour héberger le bouton. Un <xref:System.Windows.Controls.ContentPresenter> affiche le contenu du bouton. Dans cette procédure pas à pas, le contenu est texte ("Button 1", "Button 2", "Button 3"). Tous les composants du modèle (les <xref:System.Windows.Controls.DockPanel>rectangles et les <xref:System.Windows.Controls.Grid>) sont disposés à l’intérieur d’un .

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="Button">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}" ClipToBounds="True">
          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}" RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />
          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20" Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />
          <!-- Present Content (text) of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20" Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>
      </ControlTemplate>
    </Setter.Value>
    ```

     Appuyez sur F5 pour exécuter l'application. Il devrait ressembler à ce qui suit.

     ![Fenêtre avec 3 boutons](./media/custom-button-animatedbutton-4.gif)

3. **Ajoutez un effet de verre au modèle :** Ensuite, vous ajouterez le verre. Tout d’abord, vous créez des ressources qui créent un effet de gradient de verre. Ajoutez ces ressources de `Application.Resources` gradient n’importe où dans le bloc :

    ```xaml
    <Application.Resources>
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">
        <GradientStop Color="WhiteSmoke" Offset="0.2" />
        <GradientStop Color="Transparent" Offset="0.4" />
        <GradientStop Color="WhiteSmoke" Offset="0.5" />
        <GradientStop Color="Transparent" Offset="0.75" />
        <GradientStop Color="WhiteSmoke" Offset="0.9" />
        <GradientStop Color="Transparent" Offset="1" />
      </GradientStopCollection>
      <LinearGradientBrush x:Key="MyGlassBrushResource"
        StartPoint="0,0" EndPoint="1,1" Opacity="0.75"
        GradientStops="{StaticResource MyGlassGradientStopsResource}" />
    <!-- Styles and other resources below here. -->
    ```

     Ces ressources sont <xref:System.Windows.Shapes.Shape.Fill%2A> utilisées comme pour un <xref:System.Windows.Controls.Grid> rectangle que nous insérons dans le modèle de bouton. Ajoutez la marque surlignée suivante au modèle.

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}"
          ClipToBounds="True">

        <!-- Outer Rectangle with rounded corners. -->
        <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

        <!-- Inner Rectangle with rounded corners. -->
        <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20"
          Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />

        <!-- Glass Rectangle -->
        <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch"
          StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
          Fill="{StaticResource MyGlassBrushResource}"
          RenderTransformOrigin="0.5,0.5">
          <Rectangle.Stroke>
            <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
              <LinearGradientBrush.GradientStops>
                <GradientStop Offset="0.0" Color="LightBlue" />
                <GradientStop Offset="1.0" Color="Gray" />
              </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
          </Rectangle.Stroke>
          <!-- These transforms have no effect as they are declared here.
          The reason the transforms are included is to be targets
          for animation (see later). -->
          <Rectangle.RenderTransform>
            <TransformGroup>
              <ScaleTransform />
              <RotateTransform />
            </TransformGroup>
          </Rectangle.RenderTransform>
          <!-- A BevelBitmapEffect is applied to give the button a "Beveled" look. -->
          <Rectangle.BitmapEffect>
            <BevelBitmapEffect />
          </Rectangle.BitmapEffect>
        </Rectangle>

        <!-- Present Text of the button. -->
        <DockPanel Name="myContentPresenterDockPanel">
          <ContentPresenter x:Name="myContentPresenter" Margin="20"
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
        </DockPanel>
      </Grid>
    </ControlTemplate>
    </Setter.Value>
    ```

     Notez <xref:System.Windows.UIElement.Opacity%2A> que le rectangle `x:Name` avec la propriété de "glassCube" est de 0, donc quand vous exécutez l’échantillon, vous ne voyez pas le rectangle de verre superposé sur le dessus. C’est parce que nous allons plus tard ajouter des déclencheurs au modèle pour quand l’utilisateur interagit avec le bouton. Cependant, vous pouvez voir à quoi ressemble <xref:System.Windows.UIElement.Opacity%2A> le bouton maintenant en changeant la valeur à 1 et en exécutant l’application. Voir la figure suivante. Avant de passer à l’étape suivante, changez le <xref:System.Windows.UIElement.Opacity%2A> dos à 0.

     ![Boutons personnalisés créés en utilisant XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-button-interactivity"></a>Créer l’interactivité bouton

Dans cette section, vous créerez des déclencheurs de propriété et des déclencheurs d’événements pour changer les valeurs de propriété et exécuter des animations en réponse aux actions de l’utilisateur telles que le déplacement du pointeur de souris sur le bouton et le clic.

Un moyen facile d’ajouter l’interactivité (souris-over, souris-laisser, cliquez, et ainsi de suite) est de définir les déclencheurs dans votre modèle ou style. Pour créer <xref:System.Windows.Trigger>un , vous définissez une propriété <xref:System.Windows.UIElement.IsMouseOver%2A> "condition" `true`telle que: La valeur de la propriété bouton est égale à . Vous définissez ensuite les setters (actions) qui ont lieu lorsque l’état de déclenchement est vrai.

### <a name="to-create-button-interactivity"></a>Créer l’interactivité des boutons

1. **Ajouter des déclencheurs de modèle :** Ajoutez la marque mise en évidence à votre modèle.

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}"
          Height="{TemplateBinding Height}" ClipToBounds="True">

          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch" Stroke="Transparent"
            StrokeThickness="20"
            Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20"
          />

          <!-- Glass Rectangle -->
          <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch"
            StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
            Fill="{StaticResource MyGlassBrushResource}"
            RenderTransformOrigin="0.5,0.5">
            <Rectangle.Stroke>
              <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
                <LinearGradientBrush.GradientStops>
                  <GradientStop Offset="0.0" Color="LightBlue" />
                  <GradientStop Offset="1.0" Color="Gray" />
                </LinearGradientBrush.GradientStops>
              </LinearGradientBrush>
            </Rectangle.Stroke>

            <!-- These transforms have no effect as they
                 are declared here.
                 The reason the transforms are included is to be targets
                 for animation (see later). -->
            <Rectangle.RenderTransform>
              <TransformGroup>
                <ScaleTransform />
                <RotateTransform />
              </TransformGroup>
            </Rectangle.RenderTransform>

              <!-- A BevelBitmapEffect is applied to give the button a
                   "Beveled" look. -->
            <Rectangle.BitmapEffect>
              <BevelBitmapEffect />
            </Rectangle.BitmapEffect>
          </Rectangle>

          <!-- Present Text of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20"
              Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>

        <ControlTemplate.Triggers>       <!-- Set action triggers for the buttons and define            what the button does in response to those triggers. -->     </ControlTemplate.Triggers>
      </ControlTemplate>
    </Setter.Value>
    ```

2. **Ajouter les déclencheurs de propriété :** Ajoutez la marque mise `ControlTemplate.Triggers` en évidence au bloc :

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     Appuyez sur F5 pour exécuter l’application et voir l’effet que vous exécutez le pointeur de la souris sur les boutons.

3. **Ajouter un déclencheur de mise au point :** Ensuite, nous ajouterons des setters similaires pour gérer le boîtier lorsque le bouton est focalisateur (par exemple, après que l’utilisateur l’a cliqué).

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->
      <Trigger Property="IsMouseOver" Value="True">

        <!-- Below are three property settings that occur when the
             condition is met (user mouses over button).  -->
        <!-- Change the color of the outer rectangle when user          mouses over it. -->
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />

        <!-- Sets the glass opacity to 1, therefore, the          glass "appears" when user mouses over it. -->
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />

        <!-- Makes the text slightly blurry as though you were          looking at it through blurry glass. -->
        <Setter Property="ContentPresenter.BitmapEffect"       TargetName="myContentPresenter">
          <Setter.Value>
            <BlurBitmapEffect Radius="1" />
          </Setter.Value>
        </Setter>
      </Trigger>
      <!-- Set properties when button has focus. -->   <Trigger Property="IsFocused" Value="true">     <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />     <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />   </Trigger>

    </ControlTemplate.Triggers>
    ```

     Appuyez sur F5 pour exécuter l’application et cliquez sur l’un des boutons. Notez que le bouton reste surligné après avoir cliqué parce qu’il a toujours mise au point. Si vous cliquez sur un autre bouton, le nouveau bouton se concentre tandis que le dernier le perd.

4. **Ajoutez des animations pour** <xref:System.Windows.UIElement.MouseEnter> **et** <xref:System.Windows.UIElement.MouseLeave> **:** Ensuite, nous ajoutons quelques animations aux déclencheurs.   Ajouter la balisage suivante `ControlTemplate.Triggers` n’importe où à l’intérieur du bloc.

    ```xaml
    <!-- Animations that start when mouse enters and leaves button. -->
    <EventTrigger RoutedEvent="Mouse.MouseEnter">
      <EventTrigger.Actions>
        <BeginStoryboard Name="mouseEnterBeginStoryboard">
          <Storyboard>
          <!-- This animation makes the glass rectangle shrink in the X direction. -->
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleX)"
              By="-0.1" Duration="0:0:0.5" />
            <!-- This animation makes the glass rectangle shrink in the Y direction. -->
            <DoubleAnimation
            Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleY)"
              By="-0.1" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    <EventTrigger RoutedEvent="Mouse.MouseLeave">
      <EventTrigger.Actions>
        <!-- Stopping the storyboard sets all animated properties back to default. -->
        <StopStoryboard BeginStoryboardName="mouseEnterBeginStoryboard" />
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     Le rectangle de verre se rétrécit lorsque le pointeur de la souris se déplace sur le bouton et revient à la taille normale lorsque le pointeur quitte.

     Il ya deux animations qui sont déclenchées<xref:System.Windows.UIElement.MouseEnter> lorsque le pointeur va sur le bouton (l’événement est soulevé). Ces animations rétrécissent le rectangle de verre le long de l’axe X et Y. Remarquez les <xref:System.Windows.Media.Animation.DoubleAnimation> propriétés <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>sur les éléments — et . Le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> spécifie que l’animation <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> se produit plus d’une demi-seconde, et précise que le verre rétrécit de 10%.

     Le deuxième déclencheur<xref:System.Windows.UIElement.MouseLeave>de l’événement ( ) arrête simplement le premier. Lorsque vous <xref:System.Windows.Media.Animation.Storyboard>arrêtez un , toutes les propriétés animées reviennent à leurs valeurs par défaut. Par conséquent, lorsque l’utilisateur déplace le pointeur sur le bouton, le bouton remonte à la façon dont il était avant que le pointeur de la souris déplacé sur le bouton. Pour plus d’informations sur les animations, voir [Aperçu animation](../graphics-multimedia/animation-overview.md).

5. **Ajoutez une animation pour quand le bouton est cliqué :** La dernière étape consiste à ajouter un déclencheur pour quand l’utilisateur clique sur le bouton. Ajoutez la balisage suivante `ControlTemplate.Triggers` n’importe où à l’intérieur du bloc :

    ```xaml
    <!-- Animation fires when button is clicked, causing glass to spin.  -->
    <EventTrigger RoutedEvent="Button.Click">
      <EventTrigger.Actions>
        <BeginStoryboard>
          <Storyboard>
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[1].(RotateTransform.Angle)"
              By="360" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     Appuyez sur F5 pour exécuter l’application, et cliquez sur l’un des boutons. Lorsque vous cliquez sur un bouton, le rectangle de verre tourne autour.

## <a name="summary"></a>Résumé
 Dans cette procédure pas à pas, vous avez effectué les exercices suivants :

- Ciblé <xref:System.Windows.Style> un à un<xref:System.Windows.Controls.Button>type d’objet ( ).

- Propriétés de base contrôlées des boutons <xref:System.Windows.Style>dans l’ensemble de l’application en utilisant le .

- Création de ressources comme des gradients <xref:System.Windows.Style> à utiliser pour la valeur des propriétés des setters.

- Personnalisé l’apparence des boutons dans l’ensemble de l’application en appliquant un modèle sur les boutons.

- Comportement personnalisé pour les boutons en réponse aux <xref:System.Windows.UIElement.MouseEnter> <xref:System.Windows.UIElement.MouseLeave>actions <xref:System.Windows.Controls.Primitives.ButtonBase.Click>de l’utilisateur (tels que , , et ) qui comprenait des effets d’animation.

## <a name="see-also"></a>Voir aussi

- [Créer un bouton à l'aide de Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vue d'ensemble de l'animation](../graphics-multimedia/animation-overview.md)
- [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Vue d'ensemble des effets bitmap](../graphics-multimedia/bitmap-effects-overview.md)
