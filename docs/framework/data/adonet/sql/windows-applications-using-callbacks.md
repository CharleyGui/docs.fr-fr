---
title: Applications Windows utilisant des rappels
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ae2ea457-0764-4b06-8977-713c77e85bd2
ms.openlocfilehash: de925afd071a5c92dfa3f6a5e35e62a8ba734cd8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147617"
---
# <a name="windows-applications-using-callbacks"></a><span data-ttu-id="b8b46-102">Applications Windows utilisant des rappels</span><span class="sxs-lookup"><span data-stu-id="b8b46-102">Windows Applications Using Callbacks</span></span>

<span data-ttu-id="b8b46-103">Dans la plupart des scénarios de traitement asynchrone, vous souhaitez démarrer une opération de base de données et continuer à exécuter d’autres processus sans attendre la fin de l’opération de base de données.</span><span class="sxs-lookup"><span data-stu-id="b8b46-103">In most asynchronous processing scenarios, you want to start a database operation and continue running other processes without waiting for the database operation to complete.</span></span> <span data-ttu-id="b8b46-104">Toutefois, de nombreux scénarios requièrent une action une fois l’opération de base de données terminée.</span><span class="sxs-lookup"><span data-stu-id="b8b46-104">However, many scenarios require doing something once the database operation has ended.</span></span> <span data-ttu-id="b8b46-105">Dans une application Windows, par exemple, vous pouvez souhaiter la délégation de l’opération de longue durée à un thread d’arrière-plan permet au thread d’interface utilisateur de rester réactif.</span><span class="sxs-lookup"><span data-stu-id="b8b46-105">In a Windows application, for example, you may want to delegate the long-running operation to a background thread while allowing the user interface thread to remain responsive.</span></span> <span data-ttu-id="b8b46-106">Toutefois, lorsque l’opération de base de données est terminée, vous souhaitez utiliser les résultats pour remplir le formulaire.</span><span class="sxs-lookup"><span data-stu-id="b8b46-106">However, when the database operation is complete, you want to use the results to populate the form.</span></span> <span data-ttu-id="b8b46-107">Ce type de scénario est le mieux implémenté avec un rappel.</span><span class="sxs-lookup"><span data-stu-id="b8b46-107">This type of scenario is best implemented with a callback.</span></span>  
  
 <span data-ttu-id="b8b46-108">Vous définissez un rappel en spécifiant un délégué <xref:System.AsyncCallback> dans la méthode <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> ou <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8b46-108">You define a callback by specifying an <xref:System.AsyncCallback> delegate in the <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>, or <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> method.</span></span> <span data-ttu-id="b8b46-109">Le délégué est appelé une fois l’opération terminée.</span><span class="sxs-lookup"><span data-stu-id="b8b46-109">The delegate is called when the operation is complete.</span></span> <span data-ttu-id="b8b46-110">Vous pouvez transmettre au délégué une référence à la <xref:System.Data.SqlClient.SqlCommand> elle-même, ce qui facilite l’accès à l’objet <xref:System.Data.SqlClient.SqlCommand> et l’appel de la méthode `End` appropriée sans avoir à utiliser une variable globale.</span><span class="sxs-lookup"><span data-stu-id="b8b46-110">You can pass the delegate a reference to the <xref:System.Data.SqlClient.SqlCommand> itself, making it easy to access the <xref:System.Data.SqlClient.SqlCommand> object and call the appropriate `End` method without having to use a global variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8b46-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="b8b46-111">Example</span></span>  

 <span data-ttu-id="b8b46-112">L’application Windows suivante illustre l’utilisation de la méthode <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, en exécutant une instruction Transact-SQL qui comprend un délai de quelques secondes (en émulant une commande longue).</span><span class="sxs-lookup"><span data-stu-id="b8b46-112">The following Windows application demonstrates the use of the <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A> method, executing a Transact-SQL statement that includes a delay of a few seconds (emulating a long-running command).</span></span>  
  
 <span data-ttu-id="b8b46-113">Cet exemple illustre un certain nombre de techniques importantes, notamment l’appel d’une méthode qui interagit avec le formulaire à partir d’un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="b8b46-113">This example demonstrates a number of important techniques, including calling a method that interacts with the form from a separate thread.</span></span> <span data-ttu-id="b8b46-114">En outre, cet exemple montre comment vous devez empêcher les utilisateurs d’exécuter simultanément une commande plusieurs fois et comment vous devez vous assurer que le formulaire ne se ferme pas avant l’appel de la procédure de rappel.</span><span class="sxs-lookup"><span data-stu-id="b8b46-114">In addition, this example demonstrates how you must block users from concurrently executing a command multiple times, and how you must ensure that the form does not close before the callback procedure is called.</span></span>  
  
 <span data-ttu-id="b8b46-115">Pour configurer cet exemple, créez une nouvelle application Windows.</span><span class="sxs-lookup"><span data-stu-id="b8b46-115">To set up this example, create a new Windows application.</span></span> <span data-ttu-id="b8b46-116">Placez un contrôle <xref:System.Windows.Forms.Button> et deux contrôles <xref:System.Windows.Forms.Label> sur le formulaire (en acceptant le nom par défaut pour chaque contrôle).</span><span class="sxs-lookup"><span data-stu-id="b8b46-116">Place a <xref:System.Windows.Forms.Button> control and two <xref:System.Windows.Forms.Label> controls on the form (accepting the default name for each control).</span></span> <span data-ttu-id="b8b46-117">Ajoutez le code suivant à la classe du formulaire, en modifiant la chaîne de connexion en fonction des besoins de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="b8b46-117">Add the following code to the form's class, modifying the connection string as necessary for your environment.</span></span>  
  
