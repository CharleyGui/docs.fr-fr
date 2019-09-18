---
title: Application Hello World .NET Core avec Visual Basic dans Visual Studio 2017
description: Découvrez comment générer une application de console .NET Core simple avec Visual Basic à l’aide de Visual Studio 2017.
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: b4f3cc055f73332db1348ef35174beab614df147
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039613"
---
# <a name="build-a-visual-basic-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>Générer une application Visual Basic Hello World avec le SDK .NET Core dans Visual Studio 2017

Cette rubrique fournit une introduction pas à pas pour la création, le débogage et la publication d’une application de console .NET Core à l’aide de Visual Basic dans Visual Studio 2017. Visual Studio 2017 fournit un environnement de développement complet pour la création d’applications .NET Core. Tant que l’application n’a pas de dépendances spécifiques à la plateforme, elle peut s’exécuter sur n’importe quelle plateforme ciblée par .NET Core et sur tout système où .NET Core est installé.

## <a name="prerequisites"></a>Prérequis

[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), avec la charge de travail « Développement multiplateforme .Net Core » installée. Vous pouvez développer votre application avec .NET Core 2,1 ou versions ultérieures.

Pour plus d’informations, consultez [Configuration requise pour .NET Core sur Windows](../windows-prerequisites.md).

## <a name="a-simple-hello-world-application"></a>Une application Hello World simple

Commencez par créer une application console « Hello World » simple. Procédez comme suit :

1. Lancez Visual Studio 2017. Sélectionnez **Fichier** > **Nouveau** > **Projet** dans la barre de menus. Dans la boîte de dialogue *Nouveau projet*\*, sélectionnez le nœud **Visual Basic** suivi du nœud **.NET Core**. Ensuite, sélectionnez le modèle de projet **Application console (.NET Core)** . Dans la zone de texte **Nom**, tapez « HelloWorld ». Sélectionnez le bouton **OK**.

   ![Boîte de dialogue Nouveau projet avec Application console sélectionné](./media/vb-with-visual-studio/visual-studio-new-project.png)

1. Visual Studio utilise le modèle pour créer votre projet. Le modèle d’application console Visual Basic pour .NET Core définit automatiquement une classe, `Program`, avec une méthode unique, `Main`, qui accepte un tableau de <xref:System.String> comme argument. `Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application. Tous les arguments de ligne de commande fournis au lancement de l’application sont disponibles dans le tableau *args*.

   ![Visual Studio et le nouveau projet HelloWorld](./media/vb-with-visual-studio/visual-studio-main-window.png)

   Le modèle crée une application « Hello World » simple. Il appelle la méthode <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> pour afficher la chaîne littérale « Hello World ! » dans la fenêtre de console. En sélectionnant le bouton **HelloWorld** avec la flèche verte dans la barre d’outils, vous pouvez exécuter le programme en mode débogage. Si vous le faites, la fenêtre de console est visible seulement pendant un court intervalle de temps avant sa fermeture. Cela se produit, car la méthode `Main` se termine et l’application se termine dès que l’instruction unique de la méthode `Main` s’exécute.

1. Pour que la console ne se ferme pas d'elle-même, ajoutez le code suivant immédiatement après l’appel de la méthode <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> :

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

   Ce code invite l’utilisateur à appuyer sur une touche. Le programme s'arrête lorsque l’utilisateur appuie sur une touche.

1. Dans la barre de menus, sélectionnez **Générer** > **Générer la solution**. Ceci compile votre programme en un langage intermédiaire, qui est ensuite converti en code binaire par un compilateur juste-à-temps (JIT).

1. Exécutez le programme en sélectionnant le bouton **HelloWorld** avec la flèche verte dans la barre d’outils.

   ![Fenêtre de console affichant « Hello World Press any key to continue »](./media/with-visual-studio/hello-world-console.png)

1. Appuyez sur une touche pour fermer la fenêtre de console.

## <a name="enhancing-the-hello-world-application"></a>Amélioration de l’application Hello World

Améliorez votre application pour inviter l’utilisateur à entrer son nom, et pour l’afficher avec la date et l’heure. Pour modifier et tester le programme, procédez comme suit :

1. Entrez le code Visual Basic suivant dans la fenêtre de code immédiatement après le crochet ouvrant qui suit la ligne `Sub Main(args As String())` et avant le premier crochet fermant :

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Ce code remplace le contenu de la méthode `Main`.

   ![Fichier du programme Visual Studio avec la méthode Main mise à jour](./media/vb-with-visual-studio/visual-basic-code-window.png)

   Ce code affiche « What is your name? ». dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche Entrée. Il stocke cette chaîne dans une variable nommée `name`. Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `currentDate`. Enfin, elle utilise une [chaîne interpolée](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) pour afficher ces valeurs dans la fenêtre de console.

1. Recompilez le programme en choisissant **Build** > **Générer la solution**.

1. Exécutez le programme en mode débogage dans Visual Studio en sélectionnant la flèche verte dans la barre d’outils, en appuyant sur F5 ou en choisissant l’élément de menu **Déboguer** > **Démarrer le débogage**. Répondez à l’invite en entrant un nom et en appuyant sur la touche Entrée.

   ![Fenêtre de console avec la sortie du programme modifié](./media/with-visual-studio/hello-world-update.png)

1. Appuyez sur une touche pour fermer la fenêtre de console.

Vous avez créé et exécuté votre application. Pour développer une application professionnelle, appliquez quelques étapes supplémentaires pour rendre votre application prête à être publiée :

- Pour déboguer votre application, consultez [Déboguer votre application .NET Core Hello World à l’aide de Visual Studio 2017](debugging-with-visual-studio.md).

- Pour publier une version distribuable de votre application, consultez [Publier votre application .NET Core Hello World avec Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="related-topics"></a>Rubriques connexes

Au lieu d’une application console, vous pouvez créer une bibliothèque de classes .NET Standard avec Visual Basic, .NET Core et Visual Studio 2017. Pour une introduction pas à pas, voir [Générer une bibliothèque .NET Standard avec Visual Basic et le kit SDK .NET Core dans Visual Studio 2017](vb-library-with-visual-studio.md).
