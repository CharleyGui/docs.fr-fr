---
title: manipulation de fichiers à l’aide de méthodes .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], walkthroughs
- text files [Visual Basic], writing to
- reading text files [Visual Basic]
- text, writing to files
- files [Visual Basic], searching
- StreamReader class, walkthroughs
- files [Visual Basic], accessing
- I/O [Visual Basic], writing text to files
- writing to files [Visual Basic], walkthroughs
- StreamWriter class, walkthroughs
- text files [Visual Basic], reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
ms.openlocfilehash: 02cdbcc59e8817ff4ec06c2f78f835cad77b10f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333785"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>Procédure pas à pas : manipulation de fichiers à l'aide de méthodes du .NET Framework (Visual Basic)

Cette procédure pas à pas illustre comment ouvrir et lire un fichier à l’aide de la classe <xref:System.IO.StreamReader>, vérifier si une tentative d’accès à un fichier est en cours, rechercher une chaîne dans un fichier lu avec une instance de la classe <xref:System.IO.StreamReader> et écrire dans un fichier à l’aide de la classe <xref:System.IO.StreamWriter>.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a>Création de l’application

Démarrez Visual Studio et commencez le projet par la création d’un formulaire qui permet à l’utilisateur d’écrire dans le fichier désigné.

### <a name="to-create-the-project"></a>Pour créer le projet

1. Dans le menu **Fichier**, sélectionnez **Nouveau projet**.

2. Dans le volet **Nouveau projet**, cliquez sur **Application Windows**.

3. Dans la zone **nom** , `MyDiary` tapez, puis cliquez sur **OK**.

     Visual Studio ajoute le projet à **Explorateur de solutions**et le **Concepteur Windows Forms** s’ouvre.

4. Ajoutez au formulaire les contrôles répertoriés dans le tableau ci-après et définissez les valeurs de propriété correspondantes.

|**Dessin**|**Propriétés**|**Valeur**|
|---|---|---|
|<xref:System.Windows.Forms.Button>|**Nom**<br /><br /> **Text**|`Submit`<br /><br /> **Envoyer l’entrée**|
|<xref:System.Windows.Forms.Button>|**Nom**<br /><br /> **Text**|`Clear`<br /><br /> **Effacer l’entrée**|
|<xref:System.Windows.Forms.TextBox>|**Nom**<br /><br /> **Text**<br /><br /> **Multiline**|`Entry`<br /><br /> **Saisissez quelque chose.**<br /><br /> `False`|

## <a name="writing-to-the-file"></a>Écriture dans le fichier

Pour permettre l’écriture dans un fichier via l’application, utilisez la classe <xref:System.IO.StreamWriter>. La classe <xref:System.IO.StreamWriter> est conçue pour la sortie de caractères dans un encodage particulier, tandis que la classe <xref:System.IO.Stream> est conçue pour l’entrée et la sortie d’octets. Utilisez <xref:System.IO.StreamWriter> pour écrire des lignes d’informations dans un fichier texte standard. Pour plus d’informations sur la classe <xref:System.IO.StreamWriter>, consultez <xref:System.IO.StreamWriter>.

### <a name="to-add-writing-functionality"></a>Pour ajouter une fonctionnalité d’écriture

1. Dans le menu **Affichage**, choisissez **Code** pour ouvrir l’éditeur de code.

2. Étant donné que l’application référence l’espace de noms <xref:System.IO>, ajoutez les instructions ci-après tout au début de votre code, avant la déclaration de classe du formulaire, `Public Class Form1`.

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     Avant d’écrire dans le fichier, vous devez créer une instance d’une classe <xref:System.IO.StreamWriter>.

3. Dans le menu **Affichage**, choisissez **Concepteur** pour retourner au **Concepteur Windows Forms**. Double-cliquez sur le bouton `Submit` pour créer un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour ce bouton, puis ajoutez le code suivant.

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> L’environnement de développement intégré (IDE, Integrated Development Environment) Visual Studio revient à l’éditeur de code et positionne le point d’insertion dans le gestionnaire d’événements, à l’emplacement où vous devez ajouter le code.

1. Pour écrire dans le fichier, utilisez la méthode <xref:System.IO.StreamWriter.Write%2A> de la classe <xref:System.IO.StreamWriter>. Ajoutez le code ci-dessous immédiatement après `Dim fw As StreamWriter`. La levée d’une exception en cas de fichier introuvable ne doit pas vous inquiéter, car le fichier est créé s’il n’existe pas.

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. Vérifiez que l’utilisateur ne peut soumettre aucune entrée vide en ajoutant le code suivant immédiatement après `Dim ReadString As String`.

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. Comme il s’agit d’un agenda, l’utilisateur veut assigner une date à chaque entrée. Insérez le code suivant après `fw = New StreamWriter("C:\MyDiary.txt", True)` pour affecter la date actuelle à la variable `Today`.

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. Pour finir, attachez le code pour effacer <xref:System.Windows.Forms.TextBox>. Ajoutez le code suivant à l’événement <xref:System.Windows.Forms.Control.Click> du bouton `Clear`.

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a>Ajout de fonctionnalités d’affichage à l’agenda

