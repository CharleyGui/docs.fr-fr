---
title: DataContract Surrogate
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 9677e3cf024e6c1e5b2f3360423ab55536748495
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600034"
---
# <a name="datacontract-surrogate"></a><span data-ttu-id="52468-102">DataContract Surrogate</span><span class="sxs-lookup"><span data-stu-id="52468-102">DataContract Surrogate</span></span>
<span data-ttu-id="52468-103">Cet exemple illustre comment personnaliser des processus tels que la sérialisation, la désérialisation, l’exportation et l’importation de schémas à l’aide d’une classe de substitution d’un contrat de données.</span><span class="sxs-lookup"><span data-stu-id="52468-103">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="52468-104">Cet exemple montre comment utiliser un substitut dans un scénario de client et de serveur où les données sont sérialisées et transmises entre un service et un client Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="52468-104">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52468-105">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="52468-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="52468-106">L'exemple utilise le contrat de service suivant :</span><span class="sxs-lookup"><span data-stu-id="52468-106">The sample uses the following service contract:</span></span>  
  
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
  
 <span data-ttu-id="52468-107">L'opération `AddEmployee` permet aux utilisateurs d'ajouter des données sur de nouveaux employés et l'opération `GetEmployee` permet de lancer une recherche sur les employés en fonction de leur nom.</span><span class="sxs-lookup"><span data-stu-id="52468-107">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="52468-108">Ces opérations utilisent le type de données suivant :</span><span class="sxs-lookup"><span data-stu-id="52468-108">These operations use the following data type:</span></span>  
  
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
  
 <span data-ttu-id="52468-109">Dans le type `Employee`, la classe `Person` (contenue dans l'exemple de code suivant) ne peut pas être sérialisée par le <xref:System.Runtime.Serialization.DataContractSerializer>, celle-ci ne correspondant pas à une classe de contrat de données valable.</span><span class="sxs-lookup"><span data-stu-id="52468-109">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="52468-110">Vous pouvez appliquer l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> à la classe `Person`, mais cela n'est pas toujours possible.</span><span class="sxs-lookup"><span data-stu-id="52468-110">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="52468-111">Par exemple, la classe `Person` peut être définie dans un assembly distinct sur lequel vous n'exercez aucun contrôle.</span><span class="sxs-lookup"><span data-stu-id="52468-111">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="52468-112">L'une des solutions permettant alors de sérialiser la classe `Person` consiste à la remplacer par une autre classe signalée par l'attribut <xref:System.Runtime.Serialization.DataContractAttribute>, puis à copier les données requises dans cette nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="52468-112">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with <xref:System.Runtime.Serialization.DataContractAttribute> and copy over necessary data to the new class.</span></span> <span data-ttu-id="52468-113">L'objectif de l'opération ci-dessus est le suivant : présenter la classe `Person` comme DataContract au <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="52468-113">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="52468-114">Remarque : il s'agit d'une solution parmi d'autres permettant de sérialiser les classes n'appartenant pas à un contrat de données.</span><span class="sxs-lookup"><span data-stu-id="52468-114">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="52468-115">L'exemple remplace logiquement la classe `Person` par une classe différente nommée `PersonSurrogated`.</span><span class="sxs-lookup"><span data-stu-id="52468-115">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
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
  
 <span data-ttu-id="52468-116">Le substitut de contrat de données est utilisé pour effectuer ce remplacement.</span><span class="sxs-lookup"><span data-stu-id="52468-116">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="52468-117">Un substitut de contrat de données est une classe qui implémente <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span><span class="sxs-lookup"><span data-stu-id="52468-117">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="52468-118">Dans cet exemple, la classe `AllowNonSerializableTypesSurrogate` implémente cette interface.</span><span class="sxs-lookup"><span data-stu-id="52468-118">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="52468-119">Dans l’implémentation d’interface, la première tâche consiste à définir un type mappant la classe `Person` à la classe `PersonSurrogated`.</span><span class="sxs-lookup"><span data-stu-id="52468-119">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="52468-120">Ce processus de mappage est utilisé à la fois pendant la sérialisation et l'exportation des schémas.</span><span class="sxs-lookup"><span data-stu-id="52468-120">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="52468-121">Il s'effectue en implémentant la méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29>.</span><span class="sxs-lookup"><span data-stu-id="52468-121">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
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
  
 <span data-ttu-id="52468-122">La méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> mappe une instance de la classe `Person` à une instance de la classe `PersonSurrogated` pendant la sérialisation, tel qu'illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="52468-122">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="52468-123">La méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> permet d’effectuer le mappage dans le sens inverse lors de la désérialisation, tel qu’illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="52468-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="52468-124">Pour mapper le contrat de données `PersonSurrogated` à la classe `Person` existante lors de l'importation des schémas, l'exemple implémente la méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29>, tel qu'illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="52468-124">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="52468-125">L'exemple de code suivant achève l'implémentation de l'interface <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span><span class="sxs-lookup"><span data-stu-id="52468-125">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
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
  
 <span data-ttu-id="52468-126">Dans cet exemple, le substitut est activé dans ServiceModel par un attribut appelé `AllowNonSerializableTypesAttribute`.</span><span class="sxs-lookup"><span data-stu-id="52468-126">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="52468-127">Les développeurs doivent appliquer cet attribut dans leur contrat de service respectif, tel qu'illustré dans le contrat de service `IPersonnelDataService` ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="52468-127">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="52468-128">Cet attribut implémente `IContractBehavior` et définit le substitut sur les opérations dans les méthodes `ApplyClientBehavior` et `ApplyDispatchBehavior`.</span><span class="sxs-lookup"><span data-stu-id="52468-128">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="52468-129">L'attribut n'est pas nécessaire dans ce cas. Il est utilisé à des fins d'illustration dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="52468-129">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="52468-130">Les utilisateurs peuvent également activer un substitut en ajoutant manuellement un `IContractBehavior`, `IEndpointBehavior` ou `IOperationBehavior` similaire à l'aide du code ou de la configuration.</span><span class="sxs-lookup"><span data-stu-id="52468-130">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="52468-131">L'implémentation `IContractBehavior` recherche les opérations qui utilisent DataContract en vérifiant si un comportement `DataContractSerializerOperationBehavior` leur correspondant est enregistré.</span><span class="sxs-lookup"><span data-stu-id="52468-131">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="52468-132">Si tel est le cas, elle définit la propriété `DataContractSurrogate` sur ce comportement.</span><span class="sxs-lookup"><span data-stu-id="52468-132">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="52468-133">L'exemple de code suivant illustre les modalités de ce processus.</span><span class="sxs-lookup"><span data-stu-id="52468-133">The following sample code shows how this is done.</span></span> <span data-ttu-id="52468-134">La définition du substitut sur ce comportement d’opération permet pour ce dernier une sérialisation et une désérialisation.</span><span class="sxs-lookup"><span data-stu-id="52468-134">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
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
  
 <span data-ttu-id="52468-135">D'autres étapes sont nécessaires pour incorporer le substitut et ainsi pouvoir l'utiliser lors de la génération des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="52468-135">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="52468-136">Pour ce faire, l'une des solutions consiste à fournir une extension `IWsdlExportExtension`, tel qu'illustré dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="52468-136">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="52468-137">Une autre solution consiste à modifier directement le `WsdlExporter`.</span><span class="sxs-lookup"><span data-stu-id="52468-137">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="52468-138">L' `AllowNonSerializableTypesAttribute` attribut implémente `IWsdlExportExtension` et `IContractBehavior` .</span><span class="sxs-lookup"><span data-stu-id="52468-138">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="52468-139">L’extension peut être `IContractBehavior` ou `IEndpointBehavior` , dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="52468-139">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="52468-140">Son implémentation de la méthode `IWsdlExportExtension.ExportContract` active le substitut en l'ajoutant au `XsdDataContractExporter` utilisé lors de la génération des schémas du DataContract.</span><span class="sxs-lookup"><span data-stu-id="52468-140">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="52468-141">L'extrait de code suivant montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="52468-141">The following code snippet shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="52468-142">Lorsque vous exécutez l'exemple, le client appelle la méthode AddEmployee, puis la méthode GetEmployee afin de s'assurer que le premier appel a réussi.</span><span class="sxs-lookup"><span data-stu-id="52468-142">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="52468-143">Le résultat de la demande d'opération GetEmployee est affiché dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="52468-143">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="52468-144">L’opération GetEmployee doit parvenir à trouver l’employé et à imprimer « trouvé ».</span><span class="sxs-lookup"><span data-stu-id="52468-144">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52468-145">Cet exemple illustre comment incorporer un substitut à des fins de sérialisation, désérialisation et génération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="52468-145">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="52468-146">Il ne montre pas en revanche comment incorporer un substitut pour permettre la génération de code à partir des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="52468-146">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="52468-147">Pour voir un exemple de la façon dont un substitut peut être utilisé pour se connecter à la génération de code client, consultez l’exemple [publication WSDL personnalisée](custom-wsdl-publication.md) .</span><span class="sxs-lookup"><span data-stu-id="52468-147">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="52468-148">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="52468-148">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="52468-149">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52468-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="52468-150">Pour générer l’édition C# de la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52468-150">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="52468-151">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52468-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="52468-152">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="52468-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="52468-153">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="52468-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="52468-154">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="52468-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="52468-155">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="52468-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
