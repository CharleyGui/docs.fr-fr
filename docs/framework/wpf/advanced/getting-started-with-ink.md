---
title: Créer InkCanvas dans Visual Studio
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: b8087d6db04f7024b9ee48f28002bee04045a14b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737886"
---
# <a name="get-started-with-ink-in-wpf"></a>Prise en main de l’encre dans WPF

Windows Presentation Foundation (WPF) dispose d’une fonctionnalité d’encre qui facilite l’incorporation de l’encre numérique dans votre application.

## <a name="prerequisites"></a>Prerequisites

Pour utiliser les exemples suivants, commencez par installer [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). Il permet également de savoir comment écrire des applications WPF de base. Pour obtenir de l’aide sur la prise en main de WPF, consultez [procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="quick-start"></a>Démarrage rapide de la

Cette section vous aide à écrire une application WPF simple qui collecte de l’encre.

### <a name="got-ink"></a>Vous avez de l’encre ?

Pour créer une application WPF qui prend en charge l’encre :

1. Ouvrez Visual Studio.

2. Créez une **application WPF**.

   Dans la boîte de dialogue **nouveau projet** , développez la catégorie **installé** > **Visual C#**  ou **Visual Basic** > **Bureau Windows** . Ensuite, sélectionnez le modèle application **WPF (.NET Framework)** . Entrez un nom, puis sélectionnez **OK**.

   Visual Studio crée le projet, et *MainWindow. Xaml* s’ouvre dans le concepteur.

3. Tapez `<InkCanvas/>` entre les balises `<Grid>`.

   ![Concepteur XAML avec balise InkCanvas](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. Appuyez sur **F5** pour lancer votre application dans le débogueur.

5. À l’aide d’un stylet ou d’une souris, écrivez **Hello World** dans la fenêtre.

Vous avez écrit l’équivalent de l’encre d’une application « Hello World » avec seulement 12 séquences de touches !

### <a name="spice-up-your-app"></a>Agrémentez votre application

Nous allons tirer parti de certaines fonctionnalités de WPF. Remplacez tout ce qui se trouve entre les balises d’ouverture et de fermeture \<fenêtre > par le balisage suivant :

```xaml
<Page>
  <InkCanvas Name="myInkCanvas" MouseRightButtonUp="RightMouseUpHandler">
    <InkCanvas.Background>
      <LinearGradientBrush>
        <GradientStop Color="Yellow" Offset="0.0" />
          <GradientStop Color="Blue" Offset="0.5" />
            <GradientStop Color="HotPink" Offset="1.0" />
              </LinearGradientBrush>
    </InkCanvas.Background>
  </InkCanvas>
</Page>
```

Ce code XAML crée un arrière-plan de pinceau dégradé sur votre surface d’encrage.

![Couleurs de dégradé sur la surface d’entrée manuscrite dans l’application WPF](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a>Ajouter du code derrière le XAML

Bien que XAML facilite la conception de l’interface utilisateur, toute application réelle doit ajouter du code pour gérer les événements. Voici un exemple simple qui effectue un zoom avant sur l’encre en réponse à un clic droit à partir d’une souris.

1. Définissez le gestionnaire de `MouseRightButtonUp` dans votre code XAML :

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. Dans **Explorateur de solutions**, développez MainWindow. xaml et ouvrez le fichier code-behind (MainWindow.Xaml.cs ou MainWindow. Xaml. vb). Ajoutez le code de gestionnaire d’événements suivant :

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. Exécutez l'application. Ajoutez de l’encre, puis cliquez avec le bouton droit avec la souris ou effectuez une pression et une pression équivalente avec un stylet.

   L’affichage effectue un zoom avant chaque fois que vous cliquez avec le bouton droit de la souris.

### <a name="use-procedural-code-instead-of-xaml"></a>Utiliser le code de procédure au lieu de XAML

Vous pouvez accéder à toutes les fonctionnalités WPF à partir du code procédural. Suivez ces étapes pour créer une application « Hello Ink World » pour WPF qui n’utilise pas du tout XAML.

1. Créez un projet d’application console dans Visual Studio.

   Dans la boîte de dialogue **nouveau projet** , développez la catégorie **installé** > **Visual C#**  ou **Visual Basic** > **Bureau Windows** . Ensuite, sélectionnez le modèle application **console (.NET Framework)** . Entrez un nom, puis sélectionnez **OK**.

1. Collez le code suivant dans le fichier Program.cs ou Program. vb :

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. Ajoutez des références aux assemblys PresentationCore, PresentationFramework et WindowsBase en cliquant avec le bouton droit sur **références** dans **Explorateur de solutions** et en choisissant **Ajouter une référence**.

   ![Gestionnaire de références avec PresentationCore et PresentationFramework](./media/getting-started-with-ink/reference-manager-presentationcore-presentationframework.png)

1. Générez l’application en appuyant sur **F5**.

## <a name="see-also"></a>Voir aussi

- [Encre numérique](digital-ink.md)
- [Collecte d'encre](collecting-ink.md)
- [Reconnaissance d'écriture manuscrite](handwriting-recognition.md)
- [Stockage de l’encre](storing-ink.md)
