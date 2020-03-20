---
title: DataContract Surrogate
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 7ef78c4361c055d7be35c03a3c8717e86aceddab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183837"
---
# <a name="datacontract-surrogate"></a>DataContract Surrogate
Cet exemple illustre comment personnaliser des processus tels que la sérialisation, la désérialisation, l’exportation et l’importation de schémas à l’aide d’une classe de substitution d’un contrat de données. Cet exemple montre comment utiliser une mère porteuse dans un scénario de client et de serveur où les données sont sérialisées et transmises entre un client et un service de la Windows Communication Foundation (WCF).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 L'exemple utilise le contrat de service suivant :  
  
```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[AllowNonSerializableTypes]  
public interface IPersonnelDataService  
{  
    [OperationContract]  
    void AddEmployee(Employee employee);  
  
    [OperationContract]  
    Employee GetEmployee(string name);  
}  
```  
  
 L'opération `AddEmployee` permet aux utilisateurs d'ajouter des données sur de nouveaux employés et l'opération `GetEmployee` permet de lancer une recherche sur les employés en fonction de leur nom.  
  
 Ces opérations utilisent le type de données suivant :  
  
```csharp
[DataContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
class Employee  
{  
    [DataMember]  
    public DateTime dateHired;  
  
    [DataMember]  
    public Decimal salary;  
  
    [DataMember]  
    public Person person;  
}  
```  
  
 Dans le type `Employee`, la classe `Person` (contenue dans l'exemple de code suivant) ne peut pas être sérialisée par le <xref:System.Runtime.Serialization.DataContractSerializer>, celle-ci ne correspondant pas à une classe de contrat de données valable.  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Vous pouvez appliquer l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> à la classe `Person`, mais cela n'est pas toujours possible. Par exemple, la classe `Person` peut être définie dans un assembly distinct sur lequel vous n'exercez aucun contrôle.  
  
 L'une des solutions permettant alors de sérialiser la classe `Person` consiste à la remplacer par une autre classe signalée par l'attribut <xref:System.Runtime.Serialization.DataContractAttribute>, puis à copier les données requises dans cette nouvelle classe. L'objectif de l'opération ci-dessus est le suivant : présenter la classe `Person` comme DataContract au <xref:System.Runtime.Serialization.DataContractSerializer>. Remarque : il s'agit d'une solution parmi d'autres permettant de sérialiser les classes n'appartenant pas à un contrat de données.  
  
 L'exemple remplace logiquement la classe `Person` par une classe différente nommée `PersonSurrogated`.  
  
```csharp
[DataContract(Name="Person", Namespace = "http://Microsoft.ServiceModel.Samples")]  
public class PersonSurrogated  
{  
    [DataMember]  
    public string FirstName;  
  
    [DataMember]  
    public string LastName;  
  
    [DataMember]  
    public int Age;  
}  
```  
  
 Le substitut de contrat de données est utilisé pour effectuer ce remplacement. Un substitut de contrat de données est une classe qui implémente <xref:System.Runtime.Serialization.IDataContractSurrogate>. Dans cet exemple, la classe `AllowNonSerializableTypesSurrogate` implémente cette interface.  
  
 Dans l’implémentation d’interface, la première tâche consiste à définir un type mappant la classe `Person` à la classe `PersonSurrogated`. Ce processus de mappage est utilisé à la fois pendant la sérialisation et l'exportation des schémas. Il s'effectue en implémentant la méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29>.  
  
```csharp
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 La méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> mappe une instance de la classe `Person` à une instance de la classe `PersonSurrogated` pendant la sérialisation, tel qu'illustré dans l'exemple de code suivant.  
  
```csharp
public object GetObjectToSerialize(object obj, Type targetType)  
{  
    if (obj is Person)  
    {  
        Person person = (Person)obj;  
        PersonSurrogated personSurrogated = new PersonSurrogated();  
        personSurrogated.FirstName = person.firstName;  
        personSurrogated.LastName = person.lastName;  
        personSurrogated.Age = person.age;  
        return personSurrogated;  
    }  
    return obj;  
}  
```  
  
 La méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> permet d’effectuer le mappage dans le sens inverse lors de la désérialisation, tel qu’illustré dans l’exemple de code suivant.  
  
```csharp
public object GetDeserializedObject(object obj,
Type targetType)  
{  
    if (obj is PersonSurrogated)  
    {  
        PersonSurrogated personSurrogated = (PersonSurrogated)obj;  
        Person person = new Person();  
        person.firstName = personSurrogated.FirstName;  
        person.lastName = personSurrogated.LastName;  
        person.age = personSurrogated.Age;  
        return person;  
    }  
    return obj;  
}  
```  
  
 Pour mapper le contrat de données `PersonSurrogated` à la classe `Person` existante lors de l'importation des schémas, l'exemple implémente la méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29>, tel qu'illustré dans l'exemple de code suivant.  
  
```csharp
public Type GetReferencedTypeOnImport(string typeName,
               string typeNamespace, object customData)  
{  
if (  
typeNamespace.Equals("http://schemas.datacontract.org/2004/07/DCSurrogateSample")  
)  
    {  
         if (typeName.Equals("PersonSurrogated"))  
        {  
             return typeof(Person);  
        }  
     }  
     return null;  
}  
```  
  
 L'exemple de code suivant achève l'implémentation de l'interface <xref:System.Runtime.Serialization.IDataContractSurrogate>.  
  
```csharp
public System.CodeDom.CodeTypeDeclaration ProcessImportedType(  
          System.CodeDom.CodeTypeDeclaration typeDeclaration,
          System.CodeDom.CodeCompileUnit compileUnit)  
{  
    return typeDeclaration;  
}  
public object GetCustomDataToExport(Type clrType,
                               Type dataContractType)  
{  
    return null;  
}  
  
public object GetCustomDataToExport(  
System.Reflection.MemberInfo memberInfo, Type dataContractType)  
{  
    return null;  
}  
public void GetKnownCustomDataTypes(  
        KnownTypeCollection customDataTypes)  
{  
    // It does not matter what we do here.  
    throw new NotImplementedException();  
}  
```  
  
 Dans cet exemple, le substitut est activé dans ServiceModel par un attribut appelé `AllowNonSerializableTypesAttribute`. Les développeurs doivent appliquer cet attribut dans leur contrat de service respectif, tel qu'illustré dans le contrat de service `IPersonnelDataService` ci-dessus. Cet attribut implémente `IContractBehavior` et définit le substitut sur les opérations dans les méthodes `ApplyClientBehavior` et `ApplyDispatchBehavior`.  
  
 L'attribut n'est pas nécessaire dans ce cas. Il est utilisé à des fins d'illustration dans cet exemple. Les utilisateurs peuvent également activer un substitut en ajoutant manuellement un `IContractBehavior`, `IEndpointBehavior` ou `IOperationBehavior` similaire à l'aide du code ou de la configuration.  
  
 L'implémentation `IContractBehavior` recherche les opérations qui utilisent DataContract en vérifiant si un comportement `DataContractSerializerOperationBehavior` leur correspondant est enregistré. Si tel est le cas, elle définit la propriété `DataContractSurrogate` sur ce comportement. L'exemple de code suivant illustre les modalités de ce processus. La définition du substitut sur ce comportement d’opération permet pour ce dernier une sérialisation et une désérialisation.  
  
```csharp
public void ApplyClientBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime proxy)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
public void ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatch)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
private static void ApplyDataContractSurrogate(OperationDescription description)  
{  
    DataContractSerializerOperationBehavior dcsOperationBehavior = description.Behaviors.Find<DataContractSerializerOperationBehavior>();  
    if (dcsOperationBehavior != null)  
    {  
        if (dcsOperationBehavior.DataContractSurrogate == null)  
            dcsOperationBehavior.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
    }  
}  
```  
  
 D'autres étapes sont nécessaires pour incorporer le substitut et ainsi pouvoir l'utiliser lors de la génération des métadonnées. Pour ce faire, l'une des solutions consiste à fournir une extension `IWsdlExportExtension`, tel qu'illustré dans cet exemple. Une autre solution consiste à modifier directement le `WsdlExporter`.  
  
 L’attribut `AllowNonSerializableTypesAttribute` `IWsdlExportExtension` met `IContractBehavior`en œuvre et . L’extension peut `IContractBehavior` être `IEndpointBehavior` soit un ou dans ce cas. Son implémentation de la méthode `IWsdlExportExtension.ExportContract` active le substitut en l'ajoutant au `XsdDataContractExporter` utilisé lors de la génération des schémas du DataContract. L'extrait de code suivant montre comment procéder.  
  
```csharp
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (exporter == null)  
        throw new ArgumentNullException("exporter");  
  
    object dataContractExporter;  
    XsdDataContractExporter xsdDCExporter;  
    if (!exporter.State.TryGetValue(typeof(XsdDataContractExporter), out dataContractExporter))  
    {  
        xsdDCExporter = new XsdDataContractExporter(exporter.GeneratedXmlSchemas);  
        exporter.State.Add(typeof(XsdDataContractExporter), xsdDCExporter);  
    }  
    else  
    {  
        xsdDCExporter = (XsdDataContractExporter)dataContractExporter;  
    }  
    if (xsdDCExporter.Options == null)  
        xsdDCExporter.Options = new ExportOptions();  
  
    if (xsdDCExporter.Options.DataContractSurrogate == null)  
        xsdDCExporter.Options.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
}  
```  
  
 Lorsque vous exécutez l'exemple, le client appelle la méthode AddEmployee, puis la méthode GetEmployee afin de s'assurer que le premier appel a réussi. Le résultat de la demande d'opération GetEmployee est affiché dans la fenêtre de console du client. L’entreprise GetEmployee doit réussir à trouver l’employé et imprimer "trouvé".  
  
> [!NOTE]
> Cet exemple illustre comment incorporer un substitut à des fins de sérialisation, désérialisation et génération de métadonnées. Il ne montre pas en revanche comment incorporer un substitut pour permettre la génération de code à partir des métadonnées. Pour voir un échantillon de la façon dont une mère porteuse peut être utilisée pour brancher la génération de code client, consultez l’échantillon [custom WSDL Publication.](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Pour créer l’édition C de la solution, suivez les instructions dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
