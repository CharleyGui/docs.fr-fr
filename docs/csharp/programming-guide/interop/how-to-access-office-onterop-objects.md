---
title: Comment accéder aux objets interop Office - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: b5d2da011ec6318c8b07f1eb4d383a4d56488239
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700833"
---
# <a name="how-to-access-office-interop-objects-c-programming-guide"></a>Comment accéder aux objets interop Office (Guide de programmation C)

Les fonctionnalités de CMD simplifient l’accès aux objets Office API. Les nouvelles fonctionnalités incluent les arguments nommés et les arguments facultatifs, un nouveau type appelé `dynamic` et la possibilité de passer des arguments aux paramètres de référence dans les méthodes COM comme s'il s'agissait de paramètres de valeur.

Dans cette rubrique, vous allez utiliser les nouvelles fonctionnalités pour écrire le code qui crée et affiche une feuille de calcul Microsoft Office Excel. Vous écrirez ensuite le code pour ajouter un document Office Word qui contient une icône liée à la feuille de calcul Excel.

Pour effectuer cette procédure pas à pas, Microsoft Office Excel 2007 et Microsoft Office Word 2007, ou versions ultérieures, doivent être installés sur votre ordinateur.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Pour créer une application console

1. Démarrez Visual Studio.

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**. La boîte de dialogue **Nouveau projet** s'affiche.

3. Dans le volet **Modèles installés**, développez **Visual C#**, puis cliquez sur **Windows**.

4. Vérifiez en haut de la boîte de dialogue **Nouveau projet** que **.NET Framework 4** (ou version ultérieure) est sélectionné comme version cible de .NET Framework.

5. Dans le volet **Modèles**, cliquez sur **Application console**.

6. Attribuez un nom à votre projet dans le champ **Nom**.

7. Cliquez sur **OK**.

     Le nouveau projet s’affiche dans l’**Explorateur de solutions**.

## <a name="to-add-references"></a>Pour ajouter des références

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet, puis cliquez sur **Ajouter une référence**. La boîte de dialogue **Ajouter une référence** s’affiche.

2. Dans la page **Assemblys**, sélectionnez **Microsoft.Office.Interop.Word** dans la liste **Nom du composant**, puis maintenez la touche CTRL enfoncée et sélectionnez **Microsoft.Office.Interop.Excel**.  Si vous ne voyez pas les assemblages, vous devrez peut-être vous assurer qu’elles sont installées et affichées. Voir [comment: Installer office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).

3. Cliquez sur **OK**.

## <a name="to-add-necessary-using-directives"></a>Pour ajouter les directives using nécessaires

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *Program.cs*, puis cliquez sur **Afficher le code**.

2. Ajoutez les `using` directives suivantes au haut du fichier de code :

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a>Pour créer une liste de comptes bancaires

1. Copiez-collez la définition de classe suivante dans **Program.cs**, sous la classe `Program`.

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. Ajoutez le code suivant à la méthode `Main` pour créer une liste `bankAccounts` contenant deux comptes.

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a>Pour déclarer une méthode qui exporte les informations de compte vers Excel

