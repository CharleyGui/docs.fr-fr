---
title: 'Procédure : lier des données au contrôle MaskedTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
- data binding [Windows Forms], MaskedTextBox control [Windows Forms]
- MaskedTextBox control [Windows Forms], binding data
ms.assetid: 34b29f07-e8df-48d4-b08b-53fcca524708
ms.openlocfilehash: f10a19433c70eb0a1dacf99925f70d6796727da9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64612407"
---
# <a name="how-to-bind-data-to-the-maskedtextbox-control"></a><span data-ttu-id="c1fdb-102">Procédure : lier des données au contrôle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="c1fdb-102">How to: Bind Data to the MaskedTextBox Control</span></span>
<span data-ttu-id="c1fdb-103">Vous pouvez lier des données à un <xref:System.Windows.Forms.MaskedTextBox> contrôle comme vous pouvez le faire à tout autre contrôle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-103">You can bind data to a <xref:System.Windows.Forms.MaskedTextBox> control just as you can to any other Windows Forms control.</span></span> <span data-ttu-id="c1fdb-104">Toutefois, si le format de vos données dans la base de données ne correspond pas au format attendu par votre définition masque, vous devez remettre en forme les données.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-104">However, if the format of your data in the database does not match the format expected by your mask definition, you will need to reformat the data.</span></span> <span data-ttu-id="c1fdb-105">La procédure suivante montre comment effectuer cette opération à l’aide de la <xref:System.Windows.Forms.Binding.Format> et <xref:System.Windows.Forms.Binding.Parse> événements de la <xref:System.Windows.Forms.Binding> classe pour afficher le numéro de téléphone distinct et champs de base de données d’extension de téléphone en tant qu’un seul champ modifiable.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-105">The following procedure demonstrates how to do this using the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events of the <xref:System.Windows.Forms.Binding> class to display separate phone number and phone extension database fields as a single editable field.</span></span>  
  
 <span data-ttu-id="c1fdb-106">La procédure suivante nécessite que vous avez accès à une base de données SQL Server avec la base de données Northwind installé.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-106">The following procedure requires that you have access to a SQL Server database with the Northwind sample database installed.</span></span>  
  
### <a name="to-bind-data-to-a-maskedtextbox-control"></a><span data-ttu-id="c1fdb-107">Pour lier des données à un contrôle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="c1fdb-107">To bind data to a MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="c1fdb-108">Créez un projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-108">Create a new Windows Forms project.</span></span>  
  
2. <span data-ttu-id="c1fdb-109">Faites glisser deux <xref:System.Windows.Forms.TextBox> contrôles sur votre formulaire ; nommez-les `FirstName` et `LastName`.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-109">Drag two <xref:System.Windows.Forms.TextBox> controls onto your form; name them `FirstName` and `LastName`.</span></span>  
  
3. <span data-ttu-id="c1fdb-110">Faites glisser un <xref:System.Windows.Forms.MaskedTextBox> de contrôle sur votre formulaire ; nommez-le `PhoneMask`.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control onto your form; name it `PhoneMask`.</span></span>  
  
4. <span data-ttu-id="c1fdb-111">Définir le <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriété du `PhoneMask` à `(000) 000-0000 x9999`.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-111">Set the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property of `PhoneMask` to `(000) 000-0000 x9999`.</span></span>  
  
5. <span data-ttu-id="c1fdb-112">Ajoutez que l’espace de noms suivant importe dans le formulaire.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-112">Add the following namespace imports to the form.</span></span>  
  
    ```csharp  
    using System.Data.SqlClient;  
    ```  
  
    ```vb  
    Imports System.Data.SqlClient  
    ```  
  
