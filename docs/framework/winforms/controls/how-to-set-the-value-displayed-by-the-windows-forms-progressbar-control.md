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
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a><span data-ttu-id="9ca94-104">Comment : définir la valeur affichée par le contrôle ProgressBar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ca94-104">How to: Set the Value Displayed by the Windows Forms ProgressBar Control</span></span>
> [!IMPORTANT]
> <span data-ttu-id="9ca94-105">Le contrôle <xref:System.Windows.Forms.ToolStripProgressBar> remplace le contrôle <xref:System.Windows.Forms.ProgressBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ProgressBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="9ca94-105">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="9ca94-106">La .NET Framework vous offre plusieurs façons différentes d’afficher une valeur donnée dans le <xref:System.Windows.Forms.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="9ca94-106">The .NET Framework gives you several different ways to display a given value within the <xref:System.Windows.Forms.ProgressBar> control.</span></span> <span data-ttu-id="9ca94-107">L’approche que vous choisissez dépend de la tâche en cours ou du problème que vous résolvez.</span><span class="sxs-lookup"><span data-stu-id="9ca94-107">Which approach you choose will depend on the task at hand or the problem you are solving.</span></span> <span data-ttu-id="9ca94-108">Le tableau suivant présente les approches que vous pouvez choisir.</span><span class="sxs-lookup"><span data-stu-id="9ca94-108">The following table shows the approaches you can choose.</span></span>  
  
|<span data-ttu-id="9ca94-109">Approche</span><span class="sxs-lookup"><span data-stu-id="9ca94-109">Approach</span></span>|<span data-ttu-id="9ca94-110">Description</span><span class="sxs-lookup"><span data-stu-id="9ca94-110">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="9ca94-111">Définissez directement la valeur du <xref:System.Windows.Forms.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="9ca94-111">Set the value of the <xref:System.Windows.Forms.ProgressBar> control directly.</span></span>|<span data-ttu-id="9ca94-112">Cette approche est utile pour les tâches où vous connaissez le total de l’élément mesuré qui sera impliqué, par exemple la lecture d’enregistrements à partir d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="9ca94-112">This approach is useful for tasks where you know the total of the item measured that will be involved, such as reading records from a data source.</span></span> <span data-ttu-id="9ca94-113">En outre, si vous ne devez définir la valeur qu’une ou deux fois, il s’agit d’un moyen simple de le faire.</span><span class="sxs-lookup"><span data-stu-id="9ca94-113">Additionally, if you only need to set the value once or twice, this is an easy way to do it.</span></span> <span data-ttu-id="9ca94-114">Enfin, utilisez ce processus si vous devez réduire la valeur affichée par la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="9ca94-114">Finally, use this process if you need to decrease the value displayed by the progress bar.</span></span>|  
|<span data-ttu-id="9ca94-115">Augmentez l' <xref:System.Windows.Forms.ProgressBar> affichage d’une valeur fixe.</span><span class="sxs-lookup"><span data-stu-id="9ca94-115">Increase the <xref:System.Windows.Forms.ProgressBar> display by a fixed value.</span></span>|<span data-ttu-id="9ca94-116">Cette approche est utile lorsque vous affichez un nombre simple compris entre les valeurs minimale et maximale, par exemple le temps écoulé ou le nombre de fichiers qui ont été traités à partir d’un total connu.</span><span class="sxs-lookup"><span data-stu-id="9ca94-116">This approach is useful when you are displaying a simple count between the minimum and maximum, such as elapsed time or the number of files that have been processed out of a known total.</span></span>|  
|<span data-ttu-id="9ca94-117">Augmentez l' <xref:System.Windows.Forms.ProgressBar> affichage d’une valeur qui varie.</span><span class="sxs-lookup"><span data-stu-id="9ca94-117">Increase the <xref:System.Windows.Forms.ProgressBar> display by a value that varies.</span></span>|<span data-ttu-id="9ca94-118">Cette approche est utile lorsque vous devez modifier la valeur affichée plusieurs fois dans différents volumes.</span><span class="sxs-lookup"><span data-stu-id="9ca94-118">This approach is useful when you need to change the displayed value a number of times in different amounts.</span></span> <span data-ttu-id="9ca94-119">Un exemple est l’indication de la quantité d’espace disque dur consommé lors de l’écriture d’une série de fichiers sur le disque.</span><span class="sxs-lookup"><span data-stu-id="9ca94-119">An example would be showing the amount of hard-disk space being consumed while writing a series of files to the disk.</span></span>|  
  
 <span data-ttu-id="9ca94-120">La façon la plus directe de définir la valeur affichée par une barre de progression consiste à définir la <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="9ca94-120">The most direct way to set the value displayed by a progress bar is by setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="9ca94-121">Vous pouvez effectuer cette opération au moment de la conception ou au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9ca94-121">This can be done either at design time or at run time.</span></span>  
  
