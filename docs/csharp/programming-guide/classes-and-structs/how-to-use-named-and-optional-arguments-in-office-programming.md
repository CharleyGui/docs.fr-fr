---
title: Guide pratique pour utiliser des arguments nommés et facultatifs dans la programmation Office-Guide de programmation C#
description: Découvrez comment utiliser des arguments nommés et des arguments facultatifs pour faciliter l’accès aux interfaces COM, telles que les API Microsoft Office Automation.
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: de0545131385c13a79fd35df74e3a04da98ad8fb
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512474"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>Comment utiliser des arguments nommés et facultatifs dans la programmation Office (Guide de programmation C#)

Les arguments nommés et les arguments facultatifs, qui ont été introduits avec C#4, rendent la programmation en C# plus pratique, plus souple et plus lisible. De plus, ces fonctionnalités facilitent considérablement l’accès aux interfaces COM, telles que les API Microsoft Office Automation.

Dans l’exemple suivant, la méthode [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) a seize paramètres qui représentent les caractéristiques d’une table, comme le nombre de colonnes et de lignes, la mise en forme, les bordures, les polices et les couleurs. Ces seize paramètres sont facultatifs, car la plupart du temps, il n’est pas nécessaire de spécifier des valeurs pour chacun d’eux. Toutefois, en l’absence d’arguments nommés et facultatifs, une valeur ou une valeur d’espace réservé doit être fournie pour chaque paramètre. Avec les arguments nommés et facultatifs, vous spécifiez des valeurs uniquement pour les paramètres qui sont nécessaires à votre projet.

Pour que vous puissiez effectuer ces procédures, Microsoft Office Word doit être installé sur votre ordinateur.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Pour créer une application console

1. Démarrez Visual Studio.

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

3. Dans le volet **Catégories de modèles**, développez **Visual C#**, puis cliquez sur **Windows**.

4. Regardez en haut du volet **Modèles** pour vérifier que **.NET Framework 4**, ou version ultérieure, apparaît dans la zone **Framework cible**.

5. Dans le volet **Modèles**, cliquez sur **Application console**.

6. Attribuez un nom à votre projet dans le champ **Nom**.

7. Cliquez sur **OK**.

     Le nouveau projet s’affiche dans l’**Explorateur de solutions**.

## <a name="to-add-a-reference"></a>Pour ajouter une référence

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet, puis cliquez sur **Ajouter une référence**. La boîte de dialogue **Ajouter une référence** s’affiche.

2. Dans la page **.NET**, sélectionnez **Microsoft.Office.Interop.Word** dans la liste **Nom du composant**.

3. Cliquez sur **OK**.

## <a name="to-add-necessary-using-directives"></a>Pour ajouter les directives using nécessaires

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *Program.cs*, puis cliquez sur **Afficher le code**.

2. Ajoutez les `using` directives suivantes en haut du fichier de code :

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a>Pour afficher du texte dans un document Word

1. Dans la `Program` classe de *Program.cs*, ajoutez la méthode suivante pour créer une application Word et un document Word. La méthode [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) comprend quatre paramètres facultatifs. Cet exemple utilise leurs valeurs par défaut. Par conséquent, aucun argument n’est nécessaire dans l’instruction appelante.

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. Ajoutez le code suivant à la fin de la méthode pour définir l’emplacement d’affichage du texte dans le document et le texte à afficher :

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a>Pour exécuter l’application

1. Ajoutez l’instruction suivante à main :

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. Appuyez sur <kbd>CTRL</kbd> + <kbd>F5</kbd> pour exécuter le projet. Un document Word contenant le texte spécifié s’affiche.

## <a name="to-change-the-text-to-a-table"></a>Pour convertir le texte en tableau
  
1. Utilisez la méthode `ConvertToTable` pour inclure le texte dans un tableau. La méthode comprend seize paramètres facultatifs. IntelliSense place les paramètres facultatifs entre crochets, comme illustré dans l’exemple suivant.

     ![Liste de paramètres pour la méthode ConvertToTable](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     Les arguments nommés et facultatifs permettent de spécifier des valeurs uniquement pour les paramètres que vous voulez modifier. Ajoutez le code suivant à la fin de la méthode `DisplayInWord` pour créer un tableau simple. L’argument spécifie que les virgules présentes dans le texte de la chaîne comprise dans `range` séparent les cellules du tableau.

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     Dans les versions antérieures de C#, l’appel à `ConvertToTable` requiert un argument de référence pour chaque paramètre, comme indiqué dans le code suivant :
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. Appuyez sur <kbd>CTRL</kbd> + <kbd>F5</kbd> pour exécuter le projet.

## <a name="to-experiment-with-other-parameters"></a>Pour tester d’autres paramètres

1. Pour modifier la table afin qu’elle ait une colonne et trois lignes, remplacez la dernière ligne de `DisplayInWord` par l’instruction suivante, puis tapez <kbd>CTRL</kbd> + <kbd>F5</kbd>.  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. Pour spécifier un format prédéfini pour la table, remplacez la dernière ligne de `DisplayInWord` par l’instruction suivante, puis tapez <kbd>CTRL</kbd> + <kbd>F5</kbd>. Le format peut être n’importe quelle constante [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>).

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a>Exemple

Le code suivant contient l’exemple complet :

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a>Voir aussi

- [Arguments nommés et facultatifs](./named-and-optional-arguments.md)
