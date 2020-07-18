---
title: Consommer un DataSet à partir d’un service Web XML
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: e6dc32274cc3b0d7ec9d66a837a422c87fb2468b
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416212"
---
# <a name="consume-a-dataset-from-an-xml-web-service"></a>Consommer un DataSet à partir d’un service Web XML

L'objet <xref:System.Data.DataSet> a été conçu avec une architecture déconnectée, en partie afin de faciliter le transport des données sur Internet. Le **DataSet** est « sérialisable » en ce qu’il peut être spécifié comme entrée ou sortie à partir de services Web XML sans codage supplémentaire requis pour diffuser le contenu du **DataSet** à partir d’un service Web XML vers un client et inversement. Le **jeu de données** est implicitement converti en un flux XML à l’aide du format DiffGram, envoyé sur le réseau, puis reconstruit à partir du flux XML en tant que **jeu de données** sur la terminaison de réception. Vous bénéficiez ainsi d’une méthode simple et flexible pour la transmission et le retour de données relationnelles à l’aide des services Web XML. Pour plus d’informations sur le format DiffGram, consultez [DiffGrams](diffgrams.md).  
  
 L’exemple suivant montre comment créer un service Web XML et un client qui utilisent le **DataSet** pour transporter des données relationnelles (y compris des données modifiées) et réactiver les mises à jour dans la source de données d’origine.  
  
> [!NOTE]
> La transmission `DataSet` ou `DataTable` les instances dans le cadre des appels de service Web XML ne sont pas sécurisées si l’entrée n’est pas approuvée. Pour plus d’informations, consultez [Guide de sécurité des jeux de données et des DataTable](security-guidance.md).
> Nous vous recommandons également de toujours prendre en compte les implications en matière de sécurité lors de la création d’un service Web XML. Pour plus d’informations sur la sécurisation d’un service Web XML, consultez [sécurisation des services Web XML créés à l’aide de ASP.net](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).  
  
## <a name="create-an-xml-web-service"></a>Créer un service Web XML
  
1. Créez le service web XML.  
  
     Dans l’exemple, un service Web XML est créé. il retourne des données, dans ce cas une liste de clients de la base de données **Northwind** , et reçoit un **DataSet** avec des mises à jour des données, que le service Web XML résout en retour à la source de données d’origine.  
  
     Le service Web XML expose deux méthodes : **GetCustomers**, pour retourner la liste des clients, et **UpdateCustomers**, pour répercuter à nouveau les mises à jour dans la source de données. Le service Web XML est stocké sur le serveur Web dans le fichier DataSetSample.asmx. Le code suivant représente le contenu de ce fichier.  
  
    ```vb  
    <% @ WebService Language = "vb" Class = "Sample" %>  
    Imports System  
    Imports System.Data  
    Imports System.Data.SqlClient  
    Imports System.Web.Services  
  
    <WebService(Namespace:="http://microsoft.com/webservices/")> _  
    Public Class Sample  
  
    Public connection As SqlConnection = New SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind")  
  
      <WebMethod( Description := "Returns Northwind Customers", EnableSession := False )> _  
      Public Function GetCustomers() As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
          "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
        Dim custDS As DataSet = New DataSet()  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
        adapter.Fill(custDS, "Customers")  
  
        Return custDS  
      End Function  
  
      <WebMethod( Description := "Updates Northwind Customers", EnableSession := False )> _  
      Public Function UpdateCustomers(custDS As DataSet) As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter()  
  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Customers (CustomerID, CompanyName) " & _  
          "Values(@CustomerID, @CompanyName)", connection)  
        adapter.InsertCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.InsertCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Customers Set CustomerID = @CustomerID, " & _  
          "CompanyName = @CompanyName WHERE CustomerID = " & _  
          @OldCustomerID", connection)  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        Dim parameter As SqlParameter = _  
          adapter.UpdateCommand.Parameters.Add( _  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Customers WHERE CustomerID = @CustomerID", _  
          connection)  
        parameter = adapter.DeleteCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.Update(custDS, "Customers")  
  
        Return custDS  
      End Function  
    End Class  
    ```  
  
    ```csharp  
    <% @ WebService Language = "C#" Class = "Sample" %>  
    using System;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Web.Services;  
  
    [WebService(Namespace="http://microsoft.com/webservices/")]  
    public class Sample  
    {  
      public SqlConnection connection = new SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind");  
  
      [WebMethod( Description = "Returns Northwind Customers", EnableSession = false )]  
      public DataSet GetCustomers()  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter(  
          "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
        DataSet custDS = new DataSet();  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
        adapter.Fill(custDS, "Customers");  
  
        return custDS;  
      }  
  
      [WebMethod( Description = "Updates Northwind Customers",  
        EnableSession = false )]  
      public DataSet UpdateCustomers(DataSet custDS)  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        adapter.InsertCommand = new SqlCommand(  
          "INSERT INTO Customers (CustomerID, CompanyName) " +  
          "Values(@CustomerID, @CompanyName)", connection);  
        adapter.InsertCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.InsertCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
  
        adapter.UpdateCommand = new SqlCommand(  
          "UPDATE Customers Set CustomerID = @CustomerID, " +  
          "CompanyName = @CompanyName WHERE CustomerID = " +  
          "@OldCustomerID", connection);  
        adapter.UpdateCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.UpdateCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
        SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.DeleteCommand = new SqlCommand(  
        "DELETE FROM Customers WHERE CustomerID = @CustomerID",  
         connection);  
        parameter = adapter.DeleteCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.Update(custDS, "Customers");  
  
        return custDS;  
      }  
    }  
    ```  
  
     Dans un scénario classique, la méthode **UpdateCustomers** serait écrite pour intercepter les violations d’accès simultané optimiste. Par souci de simplicité, cet exemple ne le fait pas. Pour plus d’informations sur l’accès concurrentiel optimiste, consultez [accès concurrentiel optimiste](../optimistic-concurrency.md).  
  
