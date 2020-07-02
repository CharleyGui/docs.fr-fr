---
title: Définir la valeur affichée par le contrôle ProgressBar
description: Découvrez comment définir la valeur affichée par le contrôle Windows Forms ProgressBar. Vous pouvez choisir d’utiliser plusieurs approches.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: 75fe1b416636471d797a39134f45a05c972c9d39
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618101"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Comment : définir la valeur affichée par le contrôle ProgressBar Windows Forms
> [!IMPORTANT]
> Le contrôle <xref:System.Windows.Forms.ToolStripProgressBar> remplace le contrôle <xref:System.Windows.Forms.ProgressBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ProgressBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 La .NET Framework vous offre plusieurs façons différentes d’afficher une valeur donnée dans le <xref:System.Windows.Forms.ProgressBar> contrôle. L’approche que vous choisissez dépend de la tâche en cours ou du problème que vous résolvez. Le tableau suivant présente les approches que vous pouvez choisir.  
  
|Approche|Description|  
|--------------|-----------------|  
|Définissez directement la valeur du <xref:System.Windows.Forms.ProgressBar> contrôle.|Cette approche est utile pour les tâches où vous connaissez le total de l’élément mesuré qui sera impliqué, par exemple la lecture d’enregistrements à partir d’une source de données. En outre, si vous ne devez définir la valeur qu’une ou deux fois, il s’agit d’un moyen simple de le faire. Enfin, utilisez ce processus si vous devez réduire la valeur affichée par la barre de progression.|  
|Augmentez l' <xref:System.Windows.Forms.ProgressBar> affichage d’une valeur fixe.|Cette approche est utile lorsque vous affichez un nombre simple compris entre les valeurs minimale et maximale, par exemple le temps écoulé ou le nombre de fichiers qui ont été traités à partir d’un total connu.|  
|Augmentez l' <xref:System.Windows.Forms.ProgressBar> affichage d’une valeur qui varie.|Cette approche est utile lorsque vous devez modifier la valeur affichée plusieurs fois dans différents volumes. Un exemple est l’indication de la quantité d’espace disque dur consommé lors de l’écriture d’une série de fichiers sur le disque.|  
  
 La façon la plus directe de définir la valeur affichée par une barre de progression consiste à définir la <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété. Vous pouvez effectuer cette opération au moment de la conception ou au moment de l’exécution.  
  
### <a name="to-set-the-progressbar-value-directly"></a>Pour définir la valeur de ProgressBar directement  
  
1. Définissez les <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Minimum%2A> valeurs et du contrôle <xref:System.Windows.Forms.ProgressBar.Maximum%2A> .  
  
2. Dans le code, affectez à la propriété du contrôle <xref:System.Windows.Forms.ProgressBar.Value%2A> une valeur entière comprise entre les valeurs minimale et maximale que vous avez établies.  
  
    > [!NOTE]
    > Si vous définissez la <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété en dehors des limites établies par <xref:System.Windows.Forms.ProgressBar.Minimum%2A> les <xref:System.Windows.Forms.ProgressBar.Maximum%2A> Propriétés et, le contrôle lève une <xref:System.ArgumentException> exception.  
  
     L’exemple de code suivant montre comment définir la <xref:System.Windows.Forms.ProgressBar> valeur directement. Le code lit les enregistrements à partir d’une source de données et met à jour la barre de progression et l’étiquette chaque fois qu’un enregistrement de données est lu. Dans cet exemple, votre formulaire doit avoir un <xref:System.Windows.Forms.Label> contrôle, un <xref:System.Windows.Forms.ProgressBar> contrôle et une table de données avec une ligne appelée `CustomerRow` avec les `FirstName` champs et `LastName` .  
  
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
  
     Si vous affichez la progression qui se produit d’un intervalle fixe, vous pouvez définir la valeur, puis appeler une méthode qui augmente la <xref:System.Windows.Forms.ProgressBar> valeur du contrôle de cet intervalle. Cela est utile pour les minuteurs et d’autres scénarios où vous ne mesurez pas la progression en tant que pourcentage de l’ensemble.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>Pour augmenter la barre de progression d’une valeur fixe  
  
1. Définissez les <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Minimum%2A> valeurs et du contrôle <xref:System.Windows.Forms.ProgressBar.Maximum%2A> .  
  
2. Affectez à la <xref:System.Windows.Forms.ProgressBar.Step%2A> propriété du contrôle un entier représentant la quantité d’augmentation de la valeur affichée de la barre de progression.  
  
3. Appelez la <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> méthode pour modifier la valeur affichée par la quantité définie dans la <xref:System.Windows.Forms.ProgressBar.Step%2A> propriété.  
  
     L’exemple de code suivant montre comment une barre de progression peut conserver le nombre de fichiers dans une opération de copie.  
  
     Dans l’exemple suivant, à mesure que chaque fichier est lu dans la mémoire, la barre de progression et l’étiquette sont mises à jour pour refléter le nombre total de fichiers lus. Dans cet exemple, votre formulaire doit avoir un <xref:System.Windows.Forms.Label> contrôle et un <xref:System.Windows.Forms.ProgressBar> contrôle.  
  
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
  
     Enfin, vous pouvez augmenter la valeur affichée par une barre de progression afin que chaque augmentation soit une quantité unique. Cela est utile lorsque vous effectuez le suivi d’une série d’opérations uniques, telles que l’écriture de fichiers de tailles différentes sur un disque dur, ou la mesure de la progression en tant que pourcentage de l’ensemble.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>Pour augmenter la barre de progression d’une valeur dynamique  
  
1. Définissez les <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Minimum%2A> valeurs et du contrôle <xref:System.Windows.Forms.ProgressBar.Maximum%2A> .  
  
2. Appelez la <xref:System.Windows.Forms.ProgressBar.Increment%2A> méthode pour modifier la valeur affichée par un entier que vous spécifiez.  
  
     L’exemple de code suivant montre comment une barre de progression peut calculer la quantité d’espace disque qui a été utilisée pendant une opération de copie.  
  
     Dans l’exemple suivant, à mesure que chaque fichier est écrit sur le disque dur, la barre de progression et l’étiquette sont mises à jour pour refléter la quantité d’espace disque disponible. Dans cet exemple, votre formulaire doit avoir un <xref:System.Windows.Forms.Label> contrôle et un <xref:System.Windows.Forms.ProgressBar> contrôle.  
  
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
