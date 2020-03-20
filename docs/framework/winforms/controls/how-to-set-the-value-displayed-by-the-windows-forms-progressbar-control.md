---
title: Définir la valeur affichée par ProgressBar Control
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: d295079a96ca19a4e4c98e113a3f3051c6403182
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141809"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Comment : définir la valeur affichée par le contrôle ProgressBar Windows Forms
> [!IMPORTANT]
> Le contrôle <xref:System.Windows.Forms.ToolStripProgressBar> remplace le contrôle <xref:System.Windows.Forms.ProgressBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ProgressBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Le cadre .NET vous offre plusieurs façons différentes <xref:System.Windows.Forms.ProgressBar> d’afficher une valeur donnée dans le contrôle. L’approche que vous choisissez dépendra de la tâche à accomplir ou du problème que vous résolvez. Le tableau suivant montre les approches que vous pouvez choisir.  
  
|Approche|Description|  
|--------------|-----------------|  
|Définissez directement <xref:System.Windows.Forms.ProgressBar> la valeur du contrôle.|Cette approche est utile pour les tâches où vous connaissez le total de l’élément mesuré qui sera impliqué, comme la lecture des enregistrements à partir d’une source de données. En outre, si vous n’avez besoin de définir la valeur qu’une ou deux fois, c’est un moyen facile de le faire. Enfin, utilisez ce processus si vous avez besoin de diminuer la valeur affichée par la barre de progression.|  
|Augmentez <xref:System.Windows.Forms.ProgressBar> l’affichage d’une valeur fixe.|Cette approche est utile lorsque vous affichez un simple comptage entre le minimum et le maximum, comme le temps écoulé ou le nombre de fichiers qui ont été traités à partir d’un total connu.|  
|Augmentez <xref:System.Windows.Forms.ProgressBar> l’affichage d’une valeur qui varie.|Cette approche est utile lorsque vous avez besoin de modifier la valeur affichée un certain nombre de fois en différents montants. Un exemple serait de montrer la quantité d’espace disque dur consommé lors de l’écriture d’une série de fichiers sur le disque.|  
  
 La façon la plus directe de définir la valeur <xref:System.Windows.Forms.ProgressBar.Value%2A> affichée par une barre de progression est en définissant la propriété. Cela peut être fait soit au moment de la conception ou au moment de l’exécution.  
  
### <a name="to-set-the-progressbar-value-directly"></a>Définir directement la valeur ProgressBar  
  
1. Définissez <xref:System.Windows.Forms.ProgressBar> les <xref:System.Windows.Forms.ProgressBar.Minimum%2A> valeurs <xref:System.Windows.Forms.ProgressBar.Maximum%2A> et le contrôle.  
  
