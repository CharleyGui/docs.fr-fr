---
title: Enregistrer des fichiers avec le contrôle RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
ms.openlocfilehash: a87b93a53347aeba54f944b0f4c455aa272ea243
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744815"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>Comment : enregistrer des fichiers avec le contrôle RichTextBox Windows Forms

Le contrôle Windows Forms <xref:System.Windows.Forms.RichTextBox> peut écrire les informations qu’il affiche dans l’un des formats suivants :

- Texte brut

- Texte brut Unicode

- Format RTF (Rich-Text Format)

- RTF avec espaces à la place des objets OLE

- Texte brut avec une représentation textuelle des objets OLE

Pour enregistrer un fichier, appelez la méthode <xref:System.Windows.Forms.RichTextBox.SaveFile%2A>. Vous pouvez également utiliser la méthode **SaveFile** pour enregistrer des données dans un flux. Pour plus d'informations, consultez <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.

### <a name="to-save-the-contents-of-the-control-to-a-file"></a>Pour enregistrer le contenu du contrôle dans un fichier

1. Déterminez le chemin d’accès du fichier à enregistrer.

    Pour effectuer cette opération dans une application réelle, vous devez généralement utiliser le composant <xref:System.Windows.Forms.SaveFileDialog>. Pour obtenir une vue d’ensemble, consultez [vue d’ensemble du composant SaveFileDialog](savefiledialog-component-overview-windows-forms.md).

2. Appelez la méthode <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> du contrôle <xref:System.Windows.Forms.RichTextBox>, en spécifiant le fichier à enregistrer et éventuellement un type de fichier. Si vous appelez la méthode avec un nom de fichier comme seul argument, le fichier est enregistré au format RTF. Pour spécifier un autre type de fichier, appelez la méthode en spécifiant une valeur pour l’énumération <xref:System.Windows.Forms.RichTextBoxStreamType> comme deuxième argument.

    Dans l’exemple ci-dessous, le chemin d’accès défini pour l’emplacement du fichier de texte enrichi est le dossier **Mes documents** . Cet emplacement est utilisé, car vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce dossier. Le choix de cet emplacement permet également aux utilisateurs disposant d’un niveau d’accès minimal au système d’exécuter l’application en toute sécurité. L’exemple ci-dessous suppose un formulaire avec un contrôle de <xref:System.Windows.Forms.RichTextBox> déjà ajouté.

    ```vb
    Public Sub SaveFile()
       ' You should replace the bold file name in the
       ' sample below with a file name of your own choosing.
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _
       (System.Environment.SpecialFolder.Personal) _
       & "\Testdoc.rtf", _
          RichTextBoxStreamType.RichNoOleObjs)
    End Sub
    ```

    ```csharp
    public void SaveFile()
    {
       // You should replace the bold file name in the
       // sample below with a file name of your own choosing.
       // Note the escape character used (@) when specifying the path.
       richTextBox1.SaveFile(System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.Personal)
       + @"\Testdoc.rtf",
          RichTextBoxStreamType.RichNoOleObjs);
    }
    ```

    ```cpp
    public:
       void SaveFile()
       {
          // You should replace the bold file name in the
          // sample below with a file name of your own choosing.
          richTextBox1->SaveFile(String::Concat
             (System::Environment::GetFolderPath
             (System::Environment::SpecialFolder::Personal),
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);
       }
    ```

    > [!IMPORTANT]
    > Cet exemple crée un fichier s’il n’existe pas déjà. Si une application doit créer un fichier, cette application doit créer un accès pour le dossier. Les autorisations sont définies à l’aide des listes de contrôle d’accès. Si le fichier existe déjà, l’application a uniquement besoin d’un accès en écriture, ce qui est un privilège inférieur. Dans la mesure du possible, il est plus sûr de créer le fichier au cours du déploiement et d’accorder uniquement l’accès en lecture à un seul fichier, plutôt que de créer un accès pour un dossier. En outre, il est plus sûr d’écrire les données dans des dossiers utilisateur que dans le dossier racine ou le dossier Program Files.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, contrôle](richtextbox-control-windows-forms.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
