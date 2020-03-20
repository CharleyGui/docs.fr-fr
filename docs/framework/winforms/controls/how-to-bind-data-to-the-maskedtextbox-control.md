---
title: 'Comment : lier des données au contrôle MaskedTextBox'
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
ms.openlocfilehash: 0cbb239e24b254c37c453486590185e934adf482
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142171"
---
# <a name="how-to-bind-data-to-the-maskedtextbox-control"></a>Comment : lier des données au contrôle MaskedTextBox
Vous pouvez lier <xref:System.Windows.Forms.MaskedTextBox> les données à un contrôle tout comme vous le pouvez à n’importe quel autre contrôle des formulaires Windows. Toutefois, si le format de vos données dans la base de données ne correspond pas au format attendu par votre définition de masque, vous devrez reformer les données. La procédure suivante montre comment le <xref:System.Windows.Forms.Binding.Format> <xref:System.Windows.Forms.Binding.Parse> faire en <xref:System.Windows.Forms.Binding> utilisant les et les événements de la classe pour afficher des numéros de téléphone séparés et des champs de base de données d’extension de téléphone comme un champ modifiable unique.  
  
 La procédure suivante exige que vous ayez accès à une base de données SQL Server avec la base de données d’échantillons Northwind installée.  
  
### <a name="to-bind-data-to-a-maskedtextbox-control"></a>Pour lier les données à un contrôle MaskedTextBox  
  
1. Créez un projet Windows Forms.  
  
2. Faites <xref:System.Windows.Forms.TextBox> glisser deux commandes sur votre formulaire; les `FirstName` nommer `LastName`et .  
  
3. Faites <xref:System.Windows.Forms.MaskedTextBox> glisser un contrôle sur votre formulaire; nom `PhoneMask`.  
  
4. Définir <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> la `PhoneMask` propriété `(000) 000-0000 x9999`de .  
  
5. Ajoutez les importations suivantes d’espace de nom au formulaire.  
  
    ```csharp  
    using System.Data.SqlClient;  
    ```  
  
    ```vb  
    Imports System.Data.SqlClient  
    ```  
  
6. Cliquez à droite sur le formulaire et choisissez **le code de vue**. Placez ce code n’importe où dans votre classe de formulaire.  
  
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
  
7. Ajouter des gestionnaires <xref:System.Windows.Forms.Binding.Format> d’événements pour les événements et <xref:System.Windows.Forms.Binding.Parse> les événements pour combiner et séparer les `PhoneNumber` champs et `Extension` les champs de la limite <xref:System.Data.DataSet>.  
  
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
  
8. Ajoutez <xref:System.Windows.Forms.Button> deux commandes au formulaire. Nommez-les `previousButton` et `nextButton`. Double-cliquez sur chaque <xref:System.Windows.Forms.Control.Click> bouton pour ajouter un gestionnaire d’événement, et remplir les gestionnaires d’événements comme indiqué dans l’exemple de code suivant.  
  
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
  
9. Exécutez l’exemple. Modifier les données, et utiliser les boutons **Précédent** et **Suivant** pour voir <xref:System.Data.DataSet>que les données sont correctement persistées à la .  
  
## <a name="example"></a> Exemple  
 L’exemple de code suivant est la liste complète du code qui résulte de l’achèvement de la procédure précédente.  
  
 [!code-cpp[MaskedTextBoxData#1](~/samples/snippets/cpp/VS_Snippets_Winforms/MaskedTextBoxData/cpp/form1.cpp#1)]
 [!code-csharp[MaskedTextBoxData#1](~/samples/snippets/csharp/VS_Snippets_Winforms/MaskedTextBoxData/CS/form1.cs#1)]
 [!code-vb[MaskedTextBoxData#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/MaskedTextBoxData/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Créez un projet Visual CM ou Visual Basic.  
  
- Ajoutez <xref:System.Windows.Forms.TextBox> le <xref:System.Windows.Forms.MaskedTextBox> et les contrôles à la forme, comme décrit dans la procédure précédente.  
  
- Ouvrez le fichier de code source pour le formulaire par défaut du projet.  
  
- Remplacez le code source dans ce fichier avec le code indiqué dans la section précédente "Code".  
  
- Compilez l’application.  
  
## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : utilisation du contrôle MaskedTextBox](walkthrough-working-with-the-maskedtextbox-control.md)
