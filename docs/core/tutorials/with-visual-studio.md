---
title: Créer une application console avec .NET Core dans Visual Studio
description: Découvrez comment créer une application console .NET Core avec C# ou Visual Basic à l’aide de Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 144d7bb087034839ad2cde2fa28a4961cff4321f
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306992"
---
# <a name="tutorial-create-a-net-core-console-application-in-visual-studio-2019"></a>Didacticiel : créer une application console .NET Core dans Visual Studio 2019

Ce didacticiel montre comment créer et exécuter une application console .NET Core dans Visual Studio 2019.

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2019 version 16,6 ou une version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **développement multiplateforme .net Core** installée. Le kit de développement logiciel (SDK) .NET Core 3,1 est automatiquement installé lorsque vous sélectionnez cette charge de travail.

  Pour plus d’informations, consultez la section [install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) de l’article [install the kit SDK .net Core](../install/sdk.md?pivots=os-windows) .

## <a name="create-the-app"></a>Créer l’application

<!-- markdownlint-disable MD025 -->

1. Ouvrez Visual Studio 2019.

1. Créez un projet d’application console .NET Core nommé « HelloWorld ».

   1. Dans la page de démarrage, choisissez **créer un nouveau projet**.

      ![Bouton créer un projet sélectionné dans la page de démarrage de Visual Studio](./media/with-visual-studio/start-window.png)

   1. Sur la page **créer un nouveau projet** , dans la zone de recherche, entrez **console** . Ensuite, choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme. Choisissez le modèle **application console (.net Core)** , puis choisissez **suivant**.

      ![Créer une fenêtre de projet avec les filtres sélectionnés](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > Si vous ne voyez pas les modèles .NET Core, vous n’avez probablement pas la charge de travail requise. Sous le message **vous ne trouvez pas ce que vous recherchez ?** , choisissez le lien **installer d’autres outils et fonctionnalités** . Le Visual Studio Installer s’ouvre. Assurez-vous que la charge de travail de **développement multiplateforme .net Core** est installée.

   1. Dans la page **configurer votre nouveau projet** , entrez **HelloWorld** dans la zone **nom du projet** . Choisissez ensuite **Créer**.

      ![Configurer votre nouvelle fenêtre de projet avec les champs nom du projet, emplacement et nom de la solution](./media/with-visual-studio/configure-new-project.png)

   Le modèle d’application console pour .NET Core définit une classe, `Program` , avec une méthode unique, `Main` , qui prend un <xref:System.String> tableau en tant qu’argument. `Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application. Tous les arguments de ligne de commande fournis au lancement de l’application sont disponibles dans le tableau *args*.

   Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.

   ```csharp
   using System;

   namespace HelloWorld
   {
       class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello World!");
           }
       }
   }
   ```

   ```vb
   Imports System

   Module Program
       Sub Main(args As String())
           Console.WriteLine("Hello World!")
       End Sub
   End Module
   ```

   Le modèle crée une application « Hello World » simple. Elle appelle la <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> méthode pour afficher « Hello World ! » dans la fenêtre de console.

## <a name="run-the-app"></a>Exécuter l’application

1. Pour exécuter le programme, choisissez **HelloWorld** dans la barre d’outils, ou appuyez sur **F5**.

   ![Barre d’outils Visual Studio avec le bouton Exécuter HelloWorld sélectionné](./media/with-visual-studio/run-program.png)

   Une fenêtre de console s’ouvre avec le texte « Hello World ! » imprimé à l’écran et certaines informations de débogage de Visual Studio.

   ![Fenêtre de console affichant « Hello World Press any key to continue »](./media/with-visual-studio/hello-world-console.png)

1. Appuyez sur une touche pour fermer la fenêtre de console.

## <a name="enhance-the-app"></a>Améliorer l’application

Améliorez l’application pour inviter l’utilisateur à entrer son nom et l’afficher avec la date et l’heure. Les instructions suivantes modifient l’application et l’exécutent à nouveau :

1. Remplacez le contenu de la `Main` méthode, qui est actuellement simplement la ligne qui appelle `Console.WriteLine` , par le code suivant :

   [!code-csharp[GettingStarted#1](./snippets/with-visual-studio/csharp/Program.cs#1)]
   [!code-vb[GettingStarted#1](./snippets/with-visual-studio/vb/Program.vb#1)]

   Ce code affiche « What is your name? ». dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche Entrée. Elle stocke cette chaîne dans une variable nommée `name` . Elle récupère également la valeur de la <xref:System.DateTime.Now?displayProperty=nameWithType> propriété, qui contient l’heure locale actuelle, et l’assigne à une variable nommée `date` ( `currentDate` dans Visual Basic). Enfin, il affiche ces valeurs dans la fenêtre de console.

   `\n`( `vbCrLf` En Visual Basic) représente un caractère de saut de ligne.

   Le signe dollar ( `$` ) devant une chaîne vous permet de placer des expressions telles que des noms de variable entre accolades dans la chaîne. La valeur de l’expression est insérée dans la chaîne à la place de l’expression. Cette syntaxe est appelée « [chaînes interpolées](../../csharp/language-reference/tokens/interpolated.md)».

1. Pour exécuter le programme, choisissez **HelloWorld** dans la barre d’outils, ou appuyez sur **F5**.

1. Répondez à l’invite en entrant un nom et en appuyant sur la touche **entrée** .

   ![Fenêtre de console avec la sortie du programme modifié](./media/with-visual-studio/hello-world-update.png)

1. Appuyez sur une touche pour fermer la fenêtre de console.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez créé une application .NET Core. Dans le didacticiel suivant, vous allez déboguer l’application.

> [!div class="nextstepaction"]
> [Déboguer une application console .NET Core dans Visual Studio](debugging-with-visual-studio.md)
