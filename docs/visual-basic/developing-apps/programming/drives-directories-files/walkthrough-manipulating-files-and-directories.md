---
title: Manipulation de fichiers et de répertoires
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], reading text
- reading files [Visual Basic], text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files [Visual Basic], walkthroughs
- Visual Basic code, file access
- files [Visual Basic], writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files [Visual Basic], walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
ms.openlocfilehash: 83dc6ce0d29c1c368c36b51fc84ecad34d72e01f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333805"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>Procédure pas à pas : manipulation de fichiers et de répertoires en Visual Basic

Cette procédure pas à pas présente les notions de base d’E/S de fichier dans Visual Basic. Elle décrit comment créer une petite application qui répertorie et examine des fichiers texte dans un répertoire. Pour chaque fichier texte sélectionné, l’application fournit des attributs de fichier et la première ligne de contenu. Elle comprend une option pour écrire des informations dans un fichier journal.  
  
 Cette procédure pas à pas utilise des membres de `My.Computer.FileSystem Object`, qui sont disponibles dans Visual Basic. Consultez la rubrique <xref:Microsoft.VisualBasic.FileIO.FileSystem> (éventuellement en anglais) pour plus d'informations. À la fin de la procédure pas à pas, un exemple équivalent est fourni, qui utilise des classes de l’espace de noms <xref:System.IO>.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Pour créer le projet  
  
1. Dans le menu **Fichier**, cliquez sur **Nouveau projet**.  
  
     La boîte de dialogue **Nouveau projet** apparaît.  
  
2. Dans le volet **Modèles installés**, développez **Visual Basic**, puis cliquez sur **Windows**. Dans le volet **Modèles** du milieu, cliquez sur **Application Windows Forms**.  
  
3. Dans la zone **Nom**, tapez `FileExplorer` pour définir le nom de projet, puis cliquez sur **OK**.  
  
     Visual Studio ajoute le projet à l’**Explorateur de solutions** et le concepteur Windows Forms s’ouvre.  
  
4. Ajoutez au formulaire les contrôles répertoriés dans le tableau ci-après et définissez les valeurs de propriété correspondantes.  
  
    |Control|Propriété|Valeur|  
    |-------------|--------------|-----------|  
    |**Zone de liste**|**Nom**|`filesListBox`|  
    |**Bouton**|**Nom**<br /><br /> **Text**|`browseButton`<br /><br /> **Parcourir**|  
    |**Bouton**|**Nom**<br /><br /> **Text**|`examineButton`<br /><br /> **Examiner**|  
    |**Activé**|**Nom**<br /><br /> **Text**|`saveCheckBox`<br /><br /> **Enregistrer les résultats**|  
    |**FolderBrowserDialog**|**Nom**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Pour sélectionner un dossier et répertorier les fichiers dans un dossier  
  
1. Créez un gestionnaire d’événements `Click` pour `browseButton` en double-cliquant sur le contrôle sur le formulaire. L'éditeur de code s'ouvre.  
  
2. Ajoutez le code ci-après au gestionnaire d'événements `Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     L’appel de `FolderBrowserDialog1.ShowDialog` ouvre la boîte de dialogue **Rechercher un dossier**. Une fois que l’utilisateur a cliqué sur **OK**, la propriété <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> est envoyée en tant qu’argument à la méthode `ListFiles`, qui est ajoutée à l’étape suivante.  
  
3. Ajoutez la méthode `ListFiles` suivante.  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     Ce code efface d’abord le contrôle **ListBox**.  
  
     La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> récupère ensuite une collection de chaînes, une pour chaque fichier dans le répertoire. La méthode `GetFiles` accepte un argument de modèle de recherche pour récupérer les fichiers qui correspondent à un modèle particulier. Dans cet exemple, seuls les fichiers ayant l’extension .txt sont retournés.  
  
     Les chaînes qui sont retournées par la méthode `GetFiles` sont ensuite ajoutées à **ListBox**.  
  
4. Exécutez l'application. Cliquez sur le bouton **Parcourir** . Dans la boîte de dialogue **Rechercher un dossier**, accédez à un dossier qui contient des fichiers .txt, puis sélectionnez le dossier et cliquez sur **OK**.  
  
     `ListBox` contient une liste des fichiers.txt du dossier sélectionné.  
  
5. Arrêtez l’exécution de l’application.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Pour obtenir les attributs d’un fichier et le contenu d’un fichier texte  
  
1. Créez un gestionnaire d’événements `Click` pour `examineButton` en double-cliquant sur le contrôle sur le formulaire.  
  
