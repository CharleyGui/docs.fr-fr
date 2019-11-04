---
title: 'Procédure pas à pas : créer un bouton avec XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 6738b9e66c1223ea4ec50c070a421d119fd30bc4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458698"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>Procédure pas à pas : créer un bouton avec XAML

The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application. This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration. This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].

> [!IMPORTANT]
> This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Visual Studio. If you would prefer to learn how to use a designer to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).

The following figure shows the finished buttons.

![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-basic-buttons"></a>Create Basic Buttons

Let's start by creating a new project and adding a few buttons to the window.

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>To create a new WPF project and add buttons to the window

1. Démarrez Visual Studio.

2. **Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**. Find the **Windows Application (WPF)** template and name the project "AnimatedButton". This will create the skeleton for the application.

3. **Add basic default buttons:** All the files you need for this walkthrough are provided by the template. Open the Window1.xaml file by double clicking it in Solution Explorer. By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml. Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:

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

     Press F5 to run the application; you should see a set of buttons that looks like the following figure.

     ![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")

     Now that you have created the basic buttons, you are finished working in the Window1.xaml file. The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.

## <a name="set-basic-properties"></a>Set Basic Properties

Next, let's set some properties on these buttons to control the button appearance and layout. Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application. Application resources are conceptually similar to external Cascading Style Sheets (CSS) for Web pages; however, resources are much more powerful than Cascading Style Sheets (CSS), as you will see by the end of this walkthrough. To learn more about resources, see [XAML Resources](../advanced/xaml-resources.md).

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>To use styles to set basic properties on the buttons

1. **Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:

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

     Resource scope is determined by where you define the resource. Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application. To learn more about defining the scope of your resources, see [XAML Resources](../advanced/xaml-resources.md).

2. **Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block. Ce balisage crée une <xref:System.Windows.Style> qui s’applique à tous les boutons de l’application, en affectant à la <xref:System.Windows.FrameworkElement.Width%2A> des boutons la valeur 90 et la <xref:System.Windows.FrameworkElement.Margin%2A> la valeur 10 :

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     La propriété <xref:System.Windows.Style.TargetType%2A> spécifie que le style s’applique à tous les objets de type <xref:System.Windows.Controls.Button>. Chaque <xref:System.Windows.Setter> définit une valeur de propriété différente pour le <xref:System.Windows.Style>. Par conséquent, à ce stade, chaque bouton de l’application a une largeur de 90 et une marge de 10.  Si vous appuyez sur F5 pour exécuter l’application, la fenêtre suivante s’affiche.

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

     Directement sous le bloc `Application.Resources`, vous avez créé une ressource appelée « GrayBlueGradientBrush ». Cette ressource définit un dégradé horizontal. Cette ressource peut être utilisée en tant que valeur de propriété à n’importe quel endroit de l’application, y compris à l’intérieur de la méthode setter de style de bouton pour la propriété <xref:System.Windows.Controls.Control.Background%2A>. À présent, tous les boutons ont une valeur de propriété <xref:System.Windows.Controls.Control.Background%2A> de ce dégradé.

     Appuyez sur F5 pour exécuter l'application. Elle doit ressembler à ce qui suit.

     ![Boutons avec arrière-plan dégradé](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")

## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Créer un modèle qui définit l’apparence du bouton

Dans cette section, vous allez créer un modèle qui personnalise l’apparence (présentation) du bouton. La présentation du bouton est composée de plusieurs objets, y compris des rectangles et d’autres composants, pour donner un aspect unique au bouton.

Jusqu’à présent, le contrôle de l’apparence des boutons dans l’application a été limité à la modification des propriétés du bouton. Que se passe-t-il si vous souhaitez apporter des modifications plus radicales à l’apparence du bouton ? Les modèles permettent un contrôle puissant de la présentation d’un objet. Étant donné que les modèles peuvent être utilisés dans les styles, vous pouvez appliquer un modèle à tous les objets auxquels le style s’applique (dans cette procédure pas à pas, le bouton).

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Pour utiliser le modèle afin de définir l’apparence du bouton

1. **Configurez le modèle :** Comme les contrôles comme les <xref:System.Windows.Controls.Button> ont une propriété <xref:System.Windows.Controls.Control.Template%2A>, vous pouvez définir la valeur de propriété de modèle comme les autres valeurs de propriété que nous avons définies dans un <xref:System.Windows.Style> à l’aide d’un <xref:System.Windows.Setter>. Ajoutez le balisage en surbrillance suivant à votre style de bouton.

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

2. **Présentation du bouton modifier :** À ce stade, vous devez définir le modèle. Ajoutez le balisage en surbrillance suivant. Ce balisage spécifie deux éléments <xref:System.Windows.Shapes.Rectangle> avec des bords arrondis, suivis d’un <xref:System.Windows.Controls.DockPanel>. Le <xref:System.Windows.Controls.DockPanel> est utilisé pour héberger le <xref:System.Windows.Controls.ContentPresenter> du bouton. Un <xref:System.Windows.Controls.ContentPresenter> affiche le contenu du bouton. Dans cette procédure pas à pas, le contenu est de texte (« Button 1 », « Button 2 », « Button 3 »). Tous les composants de modèle (les rectangles et les <xref:System.Windows.Controls.DockPanel>) sont disposés à l’intérieur d’une <xref:System.Windows.Controls.Grid>.

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

3. **Ajoutez un GlassEffect au modèle :** Ensuite, vous allez ajouter la vitre. Tout d’abord, vous créez des ressources qui créent un effet de dégradé de verre. Ajoutez ces ressources de dégradés n’importe où dans le bloc `Application.Resources` :

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

     Notez que le <xref:System.Windows.UIElement.Opacity%2A> du rectangle avec la propriété `x:Name` de « glassCube » a la valeur 0. par conséquent, lorsque vous exécutez l’exemple, le rectangle de transparence ne s’affiche pas en haut. Cela est dû au fait que nous ajouterons ultérieurement des déclencheurs au modèle lorsque l’utilisateur interagit avec le bouton. Toutefois, vous pouvez voir à quoi ressemble le bouton en remplaçant la valeur de <xref:System.Windows.UIElement.Opacity%2A> par 1 et en exécutant l’application. Voir l'illustration suivante. Avant de passer à l’étape suivante, réaffectez la valeur 0 à la <xref:System.Windows.UIElement.Opacity%2A>.

     ![Boutons personnalisés qui ont été créés à l’aide de XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-button-interactivity"></a>Créer une interactivité de bouton

Dans cette section, vous allez créer des déclencheurs de propriété et des déclencheurs d’événements pour modifier les valeurs de propriété et exécuter des animations en réponse aux actions de l’utilisateur, telles que le déplacement du pointeur de la souris sur le bouton et le clic.

Un moyen simple d’ajouter de l’interactivité (souris, survol, clic, etc.) consiste à définir des déclencheurs dans votre modèle ou style. Pour créer un <xref:System.Windows.Trigger>, vous définissez une propriété « condition » telle que : le bouton <xref:System.Windows.UIElement.IsMouseOver%2A> valeur de la propriété est égal à `true`. Vous définissez ensuite les méthodes setter (actions) qui ont lieu lorsque la condition de déclencheur a la valeur true.

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

2. **Ajouter des déclencheurs de propriété :** Ajoutez le balisage en surbrillance au bloc `ControlTemplate.Triggers` :

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

4. **Ajoutez des animations pour**<xref:System.Windows.UIElement.MouseEnter> et <xref:System.Windows.UIElement.MouseLeave> **:** ensuite **,** nous ajoutons des animations aux déclencheurs. Ajoutez la balise suivante n’importe où dans le bloc `ControlTemplate.Triggers`.

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

     Deux animations sont déclenchées lorsque le pointeur passe sur le bouton (<xref:System.Windows.UIElement.MouseEnter> événement est déclenché). Ces animations réduisent le rectangle de transparence le long des axes X et Y. Notez les propriétés sur les éléments <xref:System.Windows.Media.Animation.DoubleAnimation>, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. L' <xref:System.Windows.Media.Animation.Timeline.Duration%2A> spécifie que l’animation se produit pendant une demi-seconde et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> spécifie que la transparence est réduite de 10%.

     Le deuxième déclencheur d’événements (<xref:System.Windows.UIElement.MouseLeave>) arrête simplement le premier. Lorsque vous arrêtez un <xref:System.Windows.Media.Animation.Storyboard>, toutes les propriétés animées retournent à leurs valeurs par défaut. Par conséquent, lorsque l’utilisateur déplace le pointeur en dehors du bouton, le bouton revient à la façon dont il se trouvait avant le pointeur de la souris sur le bouton. Pour plus d’informations sur les animations, consultez [vue d’ensemble](../graphics-multimedia/animation-overview.md)de l’animation.

5. **Ajouter une animation pour lorsque l’utilisateur clique sur le bouton :** La dernière étape consiste à ajouter un déclencheur pour lorsque l’utilisateur clique sur le bouton. Ajoutez la balise suivante n’importe où dans le bloc `ControlTemplate.Triggers` :

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

## <a name="summary"></a>Récapitulatif
 Dans cette procédure pas à pas, vous avez effectué les exercices suivants :

- Cibler une <xref:System.Windows.Style> vers un type d’objet (<xref:System.Windows.Controls.Button>).

- Contrôle des propriétés de base des boutons de l’application entière à l’aide de l' <xref:System.Windows.Style>.

- Ressources créées, comme des dégradés, à utiliser pour les valeurs de propriété des accesseurs set <xref:System.Windows.Style>.

- Personnaliser l’apparence des boutons dans toute l’application en appliquant un modèle aux boutons.

- Comportement personnalisé pour les boutons en réponse aux actions de l’utilisateur (telles que <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>et <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) qui incluaient les effets d’animation.

## <a name="see-also"></a>Voir aussi

- [Créer un bouton à l'aide de Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vue d’ensemble de l’animation](../graphics-multimedia/animation-overview.md)
- [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Vue d’ensemble des effets bitmap](../graphics-multimedia/bitmap-effects-overview.md)
