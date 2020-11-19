---
title: Créer une application console .NET à l’aide de Visual Studio
description: Découvrez comment créer une application console .NET avec C# ou Visual Basic à l’aide de Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: e395122e59f17ed66bbd9d83b01610993f663ce1
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94915918"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio"></a>Didacticiel : créer une application console .NET à l’aide de Visual Studio

Ce didacticiel montre comment créer et exécuter une application console .NET dans Visual Studio 2019.

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2019 version 16,8 ou une version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **développement multiplateforme .net Core** installée. Le kit de développement logiciel (SDK) .NET 5,0 est automatiquement installé lorsque vous sélectionnez cette charge de travail.

  Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) .net avec Visual Studio](../install/windows.md#install-with-visual-studio).

## <a name="create-the-app"></a>Créer l’application

Créez un projet d’application console .NET nommé « HelloWorld ».

1. Démarrez Visual Studio 2019.

1. Sélectionnez **Outils**  >  **options**  >  **environnement**  >  **Aperçu fonctionnalités**, puis sélectionnez **Afficher tous les modèles .net core dans le nouveau projet (nécessite un redémarrage)**.

   :::image type="content" source="media/with-visual-studio/dotnet-options.png" alt-text="Afficher tous les modèles .NET (option)":::

1. Fermez et rouvrez Visual Studio.

1. Dans la page de démarrage, choisissez **créer un nouveau projet**.

   :::image type="content" source="./media/with-visual-studio/start-window.png" alt-text="Bouton créer un projet sélectionné dans la page de démarrage de Visual Studio":::

1. Sur la page **créer un nouveau projet** , dans la zone de recherche, entrez **console** . Ensuite, choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme. Choisissez le modèle **application console** , puis cliquez sur **suivant**.

   :::image type="content" source="./media/with-visual-studio/create-new-project.png" alt-text="Créer une fenêtre de projet avec les filtres sélectionnés":::

   > [!TIP]
   > Si vous ne voyez pas les modèles .NET, vous n’avez probablement pas la charge de travail requise. Sous le message **vous ne trouvez pas ce que vous recherchez ?** , choisissez le lien **installer d’autres outils et fonctionnalités** . Le Visual Studio Installer s’ouvre. Assurez-vous que la charge de travail de **développement multiplateforme .net Core** est installée.

1. Dans la boîte de dialogue **configurer votre nouveau projet** , entrez **HelloWorld** dans la zone **nom du projet** . Choisissez ensuite **Créer**.

   :::image type="content" source="./media/with-visual-studio/configure-new-project.png" alt-text="Configurer votre nouvelle fenêtre de projet avec les champs nom du projet, emplacement et nom de la solution":::

1. Dans la boîte de dialogue **informations supplémentaires** , sélectionnez **.net 5,0 (actuel)**, puis sélectionnez **créer**.

   :::image type="content" source="media/with-visual-studio/additional-info.png" alt-text="Boîte de dialogue d’informations supplémentaires":::

Le modèle crée une application « Hello World » simple. Elle appelle la <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> méthode pour afficher « Hello World ! » dans la fenêtre de console.

Le code du modèle définit une classe, `Program` , avec une méthode unique, `Main` , qui prend un <xref:System.String> tableau en tant qu’argument :

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

`Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application. Tous les arguments de ligne de commande fournis au lancement de l’application sont disponibles dans le tableau *args*.

Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.

## <a name="run-the-app"></a>Exécuter l’application

1. Appuyez sur <kbd>CTRL</kbd> + <kbd>F5</kbd> pour exécuter le programme sans débogage.

   Une fenêtre de console s’ouvre avec le texte « Hello World ! » imprimé à l’écran.

   :::image type="content" source="./media/with-visual-studio/hello-world-console.png" alt-text="Fenêtre de console affichant « Hello World Press any key to continue »":::

1. Appuyez sur une touche pour fermer la fenêtre de console.

## <a name="enhance-the-app"></a>Améliorer l’application

Améliorez l’application pour inviter l’utilisateur à entrer son nom et l’afficher avec la date et l’heure.

1. Dans *Program.cs* ou *Program. vb*, remplacez le contenu de la `Main` méthode, qui est la ligne qui appelle `Console.WriteLine` , par le code suivant :

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   Ce code affiche une invite dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche <kbd>entrée</kbd> . Elle stocke cette chaîne dans une variable nommée `name` . Elle récupère également la valeur de la <xref:System.DateTime.Now?displayProperty=nameWithType> propriété, qui contient l’heure locale actuelle, et l’assigne à une variable nommée `date` ( `currentDate` dans Visual Basic). Et affiche ces valeurs dans la fenêtre de console. Enfin, il affiche une invite dans la fenêtre de console et appelle la <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> méthode pour attendre l’entrée utilisateur.

   `\n`( `vbCrLf` En Visual Basic) représente un caractère de saut de ligne.

   Le signe dollar ( `$` ) devant une chaîne vous permet de placer des expressions telles que des noms de variable entre accolades dans la chaîne. La valeur de l’expression est insérée dans la chaîne à la place de l’expression. Cette syntaxe est appelée « [chaînes interpolées](../../csharp/language-reference/tokens/interpolated.md)».

1. Appuyez sur <kbd>CTRL</kbd> + <kbd>F5</kbd> pour exécuter le programme sans débogage.

1. Répondez à l’invite en entrant un nom et en appuyant sur la touche <kbd>entrée</kbd> .

   :::image type="content" source="./media/with-visual-studio/hello-world-update.png" alt-text="Fenêtre de console avec la sortie du programme modifié":::

1. Appuyez sur une touche pour fermer la fenêtre de console.

## <a name="additional-resources"></a>Ressources supplémentaires

- [Versions actuelles et versions de support à long terme](../releases-and-support.md#net-core-and-net-5-version-lifecycles)

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez créé une application console .NET. Dans le didacticiel suivant, vous allez déboguer l’application.

> [!div class="nextstepaction"]
> [Débogage d’une application console .NET à l’aide de Visual Studio](debugging-with-visual-studio.md)
