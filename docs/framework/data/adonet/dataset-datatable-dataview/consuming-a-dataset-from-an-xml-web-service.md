---
title: Consommation d’un DataSet à partir d’un service web XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: d7328949e3eb4822b1a645bb5f0c1866f01ecb0a
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389749"
---
# <a name="consume-a-dataset-from-an-xml-web-service"></a>Consommez un DataSet à partir d’un service Web XML

L'objet <xref:System.Data.DataSet> a été conçu avec une architecture déconnectée, en partie afin de faciliter le transport des données sur Internet. Le **DataSet** est « sérialisable » en ce qu’il peut être spécifié comme une entrée ou une sortie des services Web XML sans aucun codage supplémentaire requis pour diffuser le contenu du **DataSet** à partir d’un service Web XML à un client et à l’arrière. Le **DataSet** est implicitement converti en flux XML à l’aide du format DiffGram, envoyé sur le réseau, puis reconstruit à partir du flux XML sous forme de **DataSet** sur l’extrémité de réception. Vous disposez ainsi d’une méthode alliant simplicité et souplesse pour la transmission et le retour de données relationnelles à l’aide des services web XML. Pour plus d’informations sur le format DiffGram, voir [DiffGrams](diffgrams.md).  
  
 L’exemple suivant montre comment créer un service Web XML et un client qui utilisent le **DataSet** pour transporter des données relationnelles (y compris les données modifiées) et résoudre toutes les mises à jour vers la source de données d’origine.  
  
> [!NOTE]
> Nous recommandons de toujours tenir compte des impératifs de sécurité lorsque vous créez un service Web XML. Pour plus d’informations sur la sécurisation d’un service Web XML, voir [Securing XML Web Services Created Using ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).  
  
## <a name="create-an-xml-web-service"></a>Créer un service Web XML
  
1. Créez le service web XML.  
  
     Dans l’exemple, un service Web XML est créé qui renvoie les données, dans ce cas une liste de clients de la base de données **Northwind,** et reçoit un **DataSet** avec mises à jour des données, que le service Web XML résout à la source de données d’origine.  
  
     Le service Web XML expose deux méthodes: **GetCustomers**, pour retourner la liste des clients, et **UpdateCustomers**, pour résoudre les mises à jour de retour à la source de données. Le service Web XML est stocké sur le serveur Web dans le fichier DataSetSample.asmx. Le code suivant représente le contenu de ce fichier.  
  
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
  
     Dans un scénario typique, la méthode **UpdateCustomers** serait écrite pour attraper les violations optimistes de la concurrence. Par souci de simplicité, cet exemple ne le fait pas. Pour plus d’informations sur la concurrence optimiste, voir [Concordurrency Optimiste](../optimistic-concurrency.md).  
  
2. Créez un proxy de service web XML.  
  
     Les clients du service web XML ont besoin d’un proxy SOAP pour pouvoir utiliser les méthodes exposées. Vous pouvez faire en sorte que Visual Studio génère ce proxy pour vous. En définissant une référence Web à un service Web existant depuis Visual Studio, tout le comportement décrit dans cette étape se passe de façon transparente. Si vous souhaitez créer la classe proxy vous-même, passez à cette description. Le plus souvent, cependant, l'utilisation de Visual Studio pour créer la classe proxy pour l'application cliente suffit.  
  
     Un proxy peut être créé à l'aide de l'outil Web Services Description Language Tool. Par exemple, si le service Web XML est exposé à l’URL, `http://myserver/data/DataSetSample.asmx`émettent une commande telle que ce qui suit pour créer un proxy Visual Basic .NET avec un espace nom de **WebData.DSSample** et le stocker dans le fichier sample.vb.  
  
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
  
     Si vous souhaitez que Visual Studio génère la classe de proxy de service Web pour vous, il suffit de créer le projet client, et, dans la fenêtre Solution Explorer, cliquez à droite sur le projet, puis sélectionnez **Add** > **Service Reference**. Dans la boîte de dialogue **Add Service Reference,** sélectionnez **Advanced**, puis **sélectionnez Ajouter la référence Web**. Sélectionnez le service Web de la liste des services Web disponibles (cela peut nécessiter la fourniture de l’adresse du point de terminaison du service Web si le service Web n’est pas disponible dans la solution actuelle ou sur l’ordinateur actuel). Si vous créez le proxy de service Web XML vous-même (comme décrit à l'étape précédente), vous pouvez l'importer dans votre code client et utiliser les méthodes de service Web XML.

     Le code d’échantillon suivant importe la bibliothèque proxy, appelle **GetCustomers** pour obtenir une liste de clients, ajoute un nouveau client, puis retourne un **DataSet** avec les mises à jour de **UpdateCustomers**.  
  
     L’exemple passe le **DataSet** retourné par **DataSet.GetChanges** à **UpdateCustomers** parce que seules les lignes modifiées doivent être passées à **UpdateCustomers**. **UpdateCustomers** renvoie le **DataSet**résolu , que vous pouvez ensuite **fusionner** dans le **DataSet** existant pour intégrer les modifications résolues et les informations d’erreur de ligne de la mise à jour. Le code suivant suppose que vous avez utilisé Visual Studio pour créer la référence Web, et que vous avez rebaptisé la référence Web à DsSample dans la boîte de dialogue **Add Web Reference.**  
  
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
- [Remplissage d’un DataSet à partir d’un DataAdapter](../populating-a-dataset-from-a-dataadapter.md)
- [Mise à jour des sources de données avec les DataAdapter](../updating-data-sources-with-dataadapters.md)
- [Paramètres DataAdapter](../dataadapter-parameters.md)
- [Outil Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