### <a name="to-set-the-progressbar-value-directly"></a><span data-ttu-id="9ca94-122">Pour définir la valeur de ProgressBar directement</span><span class="sxs-lookup"><span data-stu-id="9ca94-122">To set the ProgressBar value directly</span></span>  
  
1. <span data-ttu-id="9ca94-123">Définissez les <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Minimum%2A> valeurs et du contrôle <xref:System.Windows.Forms.ProgressBar.Maximum%2A> .</span><span class="sxs-lookup"><span data-stu-id="9ca94-123">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="9ca94-124">Dans le code, affectez à la propriété du contrôle <xref:System.Windows.Forms.ProgressBar.Value%2A> une valeur entière comprise entre les valeurs minimale et maximale que vous avez établies.</span><span class="sxs-lookup"><span data-stu-id="9ca94-124">In code, set the control's <xref:System.Windows.Forms.ProgressBar.Value%2A> property to an integer value between the minimum and maximum values you have established.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9ca94-125">Si vous définissez la <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété en dehors des limites établies par <xref:System.Windows.Forms.ProgressBar.Minimum%2A> les <xref:System.Windows.Forms.ProgressBar.Maximum%2A> Propriétés et, le contrôle lève une <xref:System.ArgumentException> exception.</span><span class="sxs-lookup"><span data-stu-id="9ca94-125">If you set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property outside the boundaries established by the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties, the control throws an <xref:System.ArgumentException> exception.</span></span>  
  
     <span data-ttu-id="9ca94-126">L’exemple de code suivant montre comment définir la <xref:System.Windows.Forms.ProgressBar> valeur directement.</span><span class="sxs-lookup"><span data-stu-id="9ca94-126">The following code example illustrates how to set the <xref:System.Windows.Forms.ProgressBar> value directly.</span></span> <span data-ttu-id="9ca94-127">Le code lit les enregistrements à partir d’une source de données et met à jour la barre de progression et l’étiquette chaque fois qu’un enregistrement de données est lu.</span><span class="sxs-lookup"><span data-stu-id="9ca94-127">The code reads records from a data source and updates the progress bar and label every time a data record is read.</span></span> <span data-ttu-id="9ca94-128">Dans cet exemple, votre formulaire doit avoir un <xref:System.Windows.Forms.Label> contrôle, un <xref:System.Windows.Forms.ProgressBar> contrôle et une table de données avec une ligne appelée `CustomerRow` avec les `FirstName` champs et `LastName` .</span><span class="sxs-lookup"><span data-stu-id="9ca94-128">This example requires that your form has a <xref:System.Windows.Forms.Label> control, a <xref:System.Windows.Forms.ProgressBar> control, and a data table with a row called `CustomerRow` with `FirstName` and `LastName` fields.</span></span>  
  
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
  
     Si vous affichez la progression qui se produit d’un intervalle fixe, vous pouvez définir la valeur, puis appeler une méthode qui augmente la <xref:System.Windows.Forms.ProgressBar> valeur du contrôle de cet intervalle. <span data-ttu-id="9ca94-130">Cela est utile pour les minuteurs et d’autres scénarios où vous ne mesurez pas la progression en tant que pourcentage de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="9ca94-130">This is useful for timers and other scenarios where you are not measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a><span data-ttu-id="9ca94-131">Pour augmenter la barre de progression d’une valeur fixe</span><span class="sxs-lookup"><span data-stu-id="9ca94-131">To increase the progress bar by a fixed value</span></span>  
  
1. <span data-ttu-id="9ca94-132">Définissez les <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Minimum%2A> valeurs et du contrôle <xref:System.Windows.Forms.ProgressBar.Maximum%2A> .</span><span class="sxs-lookup"><span data-stu-id="9ca94-132">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="9ca94-133">Affectez à la <xref:System.Windows.Forms.ProgressBar.Step%2A> propriété du contrôle un entier représentant la quantité d’augmentation de la valeur affichée de la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="9ca94-133">Set the control's <xref:System.Windows.Forms.ProgressBar.Step%2A> property to an integer representing the amount to increase the progress bar's displayed value.</span></span>  
  