Dans cette section, vous ajoutez une fonctionnalité qui affiche la dernière entrée dans le contrôle `DisplayEntry`<xref:System.Windows.Forms.TextBox>. Vous pouvez également ajouter un <xref:System.Windows.Forms.ComboBox> qui affiche différentes entrées et à partir duquel un utilisateur peut sélectionner une entrée à afficher dans le `DisplayEntry`<xref:System.Windows.Forms.TextBox>. Une instance de la classe <xref:System.IO.StreamReader> lit à partir de `MyDiary.txt`. Comme la classe <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader> est destiné à être utilisé avec des fichiers texte.

Pour cette section de la procédure pas à pas, ajoutez au formulaire les contrôles répertoriés dans le tableau ci-après et définissez les valeurs de propriété correspondantes.

|Control|Propriétés|Valeurs|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|**Nom**<br /><br /> **Parent**<br /><br /> **Taille**<br /><br /> **Multiline**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|**Nom**<br /><br /> **Text**|`Display`<br /><br /> **Affichage**|
|<xref:System.Windows.Forms.Button>|**Nom**<br /><br /> **Text**|`GetEntries`<br /><br /> **Obtenir des entrées**|
|<xref:System.Windows.Forms.ComboBox>|**Nom**<br /><br /> **Text**<br /><br /> **Activé**|`PickEntries`<br /><br /> **Sélectionner une entrée**<br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a>Pour remplir la zone de liste déroulante

1. Le contrôle `PickEntries`<xref:System.Windows.Forms.ComboBox> permet d’afficher les dates auxquelles un utilisateur soumet une entrée. Ainsi, celui-ci peut sélectionner une entrée associée à une date déterminée. Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> au bouton `GetEntries` et ajoutez le code suivant.

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. Pour tester votre code, appuyez sur F5 pour compiler l’application, puis cliquez sur **Obtenir des entrées**. Cliquez sur la flèche déroulante dans le <xref:System.Windows.Forms.ComboBox> pour afficher les dates d’entrée.

### <a name="to-choose-and-display-individual-entries"></a>Pour sélectionner et afficher des entrées individuelles

1. Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour le bouton `Display` et ajoutez le code suivant.

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. Pour tester votre code, appuyez sur F5 pour compiler l’application, puis soumettez une entrée. Cliquez sur **Obtenir des entrées**, sélectionnez une entrée dans le <xref:System.Windows.Forms.ComboBox>, puis cliquez sur **Afficher**. Le contenu de l’entrée sélectionnée s’affiche dans le `DisplayEntry`<xref:System.Windows.Forms.TextBox>.

## <a name="enabling-users-to-delete-or-modify-entries"></a>Autorisation aux utilisateurs de supprimer ou de modifier des entrées

Enfin, vous pouvez inclure des fonctionnalités supplémentaires qui permettent aux utilisateurs de supprimer ou de modifier une entrée à l’aide des boutons `DeleteEntry` et `EditEntry`. Ces deux boutons restent désactivés si aucune entrée n’est affichée.

Ajoutez au formulaire les contrôles répertoriés dans le tableau ci-après et définissez les valeurs de propriété correspondantes.

|Control|Propriétés|Valeurs|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|**Nom**<br /><br /> **Text**<br /><br /> **Activé**|`DeleteEntry`<br /><br /> **Supprimer l’entrée**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Nom**<br /><br /> **Text**<br /><br /> **Activé**|`EditEntry`<br /><br /> **Modifier l’entrée**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Nom**<br /><br /> **Text**<br /><br /> **Activé**|`SubmitEdit`<br /><br /> **Envoyer la modification**<br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a>Pour activer la suppression et la modification d’entrées

1. Ajoutez le code suivant à l’événement <xref:System.Windows.Forms.Control.Click> du bouton `Display`, après `DisplayEntry.Text = ReadString`.

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour le bouton `DeleteEntry` et ajoutez le code suivant.

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. Quand un utilisateur affiche une entrée, le bouton `EditEntry` devient disponible. Ajoutez le code suivant à l’événement <xref:System.Windows.Forms.Control.Click> du bouton `Display` après `DisplayEntry.Text = ReadString`.

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour le bouton `EditEntry` et ajoutez le code suivant.

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour le bouton `SubmitEdit` et ajoutez le code suivant.

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

Pour tester votre code, appuyez sur F5 pour compiler l’application. Cliquez sur **Obtenir des entrées**, sélectionnez une entrée, puis cliquez sur **Afficher**. L’entrée s’affiche dans le `DisplayEntry`<xref:System.Windows.Forms.TextBox>. Cliquez sur **Modifier l’entrée**. L’entrée s’affiche dans le `Entry`<xref:System.Windows.Forms.TextBox>. Modifiez l’entrée dans le `Entry` <xref:System.Windows.Forms.TextBox> , puis cliquez sur **Envoyer la modification**. Ouvrez le fichier `MyDiary.txt` pour confirmer vos corrections. À présent, sélectionnez une entrée et cliquez sur **Supprimer l’entrée**. Quand le <xref:System.Windows.Forms.MessageBox> demande confirmation, cliquez sur **OK**. Fermez l’application et ouvrez `MyDiary.txt` pour confirmer la suppression.

## <a name="see-also"></a>Voir aussi

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [Procédures pas à pas](../../../../visual-basic/walkthroughs.md)