```vb  
' Add these to the top of the class:  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
  
' Add this code to the form's class:  
  
    ' You'll need this delegate in order to display text from a
    ' thread other than the form's thread. See the HandleCallback  
    ' procedure for more information.  
    ' This same delegate matches both the DisplayStatus
    ' and DisplayResults methods.  
    Private Delegate Sub DisplayInfoDelegate(ByVal Text As String)  
  
    ' This flag ensures that the user doesn't attempt  
    ' to restart the command or close the form while the
    ' asynchronous command is executing.  
    Private isExecuting As Boolean  
  
    ' This example maintains the connection object
    ' externally, so that it's available for closing.  
    Private connection As SqlConnection  
  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
  
        ' If you have not included "Asynchronous Processing=true"  
        ' in the connection string, the command will not be able  
        ' to execute asynchronously.  
        Return "Data Source=(local);Integrated Security=SSPI;" & _  
          "Initial Catalog=AdventureWorks;" & _  
          "Asynchronous Processing=true"  
    End Function  
  
    Private Sub DisplayStatus(ByVal Text As String)  
        Me.Label1.Text = Text  
    End Sub  
  
    Private Sub DisplayResults(ByVal Text As String)  
        Me.Label1.Text = Text  
        DisplayStatus("Ready")  
    End Sub  
  
    Private Sub Form1_FormClosing(ByVal sender As Object, _  
        ByVal e As System.Windows.Forms.FormClosingEventArgs) _  
        Handles Me.FormClosing  
        If isExecuting Then  
            MessageBox.Show(Me, "Can't close the form until " & _  
             "the pending asynchronous command has completed. " & _  
             "Please wait...")  
            e.Cancel = True  
        End If  
    End Sub  
  
    Private Sub Button1_Click( _  
        ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles Button1.Click  
        If isExecuting Then  
            MessageBox.Show(Me, _  
                "Already executing. " & _  
                "Please wait until the current query " & _  
                "has completed.")  
        Else  
            Dim command As SqlCommand  
            Try  
                DisplayResults("")  
                DisplayStatus("Connecting...")  
                connection = New SqlConnection(GetConnectionString())  
                ' To emulate a long-running query, wait for
                ' a few seconds before working with the data.  
                ' This command doesn't do much, but that's the point--  
                ' it doesn't change your data, in the long run.  
                Dim commandText As String = _  
                    "WAITFOR DELAY '0:0:05';" & _  
                    "UPDATE Production.Product " & _  
                    "SET ReorderPoint = ReorderPoint + 1 " & _  
                    "WHERE ReorderPoint Is Not Null;" & _  
                    "UPDATE Production.Product " & _  
                    "SET ReorderPoint = ReorderPoint - 1 " & _  
                    "WHERE ReorderPoint Is Not Null"  
  
                command = New SqlCommand(commandText, connection)  
                connection.Open()  
  
                DisplayStatus("Executing...")  
                isExecuting = True  
                ' Although it's not required that you pass the
                ' SqlCommand object as the second parameter in the
                ' BeginExecuteNonQuery call, doing so makes it easier  
                ' to call EndExecuteNonQuery in the callback procedure.  
                Dim callback As New _  
                      AsyncCallback(AddressOf HandleCallback)  
  
                ' Once the BeginExecuteNonQuery method is called,  
                ' the code continues--and the user can interact with  
                ' the form--while the server executes the query.  
  
                command.BeginExecuteNonQuery(callback, command)  
  
            Catch ex As Exception  
                isExecuting = False  
                DisplayStatus($"Ready (last error: {ex.Message})")
                If connection IsNot Nothing Then  
                    connection.Close()  
                End If  
            End Try  
        End If  
    End Sub  
  
    Private Sub HandleCallback(ByVal result As IAsyncResult)  
        Try  
            ' Retrieve the original command object, passed  
            ' to this procedure in the AsyncState property  
            ' of the IAsyncResult parameter.  
            Dim command As SqlCommand = _  
                CType(result.AsyncState, SqlCommand)  
            Dim rowCount As Integer = _  
                command.EndExecuteNonQuery(result)  
            Dim rowText As String = " rows affected."  
            If rowCount = 1 Then  
                rowText = " row affected."  
            End If  
            rowText = rowCount & rowText  
  
            ' You may not interact with the form and its contents  
            ' from a different thread, and this callback procedure  
            ' is all but guaranteed to be running from a different
            ' thread than the form. Therefore you cannot simply call
            ' code that displays the results, like this:  
            ' DisplayResults(rowText)  
  
            ' Instead, you must call the procedure from the form's  
            ' thread. One simple way to accomplish this is to call
            ' the Invoke method of the form, which calls the delegate
            ' you supply from the form's thread.
            Dim del As New _  
                DisplayInfoDelegate(AddressOf DisplayResults)  
            Me.Invoke(del, rowText)  
  
        Catch ex As Exception  
            ' Because you're now running code in a separate thread,
            ' if you don't handle the exception here, none of your
            ' other code will catch the exception. Because none of
            ' your code is on the call stack in this thread, there's
            ' nothing higher up the stack to catch the exception if
            ' you don't handle it here. You can either log the
            ' exception or invoke a delegate (as in the non-error
            ' case in this example) to display the error on the form.
            ' In no case can you simply display the error without
            ' executing a delegate as in the Try block here.  
  
            ' You can create the delegate instance as you
            ' invoke it, like this:  
            Me.Invoke(New _  
                DisplayInfoDelegate(AddressOf DisplayStatus), _  
                $"Ready (last error: {ex.Message}")
        Finally  
            isExecuting = False  
            If connection IsNot Nothing Then  
                connection.Close()  
            End If  
        End Try  
    End Sub  
```  
  
