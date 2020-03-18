---
title: Construire une bibliothèque de classe Standard .NET à Visual Studio
description: Apprenez à construire une bibliothèque de classe standard .NET écrite en C ou Visual Basic à l’aide de Visual Studio
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714018"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a>Construire une bibliothèque .NET Standard à Visual Studio

Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application. Une bibliothèque de classe qui cible .NET Standard 2.0 permet à votre bibliothèque d’être appelée par toute implémentation .NET qui prend en charge cette version de .NET Standard. Quand vous avez terminé votre bibliothèque de classes, vous pouvez décider de la distribuer ou non comme un composant tiers, ou de l’inclure ou non dans un composant groupé avec une ou plusieurs applications.

> [!NOTE]
> Pour une liste de versions .NET Standard et les plates-formes qu’ils prennent en charge, voir [.NET Standard](../../standard/net-standard.md).

Dans cette rubrique, vous créez une bibliothèque d’utilitaire simple qui contient une seule méthode de gestion de chaîne. Vous l’implémentez en tant que [méthode d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md), pour pouvoir l’appeler comme s’il s’agissait d’un membre de la classe <xref:System.String>.

## <a name="create-a-visual-studio-solution"></a>Créer une solution Visual Studio

Commencez par créer une solution vierge pour mettre le projet de bibliothèque de classe. Une solution Visual Studio sert de conteneur pour un ou plusieurs projets. Vous ajouterez des projets supplémentaires et liés à la même solution si vous continuez avec la série de tutoriels.

Pour créer la solution vierge :

1. Ouvrez Visual Studio.

2. Sur la fenêtre de départ, choisissez **Créer un nouveau projet**.

3. Sur la **page Créer un nouveau projet,** entrez la **solution** dans la zone de recherche. Choisissez le modèle **de solution Vierge,** puis choisissez **Next**.

   ![Modèle Solution vide dans Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. Sur la configuration de votre nouvelle page **de projet,** entrez **ClassLibraryProjets** dans la boîte **de nom du projet.** Ensuite, choisissez **Créer**.

> [!TIP]
> Vous pouvez également sauter cette étape et laisser Visual Studio créer la solution pour vous lorsque vous créez le projet dans la prochaine étape. Recherchez les options de solution sur la configuration de votre nouvelle page **de projet.**

## <a name="create-a-class-library-project"></a>Créer un projet de bibliothèque de classes

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Ajoutez un nouveau projet de bibliothèque de classe standard CMD .NET nommé « StringLibrary » à la solution.

   1. Cliquez à droite sur la solution dans **Solution Explorer** et sélectionnez **Ajouter** > **un nouveau projet**.

   1. Sur la page **Ajouter un nouveau projet,** entrez la **bibliothèque** dans la boîte de recherche. Choisissez **C dans** la liste linguistique, puis choisissez toutes les **plates-formes** de la liste de la plate-forme. Choisissez le modèle **de bibliothèque de classe (.NET Standard),** puis choisissez **Next**.

   1. Sur la configuration de votre nouvelle page **de projet,** entrez **StringLibrary** dans la boîte **de nom du projet.** Ensuite, choisissez **Créer**.

1. Vérifiez que la bibliothèque cible la version correcte de .NET Standard. Cliquez à droite sur le projet de bibliothèque dans **Solution Explorer**, puis sélectionnez **Propriétés**. La boîte de texte **Target Framework** montre que le projet cible .NET Standard 2.0.

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/library-project-properties.png)

1. Remplacez le code de la fenêtre de code par le code suivant et enregistrez le fichier :

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   La bibliothèque `UtilityLibraries.StringLibrary`de classe, `StartsWithUpper`, contient une méthode nommée . Cette méthode <xref:System.Boolean> renvoie une valeur qui indique si l’instance de chaîne actuelle commence par un caractère majuscule. La norme Unicode distingue les caractères minuscules des caractères majuscules. La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.

1. Sur la barre de menu, sélectionnez **Build** > **Build Solution**.

# <a name="visual-basic"></a>[Base visuelle](#tab/vb)

1. Ajoutez un nouveau projet de bibliothèque de classe Visual Basic .NET Standard nommé "StringLibrary" à la solution.

   1. Cliquez à droite sur la solution dans **Solution Explorer** et sélectionnez **Ajouter** > **un nouveau projet**.

   1. Sur la page **Ajouter un nouveau projet,** entrez la **bibliothèque** dans la boîte de recherche. Choisissez **Visual Basic** dans la liste de langue, puis choisissez toutes les **plates-formes** de la liste De la plate-forme. Choisissez le modèle **de bibliothèque de classe (.NET Standard),** puis choisissez **Next**.

   1. Sur la configuration de votre nouvelle page **de projet,** entrez **StringLibrary** dans la boîte **de nom du projet.** Ensuite, choisissez **Créer**.

1. Vérifiez que la bibliothèque cible la version correcte de .NET Standard. Cliquez à droite sur le projet de bibliothèque dans **Solution Explorer**, puis sélectionnez **Propriétés**. La boîte de texte **Target Framework** montre que le projet cible .NET Standard 2.0.

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/vb/library-project-properties.png)

1. Dans le dialogue **Propriétés,** effacer le texte dans la boîte de texte **Root namespace.** Pour chaque projet, Visual Basic crée automatiquement un espace de nom qui correspond au nom du projet. Dans ce tutoriel, vous définissez un espace [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) de nom de haut niveau en utilisant le mot clé dans le fichier de code.

1. Remplacez le code de la fenêtre de code par le code suivant et enregistrez le fichier :

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   La bibliothèque `UtilityLibraries.StringLibrary`de classe, `StartsWithUpper`, contient une méthode nommée . Cette méthode <xref:System.Boolean> renvoie une valeur qui indique si l’instance de chaîne actuelle commence par un caractère majuscule. La norme Unicode distingue les caractères minuscules des caractères majuscules. La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.

1. Sur la barre de menu, sélectionnez **Build** > **Build Solution**.

---

   Le projet devrait être compilé sans erreur.

## <a name="next-steps"></a>Étapes suivantes

Vous avez créé la bibliothèque correctement. Comme vous n’avez appelé aucune de ses méthodes, vous ne savez pas si elle fonctionne comme prévu. La prochaine étape dans le développement de votre bibliothèque est de la tester.

> [!div class="nextstepaction"]
> [Créer un projet d’essai unitaire](testing-library-with-visual-studio.md)