3. <span data-ttu-id="9ca94-134">Appelez la <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> méthode pour modifier la valeur affichée par la quantité définie dans la <xref:System.Windows.Forms.ProgressBar.Step%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="9ca94-134">Call the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method to change the value displayed by the amount set in the <xref:System.Windows.Forms.ProgressBar.Step%2A> property.</span></span>  
  
     <span data-ttu-id="9ca94-135">L’exemple de code suivant montre comment une barre de progression peut conserver le nombre de fichiers dans une opération de copie.</span><span class="sxs-lookup"><span data-stu-id="9ca94-135">The following code example illustrates how a progress bar can maintain a count of the files in a copy operation.</span></span>  
  
     <span data-ttu-id="9ca94-136">Dans l’exemple suivant, à mesure que chaque fichier est lu dans la mémoire, la barre de progression et l’étiquette sont mises à jour pour refléter le nombre total de fichiers lus.</span><span class="sxs-lookup"><span data-stu-id="9ca94-136">In the following example, as each file is read into memory, the progress bar and label are updated to reflect the total files read.</span></span> <span data-ttu-id="9ca94-137">Dans cet exemple, votre formulaire doit avoir un <xref:System.Windows.Forms.Label> contrôle et un <xref:System.Windows.Forms.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="9ca94-137">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
     Enfin, vous pouvez augmenter la valeur affichée par une barre de progression afin que chaque augmentation soit une quantité unique. <span data-ttu-id="9ca94-139">Cela est utile lorsque vous effectuez le suivi d’une série d’opérations uniques, telles que l’écriture de fichiers de tailles différentes sur un disque dur, ou la mesure de la progression en tant que pourcentage de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="9ca94-139">This is useful when you are keeping track of a series of unique operations, such as writing files of different sizes to a hard disk, or measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a><span data-ttu-id="9ca94-140">Pour augmenter la barre de progression d’une valeur dynamique</span><span class="sxs-lookup"><span data-stu-id="9ca94-140">To increase the progress bar by a dynamic value</span></span>  
  
1. <span data-ttu-id="9ca94-141">Définissez les <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Minimum%2A> valeurs et du contrôle <xref:System.Windows.Forms.ProgressBar.Maximum%2A> .</span><span class="sxs-lookup"><span data-stu-id="9ca94-141">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="9ca94-142">Appelez la <xref:System.Windows.Forms.ProgressBar.Increment%2A> méthode pour modifier la valeur affichée par un entier que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="9ca94-142">Call the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method to change the value displayed by an integer you specify.</span></span>  
  
     <span data-ttu-id="9ca94-143">L’exemple de code suivant montre comment une barre de progression peut calculer la quantité d’espace disque qui a été utilisée pendant une opération de copie.</span><span class="sxs-lookup"><span data-stu-id="9ca94-143">The following code example illustrates how a progress bar can calculate how much disk space has been used during a copy operation.</span></span>  
  
     <span data-ttu-id="9ca94-144">Dans l’exemple suivant, à mesure que chaque fichier est écrit sur le disque dur, la barre de progression et l’étiquette sont mises à jour pour refléter la quantité d’espace disque disponible.</span><span class="sxs-lookup"><span data-stu-id="9ca94-144">In the following example, as each file is written to the hard disk, the progress bar and label are updated to reflect the amount of hard-disk space available.</span></span> <span data-ttu-id="9ca94-145">Dans cet exemple, votre formulaire doit avoir un <xref:System.Windows.Forms.Label> contrôle et un <xref:System.Windows.Forms.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="9ca94-145">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ca94-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ca94-146">See also</span></span>

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [<span data-ttu-id="9ca94-147">Vue d'ensemble du contrôle ProgressBar</span><span class="sxs-lookup"><span data-stu-id="9ca94-147">ProgressBar Control Overview</span></span>](progressbar-control-overview-windows-forms.md)
- [<span data-ttu-id="9ca94-148">ProgressBar, contrôle</span><span class="sxs-lookup"><span data-stu-id="9ca94-148">ProgressBar Control</span></span>](progressbar-control-windows-forms.md)