6. <span data-ttu-id="c1fdb-113">Avec le bouton droit de la forme et choisissez **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-113">Right-click the form and choose **View Code**.</span></span> <span data-ttu-id="c1fdb-114">Placez ce code n’importe où dans votre classe de formulaire.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-114">Place this code anywhere in your form class.</span></span>  
  
    ```csharp  
    Binding currentBinding, phoneBinding;  
    DataSet employeesTable = new DataSet();  
    SqlConnection sc;  
    SqlDataAdapter dataConnect;  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        DoMaskBinding();  
    }  
  
    private void DoMaskBinding()  
    {  
        try  
        {  
            sc = new SqlConnection("Data Source=CLIENTUE;Initial Catalog=NORTHWIND;Integrated Security=SSPI");  
            sc.Open();  
        }  
        catch (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
            return;  
        }  
  
        dataConnect = new SqlDataAdapter("SELECT * FROM Employees", sc);  
        dataConnect.Fill(employeesTable, "Employees");  
  
        // Now bind MaskedTextBox to appropriate field. Note that we must create the Binding objects  
        // before adding them to the control - otherwise, we won't get a Format event on the   
        // initial load.   
        try  
        {  
            currentBinding = new Binding("Text", employeesTable, "Employees.FirstName");  
            firstName.DataBindings.Add(currentBinding);  
  
            currentBinding = new Binding("Text", employeesTable, "Employees.LastName");  
            lastName.DataBindings.Add(currentBinding);  
  
            phoneBinding =new Binding("Text", employeesTable, "Employees.HomePhone");  
            // We must add the event handlers before we bind, or the Format event will not get called  
            // for the first record.  
            phoneBinding.Format += new ConvertEventHandler(phoneBinding_Format);  
            phoneBinding.Parse += new ConvertEventHandler(phoneBinding_Parse);  
            phoneMask.DataBindings.Add(phoneBinding);  
        }  
        catch (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
            return;  
        }  
    }  
    ```  
  
    ```vb  
    Dim WithEvents CurrentBinding, PhoneBinding As Binding  
    Dim EmployeesTable As New DataSet()  
    Dim sc As SqlConnection  
    Dim DataConnect As SqlDataAdapter  
  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        DoMaskedBinding()  
    End Sub  
  
    Private Sub DoMaskedBinding()  
        Try  
            sc = New SqlConnection("Data Source=SERVERNAME;Initial Catalog=NORTHWIND;Integrated Security=SSPI")  
            sc.Open()  
        Catch ex As Exception  
            MessageBox.Show(ex.Message)  
            Exit Sub  
        End Try  
  
        DataConnect = New SqlDataAdapter("SELECT * FROM Employees", sc)  
        DataConnect.Fill(EmployeesTable, "Employees")  
  
        ' Now bind MaskedTextBox to appropriate field. Note that we must create the Binding objects  
        ' before adding them to the control - otherwise, we won't get a Format event on the   
        ' initial load.  
        Try  
            CurrentBinding = New Binding("Text", EmployeesTable, "Employees.FirstName")  
            firstName.DataBindings.Add(CurrentBinding)  
            CurrentBinding = New Binding("Text", EmployeesTable, "Employees.LastName")  
            lastName.DataBindings.Add(CurrentBinding)  
            PhoneBinding = New Binding("Text", EmployeesTable, "Employees.HomePhone")  
            PhoneMask.DataBindings.Add(PhoneBinding)  
        Catch ex As Exception  
            MessageBox.Show(ex.Message)  
            Application.Exit()  
        End Try  
    End Sub  
    ```  
  
7. <span data-ttu-id="c1fdb-115">Ajouter des gestionnaires d’événements pour le <xref:System.Windows.Forms.Binding.Format> et <xref:System.Windows.Forms.Binding.Parse> événements pour combiner et séparer les `PhoneNumber` et `Extension` champs à partir de la limite <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-115">Add event handlers for the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events to combine and separate the `PhoneNumber` and `Extension` fields from the bound <xref:System.Data.DataSet>.</span></span>  
  
    ```csharp  
    private void phoneBinding_Format(Object sender, ConvertEventArgs e)  
    {  
        String ext;  
  
        DataRowView currentRow = (DataRowView)BindingContext[employeesTable, "Employees"].Current;  
        if (currentRow["Extension"] == null)   
        {  
            ext = "";  
        } else   
        {  
            ext = currentRow["Extension"].ToString();  
        }  
  
        e.Value = e.Value.ToString().Trim() + " x" + ext;  
    }  
  
    private void phoneBinding_Parse(Object sender, ConvertEventArgs e)  
    {  
        String phoneNumberAndExt = e.Value.ToString();  
  
        int extIndex = phoneNumberAndExt.IndexOf("x");  
        String ext = phoneNumberAndExt.Substring(extIndex).Trim();  
        String phoneNumber = phoneNumberAndExt.Substring(0, extIndex).Trim();  
  
        //Get the current binding object, and set the new extension manually.   
        DataRowView currentRow = (DataRowView)BindingContext[employeesTable, "Employees"].Current;  
        // Remove the "x" from the extension.  
        currentRow["Extension"] = ext.Substring(1);  
  
        //Return the phone number.  
        e.Value = phoneNumber;  
    }  
    ```  
  
    ```vb  
    Private Sub PhoneBinding_Format(ByVal sender As Object, ByVal e As ConvertEventArgs) Handles PhoneBinding.Format  
        Dim Ext As String  
  
        Dim CurrentRow As DataRowView = CType(Me.BindingContext(EmployeesTable, "Employees").Current, DataRowView)  
        If (CurrentRow("Extension") Is Nothing) Then  
            Ext = ""  
        Else  
            Ext = CurrentRow("Extension").ToString()  
        End If  
  
        e.Value = e.Value.ToString().Trim() & " x" & Ext  
    End Sub  
  
    Private Sub PhoneBinding_Parse(ByVal sender As Object, ByVal e As ConvertEventArgs) Handles PhoneBinding.Parse  
        Dim PhoneNumberAndExt As String = e.Value.ToString()  
  
        Dim ExtIndex As Integer = PhoneNumberAndExt.IndexOf("x")  
        Dim Ext As String = PhoneNumberAndExt.Substring(ExtIndex).Trim()  
        Dim PhoneNumber As String = PhoneNumberAndExt.Substring(0, ExtIndex).Trim()  
  
        ' Get the current binding object, and set the new extension manually.   
        Dim CurrentRow As DataRowView = CType(Me.BindingContext(EmployeesTable, "Employees").Current, DataRowView)  
        ' Remove the "x" from the extension.  
        CurrentRow("Extension") = CObj(Ext.Substring(1))  
  
        ' Return the phone number.  
        e.Value = PhoneNumber  
    End Sub  
    ```  
  