2. Créez un proxy de service web XML.  
  
     Les clients du service web XML ont besoin d’un proxy SOAP pour pouvoir utiliser les méthodes exposées. Vous pouvez faire en sorte que Visual Studio génère ce proxy pour vous. En définissant une référence Web à un service Web existant depuis Visual Studio, tout le comportement décrit dans cette étape se passe de façon transparente. Si vous souhaitez créer la classe proxy vous-même, passez à cette description. Le plus souvent, cependant, l'utilisation de Visual Studio pour créer la classe proxy pour l'application cliente suffit.  
  
     Un proxy peut être créé à l'aide de l'outil Web Services Description Language Tool. Par exemple, si le service Web XML est exposé à l’URL `http://myserver/data/DataSetSample.asmx` , émettez une commande telle que la suivante pour créer un Visual Basic proxy .net avec un espace de noms **WebData. DSSample** et stockez-le dans le fichier Sample. vb.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     Pour créer un proxy C# dans le fichier sample.cs, écrivez la commande suivante.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     Le proxy peut ensuite être compilé en tant que bibliothèque et importé dans le client du service web XML. Pour compiler le code Visual Basic .NET du proxy stocké dans sample.vb en tant que sample.dll, écrivez la commande suivante.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     Pour compiler le code C# du proxy stocké dans sample.cs en tant que sample.dll, écrivez la commande suivante.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. Créez un client de service web XML.  
  
     Si vous souhaitez que Visual Studio génère la classe proxy de service Web pour vous, créez simplement le projet client et, dans la fenêtre Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter**une  >  **référence de service**. Dans la boîte de dialogue **Ajouter une référence de service** , sélectionnez **avancé**, puis **Ajouter une référence Web**. Sélectionnez le service Web dans la liste des services Web disponibles (vous devrez peut-être fournir l’adresse du point de terminaison du service Web si le service Web n’est pas disponible dans la solution actuelle ou sur l’ordinateur actuel). Si vous créez le proxy de service Web XML vous-même (comme décrit à l'étape précédente), vous pouvez l'importer dans votre code client et utiliser les méthodes de service Web XML.

     L’exemple de code suivant importe la bibliothèque proxy, appelle **GetCustomers** pour obtenir une liste de clients, ajoute un nouveau client, puis retourne un **DataSet** avec les mises à jour de **UpdateCustomers**.  
  
     L’exemple passe le **jeu de données** retourné par **DataSet. GetChanges** à **UpdateCustomers** , car seules les lignes modifiées doivent être passées à **UpdateCustomers**. **UpdateCustomers** retourne le **DataSet**résolu, que vous pouvez ensuite **fusionner** dans le **DataSet** existant pour incorporer les modifications résolues et toutes les informations d’erreur de ligne de la mise à jour. Le code suivant suppose que vous avez utilisé Visual Studio pour créer la référence Web et que vous avez renommé la référence Web en DsSample dans la boîte de dialogue **Ajouter une référence Web** .  
  
    ```vb  
    Imports System  
    Imports System.Data  
  
    Public Class Client  
  
      Public Shared Sub Main()  
        Dim proxySample As New DsSample.Sample ()  ' Proxy object.  
        Dim customersDataSet As DataSet = proxySample.GetCustomers()  
        Dim customersTable As DataTable = _  
          customersDataSet.Tables("Customers")  
  
        Dim rowAs DataRow = customersTable.NewRow()  
        row("CustomerID") = "ABCDE"  
        row("CompanyName") = "New Company Name"  
        customersTable.Rows.Add(row)  
  
        Dim updateDataSet As DataSet = _  
          proxySample.UpdateCustomers(customersDataSet.GetChanges())  
  
        customersDataSet.Merge(updateDataSet)  
        customersDataSet.AcceptChanges()  
      End Sub  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using System.Data;  
  
    public class Client  
    {  
      public static void Main()  
      {  
        Sample proxySample = new DsSample.Sample();  // Proxy object.  
        DataSet customersDataSet = proxySample.GetCustomers();  
        DataTable customersTable = customersDataSet.Tables["Customers"];  
  
        DataRow row = customersTable.NewRow();  
        row["CustomerID"] = "ABCDE";  
        row["CompanyName"] = "New Company Name";  
        customersTable.Rows.Add(row);  
  
        DataSet updateDataSet = new DataSet();  
  
        updateDataSet =
          proxySample.UpdateCustomers(customersDataSet.GetChanges());  
  
        customersDataSet.Merge(updateDataSet);  
        customersDataSet.AcceptChanges();  
      }  
    }  
    ```  
  
     Si vous décidez de créer la classe proxy vous-même, vous devez prendre les mesures supplémentaires suivantes. Pour compiler l'exemple, fournissez la bibliothèque de proxy qui a été créée (sample.dll) ainsi que les bibliothèques .NET connexes. Pour compiler la version Visual Basic .NET de l'exemple, stockée dans le fichier client.vb, écrivez la commande suivante.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Pour compiler la version C# de l'exemple, stockée dans le fichier client.cs, écrivez la commande suivante.  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [ADO.NET](../index.md)
- [DataSets, DataTables et DataViews](index.md)
- [DataTables](datatables.md)
- [Remplissage d'un DataSet à partir d'un DataAdapter](../populating-a-dataset-from-a-dataadapter.md)
- [Mise à jour des sources de données avec les DataAdapter](../updating-data-sources-with-dataadapters.md)
- [Paramètres DataAdapter](../dataadapter-parameters.md)
- [Outil Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
