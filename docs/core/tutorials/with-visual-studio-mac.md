---
title: Créer une application console .NET Core à l’aide de Visual Studio pour Mac
description: Découvrez comment créer une application console .NET Core à l’aide de Visual Studio pour Mac.
ms.date: 06/02/2020
ms.openlocfilehash: 9cab838eaab2c59d8a0270267514f57acb7c60fb
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84811668"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-for-mac"></a>Didacticiel : créer une application console .NET Core à l’aide de Visual Studio pour Mac

Ce didacticiel montre comment créer et exécuter une application console .NET Core à l’aide de Visual Studio pour Mac.

> [!NOTE]
> Vos commentaires sont extrêmement précieux. Il existe deux moyens de transmettre vos commentaires à l’équipe de développement sur Visual Studio pour Mac :
>
> * Dans Visual Studio pour Mac, sélectionnez **aide**  >  **signaler un problème** dans le menu ou **signaler un problème** dans l’écran d’accueil, qui ouvre une fenêtre pour l’enregistrement d’un rapport de bogue. Vous pouvez effectuer le suivi de vos commentaires dans le portail de la [communauté des développeurs](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Pour faire une suggestion, sélectionnez **aide**  >  **fournir une suggestion** dans le menu ou **fournissez une suggestion** à partir de l’écran d’accueil, qui vous permet de vous rendre sur la [page Web de la communauté des développeurs Visual Studio pour Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Prérequis

* [Visual Studio pour Mac version 8,6 ou ultérieure](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Sélectionnez l’option d’installation de .NET Core. L’installation de Xamarin est facultative pour le développement .NET Core. Pour plus d’informations, consultez les ressources suivantes :

  * [Didacticiel : installer Visual Studio pour Mac](/visualstudio/mac/installation).
  * [Versions MacOS prises en charge](../install/dependencies.md?pivots=os-macos).
  * [Versions de .net Core prises en charge par Visual Studio pour Mac](/visualstudio/mac/net-core-support).

## <a name="create-the-app"></a>Créer l’application

Créez un projet d’application console .NET Core nommé « HelloWorld ».

1. Démarrez Visual Studio pour Mac.

1. Sélectionnez **nouveau** dans la fenêtre démarrer.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Bouton Nouveau sur l’écran Démarrer de Visual Studio pour Mac":::

1. Dans la boîte de dialogue **nouveau projet** , sélectionnez **application** sous le nœud **Web et console** . Sélectionnez le modèle **application console** , puis sélectionnez **suivant**.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="Liste des modèles Nouveau projet":::

1. Dans la liste déroulante **Framework cible** de la boîte de dialogue **configurer votre nouvelle application console** , sélectionnez **.net Core 3,1**, puis sélectionnez **suivant**.

   :::image type="content" source="media/with-visual-studio-mac/target-framework.png" alt-text="Sélectionner la version cible de .NET Framework":::

1. Tapez « HelloWorld » comme **nom de projet**, puis sélectionnez **créer**.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="Boîte de dialogue de configuration de votre nouvelle application console":::

Le modèle crée une application « Hello World » simple. Elle appelle la <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> méthode pour afficher « Hello World ! » dans la fenêtre de terminal.

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

`Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application. Les arguments de ligne de commande fournis lorsque l’application est lancée sont disponibles dans le `args` tableau.

## <a name="run-the-app"></a>Exécuter l’application

1. Appuyez sur <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>commande</kbd> + <kbd>entrée</kbd>) pour exécuter l’application sans débogage.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="Le terminal affiche Hello World !":::

1. Fermez la fenêtre de **Terminal** .

## <a name="enhance-the-app"></a>Améliorer l’application

Améliorez l’application pour inviter l’utilisateur à entrer son nom et l’afficher avec la date et l’heure.

1. Dans *Program.cs*, remplacez le contenu de la `Main` méthode, qui est la ligne qui appelle `Console.WriteLine` , par le code suivant :

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   Ce code affiche « What is your name? ». dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche <kbd>entrée</kbd> . Elle stocke cette chaîne dans une variable nommée `name` . Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`. Enfin, il affiche ces valeurs dans la fenêtre de console.

   `\n`Représente un caractère de saut de ligne.

   Le signe dollar ( `$` ) devant une chaîne vous permet de placer des expressions telles que des noms de variable entre accolades dans la chaîne. La valeur de l’expression est insérée dans la chaîne à la place de l’expression. Cette syntaxe est appelée « [chaînes interpolées](../../csharp/language-reference/tokens/interpolated.md)».

1. Appuyez sur <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>commande</kbd> + <kbd>entrée</kbd>) pour exécuter l’application.

1. Répondez à l’invite en entrant un nom et en appuyant sur <kbd>entrée</kbd>.

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="Le terminal affiche la sortie du programme modifié":::

1. Fermez le terminal.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez créé une application console .NET Core. Dans le didacticiel suivant, vous allez déboguer l’application.

> [!div class="nextstepaction"]
> [Déboguer une application console .NET Core dans Visual Studio](debugging-with-visual-studio-mac.md)
