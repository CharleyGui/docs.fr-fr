---
title: 'Procédure pas à pas : Programmation Office (C# et Visual Basic)'
description: Découvrez les fonctionnalités offertes par Visual Studio en C# et Visual Basic qui améliorent la programmation Microsoft Office.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
ms.openlocfilehash: eff414411c47ec83177ae6a09de4a96f47af6313
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558587"
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>Procédure pas à pas : Programmation Office (C# et Visual Basic)

Visual Studio offre des fonctionnalités dans C# et Visual Basic qui améliorent la programmation Microsoft Office. Les fonctionnalités utiles de C# incluent des arguments nommés et facultatifs ainsi que des valeurs de retour de type `dynamic`. Dans la programmation COM, vous pouvez omettre le mot clé `ref` et accéder aux propriétés indexées. Les fonctionnalités de Visual Basic incluent les propriétés implémentées automatiquement, les instructions dans les expressions lambda et les initialiseurs de collection.

Les deux langages autorisent l'incorporation d'informations de type, qui permet de déployer des assemblys interagissant avec les composants COM sans déployer les assemblys PIA (Primary Interop Assemblies) sur l'ordinateur de l'utilisateur. Pour plus d’informations, consultez [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../../../standard/assembly/embed-types-visual-studio.md).

Cette procédure pas à pas illustre ces fonctionnalités dans le contexte de la programmation Office, mais beaucoup d’entre elles sont aussi utiles en programmation générale. Dans la procédure pas à pas, vous allez utiliser une application de complément Excel pour créer un classeur Excel. Vous créerez ensuite un document Word contenant un lien vers le classeur. Enfin, vous apprendrez à activer et désactiver la dépendance d’assembly PIA.

## <a name="prerequisites"></a>Prérequis

Pour effectuer cette procédure pas à pas, Microsoft Office Excel et Microsoft Office Word doivent être installés sur votre ordinateur.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-set-up-an-excel-add-in-application"></a>Pour configurer une application de type complément Excel

1. Démarrez Visual Studio.

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

3. Dans le volet **Modèles installés**, développez **Visual Basic** ou **Visual C#**, **Office**, puis cliquez sur l’année de version du produit Office.

4. Dans le volet **modèles** , cliquez **sur \<version> complément Excel**.

5. Regardez en haut du volet **Modèles** pour vérifier que **.NET Framework 4**, ou version ultérieure, apparaît dans la zone **Framework cible**.

6. Tapez un nom pour votre projet dans la zone **Nom**, si vous le souhaitez.

7. Cliquez sur **OK**.

8. Le nouveau projet s’affiche dans l’**Explorateur de solutions**.

### <a name="to-add-references"></a>Pour ajouter des références

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet, puis cliquez sur **Ajouter une référence**. La boîte de dialogue **Ajouter une référence** s’affiche.

2. Sous l’onglet **Assemblys**, sélectionnez **Microsoft.Office.Interop.Excel**, version `<version>.0.0.0` (pour plus d’informations sur les numéros de version des produits Office, consultez [Versions Microsoft](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)),dans la liste **Nom du composant**, puis maintenez la touche CTRL enfoncée et sélectionnez **Microsoft.Office.Interop.Word**, `version <version>.0.0.0`. Si les assemblys n’apparaissent pas, vous devez vérifier qu’ils sont installés et s’affichent (consultez [Guide pratique pour installer les assemblys PIA (Primary Interop Assembly) d’Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)).

3. Cliquez sur **OK**.

### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Pour ajouter les instructions Imports ou les directives using nécessaires

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier **ThisAddIn.vb** ou **ThisAddIn.cs**, puis cliquez sur **Afficher le code**.

2. Ajoutez les instructions `Imports` suivantes (Visual Basic) ou les directives `using` (C#) en haut du fichier de code, si elles ne sont pas déjà présentes.

     [!code-csharp[csOfficeWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#1)]

     [!code-vb[csOfficeWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#1)]

### <a name="to-create-a-list-of-bank-accounts"></a>Pour créer une liste de comptes bancaires

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet, cliquez sur **Ajouter**, puis sur **Classe**. Nommez la classe Account.vb si vous utilisez Visual Basic ou Account.cs si vous utilisez C#. Cliquez sur **Add**.

2. Remplacez la définition de la classe `Account` par le code suivant : Les définitions de classe utilisent les *propriétés implémentées automatiquement*. Pour plus d’informations, consultez [Propriétés implémentées automatiquement](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).

     [!code-csharp[csOfficeWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/account.cs#2)]

     [!code-vb[csOfficeWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/account.vb#2)]

3. Pour créer une `bankAccounts` liste qui contient deux comptes, ajoutez le code suivant à la `ThisAddIn_Startup` méthode dans *ThisAddIn. vb* ou *ThisAddIn.cs*. Les déclarations de liste utilisent les *initialiseurs de collection*. Pour plus d’informations, consultez [Initialiseurs de collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

     [!code-csharp[csOfficeWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#3)]

     [!code-vb[csOfficeWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#3)]

### <a name="to-export-data-to-excel"></a>Pour exporter des données vers Excel

1. Dans le même fichier, ajoutez la méthode suivante à la classe `ThisAddIn`. La méthode configure un classeur Excel, vers lequel elle exporte les données.

     [!code-csharp[csOfficeWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#4)]

     [!code-vb[csOfficeWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#4)]

     Deux nouvelles fonctionnalités C# sont utilisées dans cette méthode. Ces deux fonctionnalités existent déjà en Visual Basic.

    - La méthode [Add](<xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>) possède un *paramètre facultatif* pour spécifier un modèle particulier. Les paramètres optionnels, introduits dans C# 4, vous permettent d'omettre l'argument du paramètre, si vous souhaitez utiliser la valeur par défaut de ce dernier. Dans la mesure où aucun argument n'est envoyé dans l'exemple précédent, `Add` utilise le modèle par défaut et crée un classeur. L'instruction équivalente dans les versions antérieures de C# nécessite un argument d'espace réservé : `excelApp.Workbooks.Add(Type.Missing)`.

         Pour plus d’informations, consultez [arguments nommés et facultatifs](../classes-and-structs/named-and-optional-arguments.md).

    - Les propriétés `Range` et `Offset` de l’objet [Range](<xref:Microsoft.Office.Interop.Excel.Range>) utilisent la fonctionnalité des *propriétés indexées*. Cette fonctionnalité vous permet de consommer ces propriétés à partir des types COM à l’aide de la syntaxe C# standard suivante. Les propriétés indexées vous permettent également d'utiliser la propriété `Value` de l'objet `Range`, ce qui rend superflue l'utilisation de la propriété `Value2`. La propriété `Value` est indexée, mais l'index est optionnel. Les arguments facultatifs et les propriétés indexées fonctionnent ensemble dans l’exemple suivant.

         [!code-csharp[csOfficeWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#5)]

         Dans les versions antérieures du langage, la syntaxe spéciale suivante est requise.

         [!code-csharp[csOfficeWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#6)]

         Vous ne pouvez pas créer vos propres propriétés indexées. La fonctionnalité prend uniquement en charge la consommation de propriétés indexées existantes.

         Pour plus d’informations, consultez Guide pratique [pour utiliser des propriétés indexées dans la programmation de COM Interop](./how-to-use-indexed-properties-in-com-interop-rogramming.md).

2. À la fin de `DisplayInExcel`, ajoutez le code suivant pour ajuster les largeurs de colonne au contenu.

     [!code-csharp[csOfficeWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#7)]

     [!code-vb[csOfficeWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#7)]

     Ces ajouts illustrent une autre fonctionnalité de C# : le traitement des valeurs `Object` retournées par les hôtes COM tels qu’Office comme si leur type était [dynamic](../../language-reference/builtin-types/reference-types.md). Cela se produit automatiquement lorsque l’option **incorporer les types d’interopérabilité** est définie sur sa valeur par défaut, `True` ou, de manière équivalente, lorsque l’assembly est référencé par l’option du compilateur [-Link](../../language-reference/compiler-options/link-compiler-option.md) . Le type `dynamic` permet la liaison tardive, déjà disponible dans Visual Basic et évite le cast explicite requis dans C# 3.0 et versions antérieures du langage.

     Par exemple, `excelApp.Columns[1]` retourne un `Object` et `AutoFit` est une méthode [Range](<xref:Microsoft.Office.Interop.Excel.Range>) Excel. Sans `dynamic`, vous devez effectuer un cast de l'objet retourné par `excelApp.Columns[1]` sous la forme d'une instance de `Range` avant d'appeler la méthode `AutoFit`.

     [!code-csharp[csOfficeWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#8)]

     Pour plus d'informations sur l'incorporation des types d'interopérabilité, consultez les procédures « Pour rechercher la référence d'assembly PIA » et « Pour restaurer la dépendance d'assembly PIA » plus loin dans cette rubrique. Pour plus d’informations sur `dynamic`, consultez [dynamic](../../language-reference/builtin-types/reference-types.md) ou [Utilisation du type dynamic](../types/using-type-dynamic.md).

### <a name="to-invoke-displayinexcel"></a>Pour appeler DisplayInExcel

1. Ajoutez le code suivant à la fin de la méthode `ThisAddIn_StartUp`. L'appel à `DisplayInExcel` contient deux arguments. Le premier argument est le nom de la liste des comptes à traiter. Le deuxième argument est une expression lambda multiligne qui définit comment les données doivent être traitées. Les valeurs `ID` et `balance` de chaque compte s'affichent dans des cellules adjacentes et la ligne s'affiche en rouge si le solde est inférieur à zéro. Pour plus d’informations, consultez [expressions lambda](../../language-reference/operators/lambda-expressions.md).

     [!code-csharp[csOfficeWalkthrough#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#9)]

     [!code-vb[csOfficeWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#9)]

2. Pour exécuter le programme, appuyez sur F5. Une feuille de calcul Excel s'affiche avec les données des comptes.

### <a name="to-add-a-word-document"></a>Pour ajouter un document Word

1. Ajoutez le code suivant à la fin de la méthode `ThisAddIn_StartUp` pour créer un document Word qui contient un lien vers le classeur Excel.

     [!code-csharp[csOfficeWalkthrough#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#10)]

     [!code-vb[csOfficeWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#10)]

     Ce code illustre plusieurs fonctionnalités nouvelles en C# : la possibilité d'omettre le mot clé `ref` dans la programmation COM, les arguments nommés et les arguments facultatifs. Ces fonctionnalités existent déjà en Visual Basic. La méthode [PasteSpecial](<xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>) comporte sept paramètres, tous définis en tant que paramètres de référence facultatifs. Les arguments nommés et les arguments facultatifs vous permettent de désigner les paramètres auxquels vous souhaitez accéder par leur nom et d’envoyer des arguments à ces seuls paramètres. Dans cet exemple, les arguments sont envoyés pour indiquer qu’un lien vers le classeur dans le Presse-papiers doit être créé (paramètre `Link`) et que ce lien doit être affiché dans le document Word sous forme d’une icône (paramètre `DisplayAsIcon`). Visual C# vous permet également d’omettre le mot clé `ref` pour ces arguments.

### <a name="to-run-the-application"></a>Pour exécuter l’application

1. Appuyez sur F5 pour exécuter l'application. Excel démarre et affiche un tableau qui contient les informations des deux comptes de `bankAccounts`. Puis, un document Word apparaît qui contient un lien vers le tableau Excel.

### <a name="to-clean-up-the-completed-project"></a>Pour nettoyer le projet terminé

1. Dans Visual Studio, cliquez sur **Nettoyer la solution** dans le menu **Générer**. Sinon, le complément s'exécutera chaque fois que vous ouvrirez Excel sur votre ordinateur.

### <a name="to-find-the-pia-reference"></a>Pour rechercher la référence d'assembly PIA

1. Exécutez de nouveau l’application, mais ne cliquez pas sur **Nettoyer la solution**.

2. Sélectionnez le bouton **Démarrer**. Recherchez **Microsoft Visual Studio \<version> ** et ouvrez une invite de commandes développeur.

3. Tapez `ildasm` dans la fenêtre Invite de commandes développeur pour Visual Studio, puis appuyez sur Entrée. La fenêtre IL DASM s'affiche.

4. Dans le menu **Fichier** de la fenêtre IL DASM, sélectionnez **Fichier** > **Ouvrir**. Double-cliquez sur **Visual \<version> Studio **, puis double-cliquez sur **projets**. Ouvrez le dossier de votre projet et, dans le dossier bin/Debug, recherchez *nom de votre projet*.dll. Double-cliquez sur *nom de votre projet*.dll. Une nouvelle fenêtre affiche les attributs de votre projet, en plus des références à d'autres modules et assemblys. Remarquez que les espaces de noms `Microsoft.Office.Interop.Excel` et `Microsoft.Office.Interop.Word` sont inclus dans l'assembly. Par défaut, dans Visual Studio, le compilateur importe les types dont vous avez besoin à partir d’un assembly PIA référencé dans votre assembly.

     Pour plus d’informations, consultez [Guide pratique pour afficher le contenu d’un assembly](../../../standard/assembly/view-contents.md).

5. Double-cliquez sur l’icône **MANIFESTE**. Une fenêtre affiche la liste des assemblys contenant les éléments référencés par le projet. `Microsoft.Office.Interop.Excel` et `Microsoft.Office.Interop.Word` ne sont pas inclus dans la liste. Étant donné que les types dont votre projet a besoin ont été importés dans votre assembly, les références à un assembly PIA ne sont pas requis. Le déploiement s'en trouve facilité. Les assemblys PIA ne doivent pas être présents sur l'ordinateur de l'utilisateur ; comme une application ne nécessite pas le déploiement d'une version spécifique d'un assembly PIA, les applications peuvent être conçues pour fonctionner avec plusieurs versions d'Office, sous réserve que les API nécessaires existent dans toutes les versions.

     Le déploiement d'assemblys PIA n'étant plus nécessaire, vous pouvez créer une application dans les scénarios avancés qui fonctionne avec plusieurs versions d'Office, y compris les versions antérieures. Cependant, cela ne fonctionne que si votre code n'utilise pas d'API qui ne sont pas disponibles dans la version d'Office que vous utilisez. Comme il n'est pas toujours évident de savoir si une API particulière était disponible dans une version antérieure, l'utilisation de versions antérieures d'Office n'est pas recommandée.

    > [!NOTE]
    > Jusqu'à Office 2003, Office ne publiait pas les assemblys PIA. Par conséquent, le seul moyen de générer un assembly d'interopérabilité pour Office 2002 ou versions antérieures consiste à importer la référence COM.

6. Fermez la fenêtre de manifeste et la fenêtre d'assembly.

### <a name="to-restore-the-pia-dependency"></a>Pour restaurer la dépendance d'assembly PIA

1. Dans l’**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**. Développez le dossier **Références** et sélectionnez **Microsoft.Office.Interop.Excel**. Appuyez sur F4 pour afficher la fenêtre **Propriétés**.

2. Dans la fenêtre **Propriétés**, remplacez la valeur **True** de la propriété **Incorporer les types d’interopérabilité** par **False**.

3. Répétez les étapes 1 et 2 de cette procédure pour `Microsoft.Office.Interop.Word`.

4. Dans C#, commentez les deux appels à `Autofit` à la fin de la méthode `DisplayInExcel`.

5. Appuyez sur F5 pour vérifier que le projet continue de s'exécuter correctement.

6. Répétez les étapes 1 à 3 de la procédure précédente pour ouvrir la fenêtre d'assembly. Notez que `Microsoft.Office.Interop.Word` et `Microsoft.Office.Interop.Excel` ne sont plus dans la liste des assemblys incorporés.

7. Double-cliquez sur l’icône **MANIFESTE** et faites défiler la liste des assemblys référencés. `Microsoft.Office.Interop.Word` et `Microsoft.Office.Interop.Excel` figurent tous deux dans la liste. Comme l’application référence les assemblys PIA Excel et Word, et que la propriété **Incorporer les types d’interopérabilité** a la valeur **False**, les deux assemblys doivent exister sur l’ordinateur de l’utilisateur final.

8. Dans Visual Studio, cliquez sur **Nettoyer la solution** dans le menu **Générer** pour nettoyer le projet achevé.

## <a name="see-also"></a>Voir aussi

- [Propriétés implémentées automatiquement (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Propriétés implémentées automatiquement (C#)](../classes-and-structs/auto-implemented-properties.md)
- [Initialiseurs de collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Initialiseurs d’objets et de collections](../classes-and-structs/object-and-collection-initializers.md)
- [Paramètres facultatifs](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Passage des arguments par position et par nom](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)
- [Arguments nommés et facultatifs](../classes-and-structs/named-and-optional-arguments.md)
- [Liaison précoce et tardive](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Utilisation du type dynamic](../types/using-type-dynamic.md)
- [Expressions lambda (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Expressions lambda (C#)](../../language-reference/operators/lambda-expressions.md)
- [Comment utiliser des propriétés indexées dans la programmation COM Interop](./how-to-use-indexed-properties-in-com-interop-rogramming.md)
- [Procédure pas à pas : incorporation d’informations de type provenant d’assemblys Microsoft Office dans Visual Studio](/previous-versions/visualstudio/visual-studio-2013/ee317478(v=vs.120))
- [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../../../standard/assembly/embed-types-visual-studio.md)
- [Procédure pas à pas : création de votre premier complément VSTO pour Excel](/visualstudio/vsto/walkthrough-creating-your-first-vsto-add-in-for-excel)
- [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
- [Interopérabilité](./index.md)