```csharp  
// Add these to the top of the class, if they're not already there:  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
// Hook up the form's Load event handler (you can double-click on
// the form's design surface in Visual Studio), and then add
// this code to the form's class:  
  
// You'll need this delegate in order to display text from a thread  
// other than the form's thread. See the HandleCallback  
// procedure for more information.  
// This same delegate matches both the DisplayStatus
// and DisplayResults methods.  
private delegate void DisplayInfoDelegate(string Text);  
  
// This flag ensures that the user doesn't attempt  
// to restart the command or close the form while the
// asynchronous command is executing.  
private bool isExecuting;  
  
// This example maintains the connection object
// externally, so that it's available for closing.  
private SqlConnection connection;  
  
private static string GetConnectionString()  
{  
    // To avoid storing the connection string in your code,
    // you can retrieve it from a configuration file.
  
    // If you have not included "Asynchronous Processing=true" in the  
    // connection string, the command will not be able  
    // to execute asynchronously.  
    return "Data Source=(local);Integrated Security=SSPI;" +  
    "Initial Catalog=AdventureWorks; Asynchronous Processing=true";  
}  
  
private void DisplayStatus(string Text)  
{  
    this.label1.Text = Text;  
}  
  
private void DisplayResults(string Text)  
{  
    this.label1.Text = Text;  
    DisplayStatus("Ready");  
}  
  
private void Form1_FormClosing(object sender, System.Windows.Forms.FormClosingEventArgs e)  
{  
    if (isExecuting)  
    {  
        MessageBox.Show(this, "Can't close the form until " +  
        "the pending asynchronous command has completed. Please " +  
        "wait...");
        e.Cancel = true;  
    }  
}  
  
private void button1_Click(object sender, System.EventArgs e)  
{  
    if (isExecuting)  
    {  
        MessageBox.Show(this, "Already executing. Please wait until " +  
        "the current query has completed.");  
    }  
    else  
    {  
        SqlCommand command = null;  
        try  
        {  
            DisplayResults("");  
            DisplayStatus("Connecting...");  
            connection = new SqlConnection(GetConnectionString());  
            // To emulate a long-running query, wait for
            // a few seconds before working with the data.  
            // This command doesn't do much, but that's the point--  
            // it doesn't change your data, in the long run.  
            string commandText =  
                "WAITFOR DELAY '0:0:05';" +  
                "UPDATE Production.Product " +  
                "SET ReorderPoint = ReorderPoint + 1 " +  
                "WHERE ReorderPoint Is Not Null;" +  
                "UPDATE Production.Product " +  
                "SET ReorderPoint = ReorderPoint - 1 " +  
                "WHERE ReorderPoint Is Not Null";  
  
            command = new SqlCommand(commandText, connection);  
            connection.Open();  
  
            DisplayStatus("Executing...");  
            isExecuting = true;  
            // Although it's not required that you pass the
            // SqlCommand object as the second parameter in the
            // BeginExecuteNonQuery call, doing so makes it easier  
            // to call EndExecuteNonQuery in the callback procedure.  
            AsyncCallback callback = new AsyncCallback(HandleCallback);  
  
            // Once the BeginExecuteNonQuery method is called,  
            // the code continues--and the user can interact with  
            // the form--while the server executes the query.  
            command.BeginExecuteNonQuery(callback, command);  
  
        }  
        catch (Exception ex)  
        {  
            isExecuting = false;  
            DisplayStatus($"Ready (last error: {ex.Message})");
            if (connection != null)  
            {  
                connection.Close();  
            }  
        }  
    }  
}  
  
private void HandleCallback(IAsyncResult result)  
{  
    try  
    {  
        // Retrieve the original command object, passed  
        // to this procedure in the AsyncState property  
        // of the IAsyncResult parameter.  
        SqlCommand command = (SqlCommand)result.AsyncState;  
        int rowCount = command.EndExecuteNonQuery(result);  
        string rowText = " rows affected.";  
        if (rowCount == 1)  
        {  
            rowText = " row affected.";  
        }  
        rowText = rowCount + rowText;  
  
        // You may not interact with the form and its contents  
        // from a different thread, and this callback procedure  
        // is all but guaranteed to be running from a different thread  
        // than the form. Therefore you cannot simply call code that
        // displays the results, like this:  
        // DisplayResults(rowText)  
  
        // Instead, you must call the procedure from the form's thread.  
        // One simple way to accomplish this is to call the Invoke  
        // method of the form, which calls the delegate you supply  
        // from the form's thread.
        DisplayInfoDelegate del =
         new DisplayInfoDelegate(DisplayResults);  
        this.Invoke(del, rowText);  
    }  
    catch (Exception ex)  
    {  
        // Because you're now running code in a separate thread,
        // if you don't handle the exception here, none of your other  
        // code will catch the exception. Because none of your  
        // code is on the call stack in this thread, there's nothing  
        // higher up the stack to catch the exception if you don't
        // handle it here. You can either log the exception or
        // invoke a delegate (as in the non-error case in this
        // example) to display the error on the form. In no case  
        // can you simply display the error without executing a
        // delegate as in the try block here.
  
        // You can create the delegate instance as you
        // invoke it, like this:  
        this.Invoke(new DisplayInfoDelegate(DisplayStatus),  
            $"Ready (last error: {ex.Message}");
    }  
    finally  
    {  
        isExecuting = false;  
        if (connection != null)  
        {  
            connection.Close();  
        }  
    }  
}  
  
private void Form1_Load(object sender, System.EventArgs e)  
{  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    this.FormClosing += new System.Windows.Forms.  
        FormClosingEventHandler(this.Form1_FormClosing);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8b46-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8b46-118">See also</span></span>

- [<span data-ttu-id="b8b46-119">Opérations asynchrones</span><span class="sxs-lookup"><span data-stu-id="b8b46-119">Asynchronous Operations</span></span>](asynchronous-operations.md)
- [<span data-ttu-id="b8b46-120">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b8b46-120">ADO.NET Overview</span></span>](../ado-net-overview.md)
