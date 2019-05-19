---
title: Générer une bibliothèque .NET Standard C# avec Visual Studio 2017
description: Découvrez comment créer une bibliothèque de classes .NET Standard écrite en C# à l’aide de Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 440ef2ed398b22262923422efd7f1259e3ee9b74
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633692"
---
# <a name="build-a-net-standard-library-with-c-and-the-net-core-sdk-in-visual-studio-2017"></a>Générer une bibliothèque .NET Standard avec C# et le kit SDK .NET Core dans Visual Studio 2017

Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application. Une bibliothèque de classes qui cible .NET Standard 2.0 permet à votre bibliothèque d’être appelée par n’importe quelle implémentation .NET qui prend en charge cette version de .NET Standard. Quand vous avez terminé votre bibliothèque de classes, vous pouvez décider de la distribuer ou non comme un composant tiers, ou de l’inclure ou non dans un composant groupé avec une ou plusieurs applications.

> [!NOTE]
> Pour obtenir la liste des versions de .NET Standard et des plateformes prises en charge, consultez [.NET Standard](../../standard/net-standard.md).

Dans cette rubrique, vous créez une bibliothèque d’utilitaire simple qui contient une seule méthode de gestion de chaîne. Vous l’implémentez en tant que [méthode d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md), pour pouvoir l’appeler comme s’il s’agissait d’un membre de la classe <xref:System.String>.

## <a name="creating-a-class-library-solution"></a>Création d'une solution de bibliothèque de classes

Commencez par créer une solution pour votre projet de bibliothèque de classes et ses projets connexes. Une solution Visual Studio sert simplement de conteneur pour un ou plusieurs projets. Pour créer la solution :

1. Dans la barre de menus de Visual Studio, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans la boîte de dialogue **Nouveau projet**, développez le nœud **Autres types de projets** et sélectionnez **Solutions Visual Studio**. Nommez la solution « ClassLibraryProjects » puis sélectionnez le bouton **OK**.

   ![Boîte de dialogue Nouveau projet avec nouvelle solution vide mise en surbrillance](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a>Création du projet de bibliothèque de classes

Créez votre projet de bibliothèque de classes :

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur la solution **ClassLibraryProjects** et, dans le menu contextuel, sélectionnez **Ajouter** > **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter un nouveau projet**, développez le nœud **Visual C#**, puis sélectionnez le nœud **.NET Standard** et choisissez le modèle de projet **Bibliothèque de classes (.NET Standard)**. Dans la zone de texte **Nom**, entrez « StringLibrary » comme nom de projet. Sélectionnez **OK** pour créer le projet de bibliothèque de classes.

   ![Boîte de dialogue Ajouter un nouveau projet bibliothèque](./media/library-with-visual-studio/add-new-library-project.png)

   Ensuite, la fenêtre de code s’ouvre dans l’environnement de développement Visual Studio.

   ![Fenêtre d’application Visual Studio montrant le code du modèle de bibliothèque de classes par défaut](./media/library-with-visual-studio/string-library-project.png)

1. Vérifiez que notre bibliothèque cible la version appropriée de .NET Standard. Dans la fenêtre **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de bibliothèque, puis sélectionnez **Propriétés**. La zone de texte **framework cible** indique que nous ciblons .NET Standard 2.0.

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/library-project-properties.png)

1. Remplacez le code de la fenêtre de code par le code suivant et enregistrez le fichier :

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   La bibliothèque de classes, `UtilityLibraries.StringLibrary`, contient une méthode nommée `StartsWithUpper`, qui retourne une valeur <xref:System.Boolean> qui indique si l’instance actuelle de la chaîne commence par une majuscule. La norme Unicode distingue les caractères minuscules des caractères majuscules. La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.

1. Dans la barre de menus, sélectionnez **Générer** > **Générer la solution**. Le projet devrait être compilé sans erreur.

   ![Volet de sortie indiquant que la génération a réussi](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a>Étape suivante

Vous avez créé la bibliothèque correctement. Comme vous n’avez appelé aucune de ses méthodes, vous ne savez pas si elle fonctionne comme prévu. L’étape suivante du développement de votre bibliothèque consiste à la tester en utilisant un [Projet de test unitaire](testing-library-with-visual-studio.md).