8. <span data-ttu-id="c1fdb-116">Ajoutez deux <xref:System.Windows.Forms.Button> contrôles au formulaire.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-116">Add two <xref:System.Windows.Forms.Button> controls to the form.</span></span> <span data-ttu-id="c1fdb-117">Nommez-les `previousButton` et `nextButton`.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-117">Name them `previousButton` and `nextButton`.</span></span> <span data-ttu-id="c1fdb-118">Double-cliquez sur chaque bouton pour ajouter un <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements et renseignez les gestionnaires d’événements comme indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-118">Double-click each button to add a <xref:System.Windows.Forms.Control.Click> event handler, and fill in the event handlers as shown in the following code example.</span></span>  
  
    ```csharp  
    private void previousButton_Click(object sender, EventArgs e)  
    {  
        BindingContext[employeesTable, "Employees"].Position = BindingContext[employeesTable, "Employees"].Position - 1;  
    }  
  
    private void nextButton_Click(object sender, EventArgs e)  
    {  
        BindingContext[employeesTable, "Employees"].Position = BindingContext[employeesTable, "Employees"].Position + 1;  
    }  
    ```  
  
    ```vb  
    Private Sub PreviousButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles PreviousButton.Click  
        Me.BindingContext(EmployeesTable, "Employees").Position = Me.BindingContext(EmployeesTable, "Employees").Position - 1  
    End Sub  
  
    Private Sub NextButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles NextButton.Click  
        Me.BindingContext(EmployeesTable, "Employees").Position = Me.BindingContext(EmployeesTable, "Employees").Position + 1  
    End Sub  
    ```  
  
9. <span data-ttu-id="c1fdb-119">Exécutez l'exemple.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-119">Run the sample.</span></span> <span data-ttu-id="c1fdb-120">Modifiez les données et utilisez le **précédent** et **suivant** boutons pour voir que les données sont persistantes dans le <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-120">Edit the data, and use the **Previous** and **Next** buttons to see that the data is properly persisted to the <xref:System.Data.DataSet>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1fdb-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="c1fdb-121">Example</span></span>  
 <span data-ttu-id="c1fdb-122">L’exemple de code suivant est l’intégralité du code qui résulte de l’exécution de la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-122">The following code example is the full code listing that results from completing the previous procedure.</span></span>  
  
 [!code-cpp[MaskedTextBoxData#1](~/samples/snippets/cpp/VS_Snippets_Winforms/MaskedTextBoxData/cpp/form1.cpp#1)]
 [!code-csharp[MaskedTextBoxData#1](~/samples/snippets/csharp/VS_Snippets_Winforms/MaskedTextBoxData/CS/form1.cs#1)]
 [!code-vb[MaskedTextBoxData#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/MaskedTextBoxData/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c1fdb-123">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="c1fdb-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="c1fdb-124">Créer un élément visuel C# ou projet Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-124">Create a Visual C# or Visual Basic project.</span></span>  
  
- <span data-ttu-id="c1fdb-125">Ajouter le <xref:System.Windows.Forms.TextBox> et <xref:System.Windows.Forms.MaskedTextBox> contrôles au formulaire, comme décrit dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-125">Add the <xref:System.Windows.Forms.TextBox> and <xref:System.Windows.Forms.MaskedTextBox> controls to the form, as described in the previous procedure.</span></span>  
  
- <span data-ttu-id="c1fdb-126">Ouvrez le fichier de code source pour le formulaire du projet par défaut.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-126">Open the source code file for the project's default form.</span></span>  
  
- <span data-ttu-id="c1fdb-127">Remplacez le code source dans ce fichier par le code répertorié dans la section « Code » précédente.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-127">Replace the source code in this file with the code listed in the previous "Code" section.</span></span>  
  
- <span data-ttu-id="c1fdb-128">Compilez l'application.</span><span class="sxs-lookup"><span data-stu-id="c1fdb-128">Compile the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1fdb-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1fdb-129">See also</span></span>

- [<span data-ttu-id="c1fdb-130">Procédure pas à pas : Utilisation du contrôle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="c1fdb-130">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