2. En code, définissez <xref:System.Windows.Forms.ProgressBar.Value%2A> la propriété du contrôle à une valeur integer entre les valeurs minimales et maximales que vous avez établies.  
  
    > [!NOTE]
    > Si vous <xref:System.Windows.Forms.ProgressBar.Value%2A> définissez la propriété en <xref:System.Windows.Forms.ProgressBar.Minimum%2A> <xref:System.Windows.Forms.ProgressBar.Maximum%2A> dehors des limites <xref:System.ArgumentException> établies par les propriétés et les propriétés, le contrôle jette une exception.  
  
     L’exemple de code suivant <xref:System.Windows.Forms.ProgressBar> illustre comment définir la valeur directement. Le code lit les enregistrements d’une source de données et met à jour la barre de progression et l’étiquette chaque fois qu’un enregistrement de données est lu. Cet exemple exige que <xref:System.Windows.Forms.Label> votre formulaire <xref:System.Windows.Forms.ProgressBar> dispose d’un contrôle, `CustomerRow` d’un contrôle et d’une table de données avec une ligne appelée avec `FirstName` et `LastName` des champs.  
  
    ```vb  
    Public Sub CreateNewRecords()  
       ' Sets the progress bar's Maximum property to  
       ' the total number of records to be created.  
       ProgressBar1.Maximum = 20  
  
       ' Creates a new record in the dataset.  
       ' NOTE: The code below will not compile, it merely  
       ' illustrates how the progress bar would be used.  
       Dim anyRow As CustomerRow = DatasetName.ExistingTable.NewRow  
       anyRow.FirstName = "Stephen"  
       anyRow.LastName = "James"  
       ExistingTable.Rows.Add(anyRow)  
  
       ' Increases the value displayed by the progress bar.  
       ProgressBar1.Value += 1  
       ' Updates the label to show that a record was read.  
       Label1.Text = "Records Read = " & ProgressBar1.Value.ToString()  
    End Sub  
    ```  
  
    ```csharp  
    public void createNewRecords()  
    {  
       // Sets the progress bar's Maximum property to  
       // the total number of records to be created.  
       progressBar1.Maximum = 20;  
  
       // Creates a new record in the dataset.  
       // NOTE: The code below will not compile, it merely  
       // illustrates how the progress bar would be used.  
       CustomerRow anyRow = DatasetName.ExistingTable.NewRow();  
       anyRow.FirstName = "Stephen";  
       anyRow.LastName = "James";  
       ExistingTable.Rows.Add(anyRow);  
  
       // Increases the value displayed by the progress bar.  
       progressBar1.Value += 1;  
       // Updates the label to show that a record was read.  
       label1.Text = "Records Read = " + progressBar1.Value.ToString();  
    }  
    ```  
  
     Si vous affichez des progrès qui procèdent d’un intervalle fixe, <xref:System.Windows.Forms.ProgressBar> vous pouvez définir la valeur, puis appeler une méthode qui augmente la valeur du contrôle par cet intervalle. Ceci est utile pour les minuteries et autres scénarios où vous ne mesurez pas les progrès en pourcentage de l’ensemble.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>Augmenter la barre de progression d’une valeur fixe  
  
1. Définissez <xref:System.Windows.Forms.ProgressBar> les <xref:System.Windows.Forms.ProgressBar.Minimum%2A> valeurs <xref:System.Windows.Forms.ProgressBar.Maximum%2A> et le contrôle.  
  
2. Définissez la <xref:System.Windows.Forms.ProgressBar.Step%2A> propriété du contrôle à un intégrant représentant le montant pour augmenter la valeur affichée de la barre de progression.  
  
