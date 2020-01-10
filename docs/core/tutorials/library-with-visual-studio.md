---
title: Créer une bibliothèque de classes .NET Standard dans Visual Studio
description: Découvrez comment créer une bibliothèque de classes .NET Standard écrite dans C# ou Visual Basic à l’aide de Visual Studio
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714018"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a>Créer une bibliothèque de .NET Standard dans Visual Studio

Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application. Une bibliothèque de classes qui cible .NET Standard 2,0 permet à votre bibliothèque d’être appelée par n’importe quelle implémentation .NET qui prend en charge cette version de .NET Standard. Quand vous avez terminé votre bibliothèque de classes, vous pouvez décider de la distribuer ou non comme un composant tiers, ou de l’inclure ou non dans un composant groupé avec une ou plusieurs applications.

> [!NOTE]
> Pour obtenir la liste des versions de .NET Standard et les plateformes qu’elles prennent en charge, consultez [.NET standard](../../standard/net-standard.md).

Dans cette rubrique, vous créez une bibliothèque d’utilitaire simple qui contient une seule méthode de gestion de chaîne. Vous l’implémentez en tant que [méthode d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md), pour pouvoir l’appeler comme s’il s’agissait d’un membre de la classe <xref:System.String>.

## <a name="create-a-visual-studio-solution"></a>Créer une solution Visual Studio

Commencez par créer une solution vide dans laquelle placer le projet de bibliothèque de classes. Une solution Visual Studio sert de conteneur pour un ou plusieurs projets. Vous ajouterez des projets connexes supplémentaires à la même solution si vous continuez avec la série de didacticiels.

Pour créer la solution vide :

1. Ouvrez Visual Studio.

2. Dans la fenêtre de démarrage, choisissez **Créer un projet**.

3. Dans la page **créer un nouveau projet** , entrez **solution** dans la zone de recherche. Choisissez le modèle de **solution vide** , puis cliquez sur **suivant**.

   ![Modèle Solution vide dans Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. Dans la page **configurer votre nouveau projet** , entrez **ClassLibraryProjects** dans la zone **nom du projet** . Choisissez ensuite **Créer**.

> [!TIP]
> Vous pouvez également ignorer cette étape et laisser Visual Studio créer la solution pour vous quand vous créez le projet à l’étape suivante. Recherchez les options de la solution dans la page **configurer votre nouveau projet** .

## <a name="create-a-class-library-project"></a>Créer un projet de bibliothèque de classes

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Ajoutez un nouveau C# projet de bibliothèque de classes .NET standard nommé « StringLibrary » à la solution.

   1. Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter** > **nouveau projet**.

   1. Dans la page **Ajouter un nouveau projet** , entrez **bibliothèque** dans la zone de recherche. Choisissez **C#** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme. Choisissez le modèle **bibliothèque de classes (.NET standard)** , puis choisissez **suivant**.

   1. Dans la page **configurer votre nouveau projet** , entrez **StringLibrary** dans la zone **nom du projet** . Choisissez ensuite **Créer**.

1. Assurez-vous que la bibliothèque cible la version correcte de .NET Standard. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de bibliothèque, puis sélectionnez **Propriétés**. La zone de texte de la version **cible du .NET Framework** indique que le projet cible .NET standard 2,0.

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/library-project-properties.png)

1. Remplacez le code de la fenêtre de code par le code suivant et enregistrez le fichier :

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   La bibliothèque de classes, `UtilityLibraries.StringLibrary`, contient une méthode nommée `StartsWithUpper`. Cette méthode retourne une valeur <xref:System.Boolean> qui indique si l’instance de chaîne en cours commence par un caractère majuscule. La norme Unicode distingue les caractères minuscules des caractères majuscules. La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.

1. Dans la barre de menus, sélectionnez **Générer** > **Générer la solution**.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Ajoutez un nouveau Visual Basic .NET Standard projet de bibliothèque de classes nommé « StringLibrary » à la solution.

   1. Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter** > **nouveau projet**.

   1. Dans la page **Ajouter un nouveau projet** , entrez **bibliothèque** dans la zone de recherche. Choisissez **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme. Choisissez le modèle **bibliothèque de classes (.NET standard)** , puis choisissez **suivant**.

   1. Dans la page **configurer votre nouveau projet** , entrez **StringLibrary** dans la zone **nom du projet** . Choisissez ensuite **Créer**.

1. Assurez-vous que la bibliothèque cible la version correcte de .NET Standard. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de bibliothèque, puis sélectionnez **Propriétés**. La zone de texte de la version **cible du .NET Framework** indique que le projet cible .NET standard 2,0.

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/vb/library-project-properties.png)

1. Dans la boîte de dialogue **Propriétés** , effacez le texte de la zone de texte **espace de noms racine** . Pour chaque projet, Visual Basic crée automatiquement un espace de noms qui correspond au nom du projet. Dans ce didacticiel, vous définissez un espace de noms de niveau supérieur à l’aide du mot clé [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) dans le fichier de code.

1. Remplacez le code de la fenêtre de code par le code suivant et enregistrez le fichier :

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   La bibliothèque de classes, `UtilityLibraries.StringLibrary`, contient une méthode nommée `StartsWithUpper`. Cette méthode retourne une valeur <xref:System.Boolean> qui indique si l’instance de chaîne en cours commence par un caractère majuscule. La norme Unicode distingue les caractères minuscules des caractères majuscules. La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.

1. Dans la barre de menus, sélectionnez **Générer** > **Générer la solution**.

---

   Le projet devrait être compilé sans erreur.

## <a name="next-steps"></a>Étapes suivantes :

Vous avez créé la bibliothèque correctement. Comme vous n’avez appelé aucune de ses méthodes, vous ne savez pas si elle fonctionne comme prévu. L’étape suivante du développement de votre bibliothèque consiste à la tester.

> [!div class="nextstepaction"]
> [Créer un projet de test unitaire](testing-library-with-visual-studio.md)