2. Ajoutez le code ci-après au gestionnaire d'événements `Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     Le code vérifie qu’un élément est sélectionné dans le contrôle `ListBox`. Il obtient ensuite l’entrée du chemin du fichier à partir de `ListBox`. La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> est utilisée pour vérifier si le fichier existe toujours.  
  
     Le chemin du fichier est envoyé en tant qu’argument à la méthode `GetTextForOutput`, qui est ajoutée à l’étape suivante. Cette méthode retourne une chaîne qui contient des informations sur le fichier. Les informations sur le fichier s’affichent dans un élément **MessageBox**.  
  
3. Ajoutez la méthode `GetTextForOutput` suivante.  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     Le code utilise la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> pour obtenir des paramètres de fichier. Les paramètres de fichier sont ajoutés à un <xref:System.Text.StringBuilder>.  
  
     La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> lit le contenu du fichier dans un <xref:System.IO.StreamReader>. La première ligne du contenu est obtenue à partir du `StreamReader` et est ajoutée au `StringBuilder`.  
  
4. Exécutez l'application. Cliquez sur **Parcourir** et recherchez un dossier qui contient des fichiers .txt. Cliquez sur **OK**.  
  
     Sélectionnez un fichier dans le contrôle `ListBox`, puis cliquez sur **Examiner**. `MessageBox` affiche les informations sur le fichier.  
  
5. Arrêtez l’exécution de l’application.  
  
### <a name="to-add-a-log-entry"></a>Pour ajouter une entrée de journal  
  
1. Ajoutez le code suivant à la fin du gestionnaire d’événements `examineButton_Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     Le code définit le chemin du fichier journal de sorte que ce dernier soit placé dans le même répertoire que celui du fichier sélectionné. Le texte de l’entrée de journal prend comme valeur la date et l’heure actuelles, suivies des informations sur le fichier.  
  
     La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>, avec l’argument `append` défini sur `True`, est utilisée pour créer l’entrée de journal.  
  
2. Exécutez l'application. Accédez à un fichier texte, sélectionnez-le dans le contrôle `ListBox`, cochez la case **Enregistrer les résultats**, puis cliquez sur **Examiner**. Vérifiez que l’entrée de journal est écrite dans le fichier `log.txt`.  
  
3. Arrêtez l’exécution de l’application.  
  
### <a name="to-use-the-current-directory"></a>Pour utiliser le répertoire actif  
  
1. Créez un gestionnaire d’événements pour `Form1_Load` en double-cliquant sur le formulaire.  
  
2. Ajoutez le code suivant au gestionnaire d’événements.  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     Ce code définit le répertoire actif comme le répertoire par défaut de l’Explorateur de dossiers.  
  
3. Exécutez l'application. Quand vous cliquez pour la première fois sur **Parcourir**, la boîte de dialogue **Rechercher un dossier** affiche le répertoire actif.  
  
4. Arrêtez l’exécution de l’application.  
  
### <a name="to-selectively-enable-controls"></a>Pour activer des contrôles de manière sélective  
  
1. Ajoutez la méthode `SetEnabled` suivante.  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     La méthode `SetEnabled` active ou désactive les contrôles, selon qu’un élément est sélectionné ou non dans le contrôle `ListBox`.  
  
2. Créez un gestionnaire d’événements `SelectedIndexChanged` pour `filesListBox` en double-cliquant sur le contrôle `ListBox` sur le formulaire.  
  
3. Ajoutez un appel à `SetEnabled` dans le nouveau gestionnaire d’événements `filesListBox_SelectedIndexChanged`.  
  
4. Ajoutez un appel à `SetEnabled` à la fin du gestionnaire d’événements `browseButton_Click`.  
  
5. Ajoutez un appel à `SetEnabled` à la fin du gestionnaire d’événements `Form1_Load`.  
  
6. Exécutez l'application. La case **Enregistrer les résultats** et le bouton **Examiner** sont désactivés si aucun élément n’est sélectionné dans le contrôle `ListBox`.  
  
## <a name="full-example-using-mycomputerfilesystem"></a>Exemple complet de l’utilisation de My.Computer.FileSystem  

 L’exemple complet se trouve ci-dessous.  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a>Exemple complet de l’utilisation de System.IO  

 L’exemple équivalent suivant utilise des classes de l’espace de noms <xref:System.IO> au lieu d’utiliser des objets `My.Computer.FileSystem`.  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [Procédure pas à pas : manipulation de fichiers à l'aide de méthodes du .NET Framework](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