3. Appelez <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> la méthode pour modifier la valeur <xref:System.Windows.Forms.ProgressBar.Step%2A> affichée par le montant fixé dans la propriété.  
  
     L’exemple de code suivant illustre comment une barre de progression peut maintenir un nombre de fichiers dans une opération de copie.  
  
     Dans l’exemple suivant, lorsque chaque fichier est lu dans la mémoire, la barre de progression et l’étiquette sont mises à jour pour refléter le nombre total de fichiers lus. Cet exemple exige que <xref:System.Windows.Forms.Label> votre formulaire <xref:System.Windows.Forms.ProgressBar> ait un contrôle et un contrôle.  
  
    ```vb  
    Public Sub LoadFiles()  
       ' Sets the progress bar's minimum value to a number representing  
       ' no operations complete -- in this case, no files read.  
       ProgressBar1.Minimum = 0  
       ' Sets the progress bar's maximum value to a number representing  
       ' all operations complete -- in this case, all five files read.  
       ProgressBar1.Maximum = 5  
       ' Sets the Step property to amount to increase with each iteration.  
       ' In this case, it will increase by one with every file read.  
       ProgressBar1.Step = 1  
  
       ' Dimensions a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be copied into memory,  
       ' so the loop will execute 5 times.  
       For i = 0 To 4  
          ' Insert code to copy a file  
          ProgressBar1.PerformStep()  
          ' Update the label to show that a file was read.  
          Label1.Text = "# of Files Read = " & ProgressBar1.Value.ToString  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void loadFiles()  
    {  
       // Sets the progress bar's minimum value to a number representing  
       // no operations complete -- in this case, no files read.  
       progressBar1.Minimum = 0;  
       // Sets the progress bar's maximum value to a number representing  
       // all operations complete -- in this case, all five files read.  
       progressBar1.Maximum = 5;  
       // Sets the Step property to amount to increase with each iteration.  
       // In this case, it will increase by one with every file read.  
       progressBar1.Step = 1;  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be copied into memory,  
       // so the loop will execute 5 times.  
       for (int i = 0; i <= 4; i++)  
       {  
          // Inserts code to copy a file  
          progressBar1.PerformStep();  
          // Updates the label to show that a file was read.  
          label1.Text = "# of Files Read = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
     Enfin, vous pouvez augmenter la valeur affichée par une barre de progression de sorte que chaque augmentation est un montant unique. Ceci est utile lorsque vous gardez une trace d’une série d’opérations uniques, telles que l’écriture de fichiers de différentes tailles à un disque dur, ou de mesurer les progrès en pourcentage de l’ensemble.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>Augmenter la barre de progression d’une valeur dynamique  
  
1. Définissez <xref:System.Windows.Forms.ProgressBar> les <xref:System.Windows.Forms.ProgressBar.Minimum%2A> valeurs <xref:System.Windows.Forms.ProgressBar.Maximum%2A> et le contrôle.  
  
2. Appelez <xref:System.Windows.Forms.ProgressBar.Increment%2A> la méthode pour modifier la valeur affichée par un intégriste que vous spécifiez.  
  
     L’exemple de code suivant illustre comment une barre de progression peut calculer la quantité d’espace de disque utilisée lors d’une opération de copie.  
  
     Dans l’exemple suivant, comme chaque fichier est écrit sur le disque dur, la barre de progression et l’étiquette sont mises à jour pour refléter la quantité d’espace disque dur disponible. Cet exemple exige que <xref:System.Windows.Forms.Label> votre formulaire <xref:System.Windows.Forms.ProgressBar> ait un contrôle et un contrôle.  
  
    ```vb  
    Public Sub ReadFiles()  
       ' Sets the progress bar's minimum value to a number
       ' representing the hard disk space before the files are read in.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example and  
       ' will not compile.  
       ProgressBar1.Minimum = AvailableDiskSpace()  
       ' Sets the progress bar's maximum value to a number
       ' representing the total hard disk space.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example
       ' and will not compile.  
       ProgressBar1.Maximum = TotalDiskSpace()  
  
       ' Dimension a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be written to the disk,  
       ' so it will execute the loop 5 times.  
       For i = 1 To 5  
          ' Insert code to read a file into memory and update file size.  
          ' Increases the progress bar's value based on the size of
          ' the file currently being written.  
          ProgressBar1.Increment(FileSize)  
          ' Updates the label to show available drive space.  
          Label1.Text = "Current Disk Space Used = " &_
          ProgressBar1.Value.ToString()  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void readFiles()  
    {  
       // Sets the progress bar's minimum value to a number
       // representing the hard disk space before the files are read in.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example and
       // will not compile.  
       progressBar1.Minimum = AvailableDiskSpace();  
       // Sets the progress bar's maximum value to a number
       // representing the total hard disk space.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example
       // and will not compile.  
       progressBar1.Maximum = TotalDiskSpace();  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be written  
       // to the disk, so it will execute the loop 5 times.  
       for (int i = 1; i<= 5; i++)  
       {  
          // Insert code to read a file into memory and update file size.  
          // Increases the progress bar's value based on the size of
          // the file currently being written.  
          progressBar1.Increment(FileSize);  
          // Updates the label to show available drive space.  
          label1.Text = "Current Disk Space Used = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [Vue d'ensemble du contrôle ProgressBar](progressbar-control-overview-windows-forms.md)
- [ProgressBar, contrôle](progressbar-control-windows-forms.md)