1. Ajoutez la méthode suivante à la classe `Program` pour définir une feuille de calcul Excel.

     La méthode <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> a un paramètre facultatif pour spécifier un modèle particulier. Les paramètres optionnels, introduits dans C# 4, vous permettent d'omettre l'argument du paramètre, si vous souhaitez utiliser la valeur par défaut de ce dernier. Dans la mesure où aucun argument n'est envoyé dans le code suivant, `Add` utilise le modèle par défaut et crée un classeur. L'instruction équivalente dans les versions antérieures de C# nécessite un argument d'espace réservé : `ExcelApp.Workbooks.Add(Type.Missing)`.

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. À la fin de `DisplayInExcel`, ajoutez le code suivant. Le code insère les valeurs dans les deux premières colonnes de la première ligne de la feuille de calcul.

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. À la fin de `DisplayInExcel`, ajoutez le code suivant. La boucle `foreach` place les informations de la liste des comptes dans les deux premières colonnes des lignes successives de la feuille de calcul.

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. À la fin de `DisplayInExcel`, ajoutez le code suivant pour ajuster les largeurs de colonne au contenu.

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     Les versions antérieures de C# nécessitent un cast explicite pour ces opérations, car `ExcelApp.Columns[1]` retourne `Object`, et `AutoFit` est une méthode <xref:Microsoft.Office.Interop.Excel.Range> d’Excel. Les lignes suivantes illustrent le cast.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     Les versions C 4, et plus `Object` `dynamic` tard, convertissent automatiquement les versions retournées si l’assemblage est référencé par l’option [compilateur -lien](../../language-reference/compiler-options/link-compiler-option.md) ou, de façon équivalente, si la propriété Excel **Embed Interop Types** est définie pour être vraie. La valeur par défaut de cette propriété est true.

## <a name="to-run-the-project"></a>Pour exécuter le projet

1. À la fin de `Main`, ajoutez la ligne suivante.

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. Appuyez sur CTRL+F5.

     Une feuille de calcul Excel s'affiche avec les données des deux comptes.

## <a name="to-add-a-word-document"></a>Pour ajouter un document Word

1. Pour illustrer d'autres façons grâce auxquelles C# 4, ainsi que les versions ultérieures, améliore la programmation Office, le code suivant ouvre une application Word et crée une icône liée à la feuille de calcul Excel.

     Collez la méthode `CreateIconInWordDoc`, fournie ultérieurement dans cette étape, dans la classe `Program`. `CreateIconInWordDoc` utilise des arguments nommés et facultatifs pour réduire la complexité des appels de méthode à <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> et <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>. Ces appels incorporent deux autres nouvelles fonctionnalités introduites dans C# 4, qui simplifient les appels aux méthodes COM comportant des paramètres de référence. Premièrement, vous pouvez envoyer des arguments aux paramètres de référence comme s'il s'agissait de paramètres de valeur. Autrement dit, vous pouvez envoyer les valeurs directement, sans créer une variable pour chaque paramètre de référence. Le compilateur génère des variables temporaires pour stocker les valeurs d'argument et les ignore lors du retour de l'appel. Ensuite, vous pouvez omettre le mot clé `ref` dans la liste d'arguments.

     La méthode `Add` comporte quatre paramètres de référence, tous facultatifs. Dans C# 4.0 ou versions ultérieures, vous pouvez omettre les arguments de tout ou partie des paramètres si vous voulez utiliser leurs valeurs par défaut. Dans C# 3.0 et versions antérieures, un argument doit être fourni pour chaque paramètre et l'argument doit être une variable, car les paramètres sont des paramètres de référence.

     La méthode `PasteSpecial` insère le contenu du Presse-papiers. La méthode comporte sept paramètres de référence, tous facultatifs. Le code suivant spécifie des arguments pour deux d'entre eux : `Link` pour créer un lien vers la source du contenu du Presse-papiers et `DisplayAsIcon` pour afficher le lien sous forme d'icône. Dans C# 4.0 et versions ultérieures, vous pouvez utiliser des arguments nommés pour ces deux-là et omettre les autres. Bien qu'il s'agisse de paramètres de référence, vous n'avez pas à utiliser le mot clé `ref` ou à créer des variables à envoyer tant qu'arguments. Vous pouvez envoyer les valeurs directement. Dans C# 3.0 et versions antérieures, vous devez fournir un argument de variable pour chaque paramètre de référence.

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     Dans C# 3.0 ou dans les versions antérieures du langage, le code plus complexe suivant est requis.

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. À la fin de `Main`, ajoutez l'instruction suivante.

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. À la fin de `DisplayInExcel`, ajoutez l'instruction suivante. La méthode `Copy` ajoute la feuille de calcul au Presse-papiers.

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. Appuyez sur CTRL+F5.

     Un document Word s'affiche avec une icône. Double-cliquez sur l'icône pour afficher la feuille de calcul au premier plan.

