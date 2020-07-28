---
title: 'Procédure pas à pas : créer un bouton avec XAML'
description: Utilisez cette procédure pas à pas pour apprendre à créer un bouton animé à utiliser dans une application Windows Presentation Foundation à l’aide de XAML.
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 136d1ad5d6fefd70f0d977e5287ae75f06c52d36
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164845"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>Procédure pas à pas : créer un bouton avec XAML

L’objectif de cette procédure pas à pas est d’apprendre à créer un bouton animé à utiliser dans une application Windows Presentation Foundation (WPF). Cette procédure pas à pas utilise des styles et un modèle pour créer une ressource de bouton personnalisée qui permet la réutilisation du code et la séparation de la logique de bouton à partir de la déclaration de bouton. Cette procédure pas à pas est écrite entièrement dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .

> [!IMPORTANT]
> Cette procédure pas à pas vous guide tout au long des étapes de création de l’application en tapant ou en copiant-collant [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dans Visual Studio. Si vous préférez apprendre à utiliser un concepteur pour créer la même application, consultez [créer un bouton à l’aide de Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).

L’illustration suivante montre les boutons terminés.

![Boutons personnalisés créés en utilisant XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-basic-buttons"></a>Créer des boutons de base

Commençons par créer un nouveau projet et à ajouter quelques boutons à la fenêtre.

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Pour créer un projet WPF et ajouter des boutons à la fenêtre

1. Démarrez Visual Studio.

2. **Créez un projet WPF :** Dans le menu **fichier** , pointez sur **nouveau**, puis cliquez sur **projet**. Recherchez le modèle d' **application Windows (WPF)** et nommez le projet « AnimatedButton ». Cette opération crée la structure de l’application.

3. **Ajouter des boutons par défaut de base :** Tous les fichiers dont vous avez besoin pour cette procédure pas à pas sont fournis par le modèle. Ouvrez le fichier Window1. XAML en double-cliquant dessus dans Explorateur de solutions. Par défaut, il existe un <xref:System.Windows.Controls.Grid> élément dans Window1. Xaml. Supprimez l' <xref:System.Windows.Controls.Grid> élément et ajoutez quelques boutons à la [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page en tapant ou en recopiant et collant le code en surbrillance suivant dans Window1. xaml :

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

     Appuyez sur F5 pour exécuter l’application. vous devez voir un ensemble de boutons ressemblant à l’illustration suivante.

     ![Trois boutons de base](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")

     Maintenant que vous avez créé les boutons de base, vous avez fini de travailler dans le fichier Window1. Xaml. Le reste de la procédure pas à pas se concentre sur le fichier app. xaml, sur la définition des styles et un modèle pour les boutons.

## <a name="set-basic-properties"></a>Définir les propriétés de base

Ensuite, nous allons définir des propriétés sur ces boutons pour contrôler l’apparence et la disposition du bouton. Au lieu de définir des propriétés sur les boutons individuellement, vous allez utiliser des ressources pour définir les propriétés de bouton de l’application entière. Les ressources d’application sont conceptuellement similaires aux feuilles de style en cascade externes (CSS) pour les pages Web ; Toutefois, les ressources sont bien plus puissantes que feuilles de style en cascade (CSS), comme vous le verrez à la fin de cette procédure pas à pas. Pour en savoir plus sur les ressources, consultez [ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Pour utiliser des styles pour définir des propriétés de base sur les boutons

1. **Définissez un bloc application. Resources :** Ouvrez App. xaml et ajoutez le balisage en surbrillance suivant s’il n’y figure pas déjà :

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

     L’étendue des ressources est déterminée par l’emplacement de définition de la ressource. La définition de ressources dans `Application.Resources` le fichier app. Xaml permet d’utiliser la ressource depuis n’importe où dans l’application. Pour en savoir plus sur la définition de l’étendue de vos ressources, consultez [ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

2. **Créez un style et définissez les valeurs de propriété de base avec lui :** Ajoutez le balisage suivant au `Application.Resources` bloc. Ce balisage crée un <xref:System.Windows.Style> qui s’applique à tous les boutons de l’application, en affectant à la propriété <xref:System.Windows.FrameworkElement.Width%2A> des boutons la valeur 90 et la <xref:System.Windows.FrameworkElement.Margin%2A> valeur 10 :

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     La <xref:System.Windows.Style.TargetType%2A> propriété spécifie que le style s’applique à tous les objets de type <xref:System.Windows.Controls.Button> . Chaque <xref:System.Windows.Setter> définit une valeur de propriété différente pour le <xref:System.Windows.Style> . Par conséquent, à ce stade, chaque bouton de l’application a une largeur de 90 et une marge de 10.  Si vous appuyez sur F5 pour exécuter l’application, la fenêtre suivante s’affiche.

     ![Boutons avec une largeur de 90 et une marge de 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")

     Vous pouvez faire bien d’autres choses avec les styles, y compris diverses façons d’affiner les objets ciblés, en spécifiant des valeurs de propriété complexes et même en utilisant des styles comme entrée pour d’autres styles. Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

3. **Définissez une valeur de propriété de style sur une ressource :** Les ressources permettent de réutiliser facilement les objets et valeurs couramment définis. Il est particulièrement utile de définir des valeurs complexes à l’aide de ressources pour faciliter la modularité de votre code. Ajoutez le balisage en surbrillance suivant à App. Xaml.

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

     Directement sous le `Application.Resources` bloc, vous avez créé une ressource appelée « GrayBlueGradientBrush ». Cette ressource définit un dégradé horizontal. Cette ressource peut être utilisée en tant que valeur de propriété à n’importe quel endroit de l’application, y compris à l’intérieur de la méthode setter de style de bouton pour la <xref:System.Windows.Controls.Control.Background%2A> propriété. À présent, tous les boutons ont une <xref:System.Windows.Controls.Control.Background%2A> valeur de propriété de ce dégradé.

     Appuyez sur F5 pour exécuter l'application. Elle doit ressembler à ce qui suit.

     ![Boutons avec un arrière-plan dégradé](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")

## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Créer un modèle qui définit l’apparence du bouton

Dans cette section, vous allez créer un modèle qui personnalise l’apparence (présentation) du bouton. La présentation du bouton est composée de plusieurs objets, y compris des rectangles et d’autres composants, pour donner un aspect unique au bouton.

Jusqu’à présent, le contrôle de l’apparence des boutons dans l’application a été limité à la modification des propriétés du bouton. Que se passe-t-il si vous souhaitez apporter des modifications plus radicales à l’apparence du bouton ? Les modèles permettent un contrôle puissant de la présentation d’un objet. Étant donné que les modèles peuvent être utilisés dans les styles, vous pouvez appliquer un modèle à tous les objets auxquels le style s’applique (dans cette procédure pas à pas, le bouton).

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Pour utiliser le modèle afin de définir l’apparence du bouton

1. **Configurez le modèle :** Comme les contrôles comme <xref:System.Windows.Controls.Button> ont une <xref:System.Windows.Controls.Control.Template%2A> propriété, vous pouvez définir la valeur de propriété de modèle comme les autres valeurs de propriété que nous avons définies dans un <xref:System.Windows.Style> à l’aide d’un <xref:System.Windows.Setter> . Ajoutez le balisage en surbrillance suivant à votre style de bouton.

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

2. **Présentation du bouton modifier :** À ce stade, vous devez définir le modèle. Ajoutez le balisage en surbrillance suivant. Ce balisage spécifie deux <xref:System.Windows.Shapes.Rectangle> éléments avec des bords arrondis, suivis d’un <xref:System.Windows.Controls.DockPanel> . Le <xref:System.Windows.Controls.DockPanel> est utilisé pour héberger le <xref:System.Windows.Controls.ContentPresenter> du bouton. Un <xref:System.Windows.Controls.ContentPresenter> affiche le contenu du bouton. Dans cette procédure pas à pas, le contenu est de texte (« Button 1 », « Button 2 », « Button 3 »). Tous les composants de modèle (les rectangles et <xref:System.Windows.Controls.DockPanel> ) sont disposés à l’intérieur d’un <xref:System.Windows.Controls.Grid> .

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

     Appuyez sur F5 pour exécuter l'application. Elle doit ressembler à ce qui suit.

     ![Fenêtre avec 3 boutons](./media/custom-button-animatedbutton-4.gif)

3. **Ajoutez un GlassEffect au modèle :** Ensuite, vous allez ajouter la vitre. Tout d’abord, vous créez des ressources qui créent un effet de dégradé de verre. Ajoutez ces ressources de dégradés n’importe où dans le `Application.Resources` bloc :

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

     Ces ressources sont utilisées comme <xref:System.Windows.Shapes.Shape.Fill%2A> pour un rectangle que nous insérons dans le <xref:System.Windows.Controls.Grid> du modèle de bouton. Ajoutez le balisage en surbrillance suivant au modèle.

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

     Notez que le <xref:System.Windows.UIElement.Opacity%2A> du rectangle avec la `x:Name` propriété de « glassCube » a la valeur 0. par conséquent, lorsque vous exécutez l’exemple, le rectangle de transparence ne s’affiche pas en haut. Cela est dû au fait que nous ajouterons ultérieurement des déclencheurs au modèle lorsque l’utilisateur interagit avec le bouton. Toutefois, vous pouvez voir à quoi ressemble le bouton maintenant en remplaçant la <xref:System.Windows.UIElement.Opacity%2A> valeur par 1 et en exécutant l’application. Voir la figure suivante. Avant de passer à l’étape suivante, repassez la <xref:System.Windows.UIElement.Opacity%2A> valeur 0.

     ![Boutons personnalisés créés en utilisant XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-button-interactivity"></a>Créer une interactivité de bouton

Dans cette section, vous allez créer des déclencheurs de propriété et des déclencheurs d’événements pour modifier les valeurs de propriété et exécuter des animations en réponse aux actions de l’utilisateur, telles que le déplacement du pointeur de la souris sur le bouton et le clic.

Un moyen simple d’ajouter de l’interactivité (souris, survol, clic, etc.) consiste à définir des déclencheurs dans votre modèle ou style. Pour créer un <xref:System.Windows.Trigger> , vous définissez une propriété « condition » telle que : la <xref:System.Windows.UIElement.IsMouseOver%2A> valeur de la propriété du bouton est égale à `true` . Vous définissez ensuite les méthodes setter (actions) qui ont lieu lorsque la condition de déclencheur a la valeur true.

### <a name="to-create-button-interactivity"></a>Pour créer une interactivité de bouton

1. **Ajouter des déclencheurs de modèle :** Ajoutez le balisage en surbrillance à votre modèle.

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

2. **Ajouter des déclencheurs de propriété :** Ajoutez le balisage en surbrillance au `ControlTemplate.Triggers` bloc :

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     Appuyez sur F5 pour exécuter l’application et voir l’effet lorsque vous exécutez le pointeur de la souris sur les boutons.

3. **Ajouter un déclencheur de Focus :** Ensuite, nous allons ajouter des accesseurs set similaires pour gérer le cas où le bouton a le focus (par exemple, une fois que l’utilisateur clique dessus).

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

     Appuyez sur F5 pour exécuter l’application et cliquez sur l’un des boutons. Notez que le bouton reste en surbrillance après avoir cliqué dessus, car il a toujours le focus. Si vous cliquez sur un autre bouton, le nouveau bouton gagne le focus tandis que le dernier le perd.

4. **Ajouter des animations pour** <xref:System.Windows.UIElement.MouseEnter> **et** <xref:System.Windows.UIElement.MouseLeave> **:** Ensuite, nous ajoutons des animations aux déclencheurs.   Ajoutez la balise suivante n’importe où dans le `ControlTemplate.Triggers` bloc.

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

     Le rectangle de transparence se réduit lorsque le pointeur de la souris se déplace sur le bouton et retourne à la taille normale lorsque le pointeur quitte.

     Deux animations sont déclenchées lorsque le pointeur passe sur le bouton (l' <xref:System.Windows.UIElement.MouseEnter> événement est déclenché). Ces animations réduisent le rectangle de transparence le long des axes X et Y. Notez les propriétés sur les <xref:System.Windows.Media.Animation.DoubleAnimation> éléments, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> . <xref:System.Windows.Media.Animation.Timeline.Duration%2A>Spécifie que l’animation se produit pendant une demi-seconde et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> spécifie que la transparence est réduite de 10%.

     Le deuxième déclencheur d’événements ( <xref:System.Windows.UIElement.MouseLeave> ) arrête simplement le premier. Lorsque vous arrêtez un <xref:System.Windows.Media.Animation.Storyboard> , toutes les propriétés animées retournent à leurs valeurs par défaut. Par conséquent, lorsque l’utilisateur déplace le pointeur en dehors du bouton, le bouton revient à la façon dont il se trouvait avant le pointeur de la souris sur le bouton. Pour plus d’informations sur les animations, consultez [vue d’ensemble](../graphics-multimedia/animation-overview.md)de l’animation.

5. **Ajouter une animation pour lorsque l’utilisateur clique sur le bouton :** La dernière étape consiste à ajouter un déclencheur pour lorsque l’utilisateur clique sur le bouton. Ajoutez la balise suivante n’importe où dans le `ControlTemplate.Triggers` bloc :

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

     Appuyez sur F5 pour exécuter l’application, puis cliquez sur l’un des boutons. Lorsque vous cliquez sur un bouton, le rectangle de transparence tourne.

## <a name="summary"></a>Résumé
 Dans cette procédure pas à pas, vous avez effectué les exercices suivants :

- Ciblé a <xref:System.Windows.Style> vers un type d’objet ( <xref:System.Windows.Controls.Button> ).

- Contrôle des propriétés de base des boutons de l’application entière à l’aide de <xref:System.Windows.Style> .

- Ressources créées, comme des dégradés, à utiliser pour les valeurs de propriété des <xref:System.Windows.Style> accesseurs set.

- Personnaliser l’apparence des boutons dans toute l’application en appliquant un modèle aux boutons.

- Comportement personnalisé pour les boutons en réponse aux actions de l’utilisateur (telles que <xref:System.Windows.UIElement.MouseEnter> , <xref:System.Windows.UIElement.MouseLeave> et <xref:System.Windows.Controls.Primitives.ButtonBase.Click> ) qui incluent des effets d’animation.

## <a name="see-also"></a>Voir aussi

- [Créer un bouton à l'aide de Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [Application d'un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vue d'ensemble de l'animation](../graphics-multimedia/animation-overview.md)
- [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Vue d'ensemble des effets bitmap](../graphics-multimedia/bitmap-effects-overview.md)