## <a name="to-set-the-embed-interop-types-property"></a>Pour définir la propriété Incorporer les types interop

1. D'autres améliorations sont possibles lorsque vous appelez un type COM qui ne nécessite pas un assembly PIA (Primary Interop Assembly) au moment de l'exécution. La suppression de la dépendance vis-à-vis des assemblys PIA aboutit à l'indépendance des versions et facilite le déploiement. Pour plus d’informations sur les avantages de la programmation sans assemblys PIA, consultez [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../../../standard/assembly/embed-types-visual-studio.md).

     En outre, la programmation est plus facile, car les types qui sont requis et retournés par les méthodes COM peuvent être représentés par l'utilisation du type `dynamic` à la place d'`Object`. Les variables de type `dynamic` ne sont pas évaluées avant l'exécution, ce qui élimine la nécessité d'un cast explicite. Pour plus d’informations, consultez [Utilisation du type dynamic](../types/using-type-dynamic.md).

     Dans C# 4, l'incorporation des informations de type au lieu de l'utilisation des assemblys PIA est le comportement par défaut. En raison de ce comportement par défaut, plusieurs des exemples précédents sont simplifiés, car un cast explicite n'est pas requis. Par exemple, la déclaration de `worksheet` dans `DisplayInExcel` est écrite sous la forme `Excel._Worksheet workSheet = excelApp.ActiveSheet` plutôt que sous la forme `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`. Les appels à `AutoFit` dans la même méthode nécessiteraient également un cast explicite sans la valeur par défaut, parce que `ExcelApp.Columns[1]` retourne un `Object` et que `AutoFit` est une méthode Excel. Le code suivant illustre le cast.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. Pour modifier la valeur par défaut et utiliser les assemblys PIA au lieu d’incorporer les informations de type, développez le nœud **Références** dans **l’Explorateur de solutions**, puis sélectionnez **Microsoft.Office.Interop.Excel** ou **Microsoft.Office.Interop.Word**.

3. Si la fenêtre **Propriétés** n’apparaît pas, appuyez sur **F4**.

4. Recherchez **Incorporer les types interop** dans la liste des propriétés et attribuez-lui la valeur **False**. De façon équivalente, vous pouvez compiler en utilisant l’option [compilateur de référence](../../language-reference/compiler-options/reference-compiler-option.md) au lieu de [-lien](../../language-reference/compiler-options/link-compiler-option.md) à une invite de commande.

## <a name="to-add-additional-formatting-to-the-table"></a>Pour ajouter une mise en forme supplémentaire au tableau

1. Remplacez les deux appels à `AutoFit` de `DisplayInExcel` avec l'instruction suivante.

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     La méthode <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> a sept paramètres de valeur, tous facultatifs. Les arguments nommés et les arguments facultatifs vous permettent de fournir des arguments pour tout ou partie des paramètres, voire pour aucun. Dans l'instruction précédente, un argument est fourni pour un seul des paramètres, `Format`. Comme `Format` est le premier paramètre dans la liste des paramètres, vous n'avez pas à fournir le nom du paramètre. Cependant, l'instruction peut être plus facile à comprendre si le nom du paramètre est inclus, comme illustré dans le code suivant.

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. Appuyez sur CTRL+F5 pour afficher le résultat. D’autres formats sont listés dans l’énumération <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat>.

3. Comparez l'instruction de l'étape 1 au code suivant, qui indique les arguments requis dans C# 3.0 et versions antérieures.

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a> Exemple

L'exemple de code suivant illustre l'exemple complet.

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [Dynamique](../../language-reference/builtin-types/reference-types.md)
- [Utilisation du type dynamic](../types/using-type-dynamic.md)
- [Arguments nommés et facultatifs](../classes-and-structs/named-and-optional-arguments.md)
- [Comment utiliser les arguments nommés et facultatifs dans la programmation du Bureau](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
