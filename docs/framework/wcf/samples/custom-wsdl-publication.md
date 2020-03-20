---
title: Publication WSDL personnalisée
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: ae6d5fdf243d5000090e993bd3353c6180d0ccaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145057"
---
# <a name="custom-wsdl-publication"></a><span data-ttu-id="e3ad0-102">Publication WSDL personnalisée</span><span class="sxs-lookup"><span data-stu-id="e3ad0-102">Custom WSDL Publication</span></span>
<span data-ttu-id="e3ad0-103">Cet exemple montre comment :</span><span class="sxs-lookup"><span data-stu-id="e3ad0-103">This sample demonstrates how to:</span></span>  
  
- <span data-ttu-id="e3ad0-104">Implémenter une <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> sur un attribut <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> personnalisé pour exporter les propriétés de l'attribut en tant qu'annotations WSDL ;</span><span class="sxs-lookup"><span data-stu-id="e3ad0-104">Implement a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> on a custom <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> attribute to export attribute properties as WSDL annotations.</span></span>  
  
- <span data-ttu-id="e3ad0-105">Implémenter <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> pour importer les annotations WSDL personnalisées ;</span><span class="sxs-lookup"><span data-stu-id="e3ad0-105">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> to import the custom WSDL annotations.</span></span>  
  
- <span data-ttu-id="e3ad0-106">Implémenter <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> et <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> sur un comportement de contrat personnalisé et un comportement d’opération personnalisé, respectivement, pour écrire des annotations importées en tant que commentaires dans le CodeDom pour le contrat et l’opération importés ;</span><span class="sxs-lookup"><span data-stu-id="e3ad0-106">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> on a custom contract behavior and a custom operation behavior, respectively, to write imported annotations as comments in the CodeDom for the imported contract and operation.</span></span>  
  
- <span data-ttu-id="e3ad0-107">Utilisez <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> le téléchargement de la <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> WSDL, un pour importer le WSDL <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> en utilisant l’importateur personnalisé WSDL, et le pour générer Windows Communication Foundation (WCF) code client avec les annotations WSDL comme // et «» commentaires dans C et Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-107">Use the <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> to download the WSDL, a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> to import the WSDL using the custom WSDL importer, and the <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> to generate Windows Communication Foundation (WCF) client code with the WSDL annotations as /// and ''' comments in C# and Visual Basic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3ad0-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="e3ad0-109">Service</span><span class="sxs-lookup"><span data-stu-id="e3ad0-109">Service</span></span>  
 <span data-ttu-id="e3ad0-110">Le service dans cet exemple est marqué avec deux attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-110">The service in this sample is marked with two custom attributes.</span></span> <span data-ttu-id="e3ad0-111">Le premier, `WsdlDocumentationAttribute`, accepte une chaîne dans le constructeur et peut être appliqué pour fournir une interface de contrat ou d'opération avec une chaîne qui décrit son utilisation.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-111">The first, the `WsdlDocumentationAttribute`, accepts a string in the constructor and can be applied to provide a contract interface or operation with a string that describes its usage.</span></span> <span data-ttu-id="e3ad0-112">Le second, `WsdlParamOrReturnDocumentationAttribute`, peut être appliqué aux valeurs ou aux paramètres de retour pour décrire ces valeurs dans l'opération.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-112">The second, `WsdlParamOrReturnDocumentationAttribute`, can be applied to return values or parameters to describe those values in the operation.</span></span> <span data-ttu-id="e3ad0-113">L'exemple suivant illustre un contrat de service, `ICalculator`, décrit à l'aide de ces attributs.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-113">The following example shows a service contract, `ICalculator`, described using these attributes.</span></span>  
  
```csharp  
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
// Document it.  
[WsdlDocumentation("The ICalculator contract performs basic calculation services.")]  
public interface ICalculator  
{  
    [OperationContract]  
    [WsdlDocumentation("The Add operation adds two numbers and returns the result.")]  
    [return:WsdlParamOrReturnDocumentation("The result of adding the two arguments together.")]  
    double Add(  
      [WsdlParamOrReturnDocumentation("The first value to add.")]double n1,
      [WsdlParamOrReturnDocumentation("The second value to add.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Subtract operation subtracts the second argument from the first.")]  
    [return:WsdlParamOrReturnDocumentation("The result of the second argument subtracted from the first.")]  
    double Subtract(  
      [WsdlParamOrReturnDocumentation("The value from which the second is subtracted.")]double n1,
      [WsdlParamOrReturnDocumentation("The value that is subtracted from the first.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Multiply operation multiplies two values.")]  
    [return:WsdlParamOrReturnDocumentation("The result of multiplying the first and second arguments.")]  
    double Multiply(  
      [WsdlParamOrReturnDocumentation("The first value to multiply.")]double n1,
      [WsdlParamOrReturnDocumentation("The second value to multiply.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Divide operation returns the value of the first argument divided by the second argument.")]  
    [return:WsdlParamOrReturnDocumentation("The result of dividing the first argument by the second.")]  
    double Divide(  
      [WsdlParamOrReturnDocumentation("The numerator.")]double n1,
      [WsdlParamOrReturnDocumentation("The denominator.")]double n2  
    );  
}  
```  
  
 <span data-ttu-id="e3ad0-114">L'`WsdlDocumentationAttribute` implémente <xref:System.ServiceModel.Description.IContractBehavior> et <xref:System.ServiceModel.Description.IOperationBehavior>, donc les instances d'attribut sont ajoutées à la <xref:System.ServiceModel.Description.ContractDescription> correspondante ou à la <xref:System.ServiceModel.Description.OperationDescription> lorsque le service est ouvert.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-114">The `WsdlDocumentationAttribute` implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior>, so the attribute instances are added to the corresponding <xref:System.ServiceModel.Description.ContractDescription> or <xref:System.ServiceModel.Description.OperationDescription> when the service is opened.</span></span> <span data-ttu-id="e3ad0-115">L'attribut implémente également <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-115">The attribute also implements <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span></span> <span data-ttu-id="e3ad0-116">Lorsque <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> est appelée, le <xref:System.ServiceModel.Description.WsdlExporter> utilisé pour exporter les métadonnées et le <xref:System.ServiceModel.Description.WsdlContractConversionContext> qui contient les objets de description du service sont passés comme des paramètres permettant la modification des métadonnées exportées.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-116">When <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> is called, the <xref:System.ServiceModel.Description.WsdlExporter> that is used to export the metadata and the <xref:System.ServiceModel.Description.WsdlContractConversionContext> that contains the service description objects are passed in as parameters enabling the modification of the exported metadata.</span></span>  
  
 <span data-ttu-id="e3ad0-117">Dans cet exemple, selon que l’objet de contexte d’exportation a une <xref:System.ServiceModel.Description.ContractDescription> ou une <xref:System.ServiceModel.Description.OperationDescription>, un commentaire est extrait de l’attribut à l’aide de la propriété de texte et est ajouté à l’élément d’annotation WSDL comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-117">In this sample, depending upon whether the export context object has a <xref:System.ServiceModel.Description.ContractDescription> or an <xref:System.ServiceModel.Description.OperationDescription>, a comment is extracted from the attribute using the text property and is added to the WSDL annotation element as shown in the following code.</span></span>  
  
```csharp
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)
{
    if (contractDescription != null)
    {
        // Inside this block it is the contract-level comment attribute.
        // This.Text returns the string for the contract attribute.
        // Set the doc element; if this isn't done first, there is no XmlElement in the
        // DocumentElement property.
        context.WsdlPortType.Documentation = string.Empty;
        // Contract comments.
        XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;
        XmlElement summaryElement = owner.CreateElement("summary");
        summaryElement.InnerText = this.Text;
        context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);
    }
    else
    {
        Operation operation = context.GetOperation(operationDescription);
        if (operation != null)
        {
            // We are dealing strictly with the operation here.
            // This.Text returns the string for the operation-level attributes.
            // Set the doc element; if this isn't done first, there is no XmlElement in the
            // DocumentElement property.
            operation.Documentation = String.Empty;

            // Operation C# triple comments.
            XmlDocument owner = operation.DocumentationElement.OwnerDocument;
            XmlElement newSummaryElement = owner.CreateElement("summary");
            newSummaryElement.InnerText = this.Text;
            operation.DocumentationElement.AppendChild(newSummaryElement);
        }
    }
}
```  
  
 <span data-ttu-id="e3ad0-118">Si une opération est en cours d'exportation, l'exemple utilise la réflexion pour obtenir toutes valeurs `WsdlParamOrReturnDocumentationAttribute` pour les paramètres et les valeurs de retour et les ajoute aux éléments d'annotation WSDL pour cette opération comme suit.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-118">If an operation is being exported, the sample uses reflection to obtain any `WsdlParamOrReturnDocumentationAttribute` values for parameters and return values and adds them to the WSDL annotation elements for that operation as follows.</span></span>  
  
```csharp
// Get returns information  
ParameterInfo returnValue = operationDescription.SyncMethod.ReturnParameter;  
object[] returnAttrs = returnValue.GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
if (returnAttrs.Length != 0)  
{  
    // <returns>text.</returns>  
    XmlElement returnsElement = owner.CreateElement("returns");  
    returnsElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)returnAttrs[0]).ParamComment;  
    operation.DocumentationElement.AppendChild(returnsElement);  
}  
  
// Get parameter information.  
ParameterInfo[] args = operationDescription.SyncMethod.GetParameters();  
for (int i = 0; i < args.Length; i++)  
{  
    object[] docAttrs = args[i].GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
    if (docAttrs.Length == 1)  
    {  
        // <param name="Int1">Text.</param>  
        XmlElement newParamElement = owner.CreateElement("param");  
        XmlAttribute paramName = owner.CreateAttribute("name");  
        paramName.Value = args[i].Name;  
        newParamElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)docAttrs[0]).ParamComment;  
        newParamElement.Attributes.Append(paramName);  
        operation.DocumentationElement.AppendChild(newParamElement);  
    }  
}  
```  
  
 <span data-ttu-id="e3ad0-119">L'exemple publie ensuite les métadonnées de la manière standard, à l'aide du fichier de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-119">The sample then publishes metadata in the standard way, using the following configuration file.</span></span>  
  
```xml  
<services>  
  <service
      name="Microsoft.ServiceModel.Samples.CalculatorService"  
      behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- ICalculator is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    <!-- the mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
    <endpoint address="mex"  
              binding="mexHttpBinding"  
              contract="IMetadataExchange" />  
  </service>  
</services>  
  
<!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="svcutil-client"></a><span data-ttu-id="e3ad0-120">Client Svcutil</span><span class="sxs-lookup"><span data-stu-id="e3ad0-120">Svcutil client</span></span>  
 <span data-ttu-id="e3ad0-121">Cet exemple n'utilise pas Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-121">This sample does not use Svcutil.exe.</span></span> <span data-ttu-id="e3ad0-122">Le contrat est fourni dans le fichier generatedClient.cs ; ainsi, après que l'exemple a illustré l'importation WSDL personnalisée et la génération de code, le service peut être appelé.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-122">The contract is provided in the generatedClient.cs file so that after the sample demonstrates custom WSDL import and code generation, the service can be invoked.</span></span> <span data-ttu-id="e3ad0-123">Pour utiliser l’importateur WSDL personnalisé suivant pour cet exemple, vous pouvez exécuter Svcutil.exe et spécifier l’option `/svcutilConfig`, pour donner le chemin d’accès au fichier de configuration client utilisé dans cet exemple, qui fait référence à la bibliothèque `WsdlDocumentation.dll`.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-123">To use the following custom WSDL importer for this example, you can run Svcutil.exe and specify the `/svcutilConfig` option, giving the path to the client configuration file used in this sample, which references the `WsdlDocumentation.dll` library.</span></span> <span data-ttu-id="e3ad0-124">Pour charger l'`WsdlDocumentationImporter`, toutefois, Svuctil.exe doit être en mesure de localiser et charger la bibliothèque `WsdlDocumentation.dll`, ce qui signifie soit qu'elle est enregistrée dans le Global Assembly Cache, dans le chemin d'accès, soit qu'elle se trouve dans le même répertoire que Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-124">To load the `WsdlDocumentationImporter`, however, Svuctil.exe must be able to locate and load the `WsdlDocumentation.dll` library, which means either that it is registered in the global assembly cache, in the path, or is in the same directory as Svcutil.exe.</span></span> <span data-ttu-id="e3ad0-125">Pour un exemple de base tel que celui-ci, le plus simple est de copier Svcutil.exe et le fichier de configuration client dans le même répertoire que `WsdlDocumentation.dll` et l'exécuter à partir de là.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-125">For a basic sample such as this, the easiest thing to do is to copy Svcutil.exe and the client configuration file into the same directory as `WsdlDocumentation.dll` and run it from there.</span></span>  
  
## <a name="the-custom-wsdl-importer"></a><span data-ttu-id="e3ad0-126">L'importateur WSDL personnalisé</span><span class="sxs-lookup"><span data-stu-id="e3ad0-126">The Custom WSDL Importer</span></span>  
 <span data-ttu-id="e3ad0-127">L'objet <xref:System.ServiceModel.Description.IWsdlImportExtension> personnalisé `WsdlDocumentationImporter` implémente également <xref:System.ServiceModel.Description.IContractBehavior> et <xref:System.ServiceModel.Description.IOperationBehavior> pour être ajouté aux ServiceEndpoints importés et <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> et <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> pour être appelé afin de modifier la génération du code lorsque le code du contrat ou de l'opération est créé.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-127">The custom <xref:System.ServiceModel.Description.IWsdlImportExtension> object `WsdlDocumentationImporter` also implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior> to be added to the imported ServiceEndpoints and <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> to be invoked to modify the code generation when the contract or operation code is being created.</span></span>  
  
 <span data-ttu-id="e3ad0-128">En premier lieu, dans la méthode <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29>, l'exemple détermine si l'annotation WSDL se trouve au niveau du contrat ou de l'opération, et s'ajoute lui-même en tant que comportement à l'étendue appropriée, en passant le texte d'annotation importé à son constructeur.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-128">First, in the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method, the sample determines whether the WSDL annotation is at the contract or operation level, and adds itself as a behavior at the appropriate scope, passing the imported annotation text to its constructor.</span></span>  
  
```csharp
public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
{  
    // Contract Documentation  
    if (context.WsdlPortType.Documentation != null)  
    {  
        // System examines the contract behaviors to see whether any implement IWsdlImportExtension.  
        context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
    }  
    // Operation Documentation  
    foreach (Operation operation in context.WsdlPortType.Operations)  
    {  
        if (operation.Documentation != null)  
        {  
            OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
            if (operationDescription != null)  
            {  
                // System examines the operation behaviors to see whether any implement IWsdlImportExtension.  
                operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="e3ad0-129">Ensuite, lorsque le code est généré, le système appelle les méthodes<xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> et  <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29>, en passant les informations de contexte appropriées.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-129">Then, when the code is generated, the system invokes the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> methods, passing the appropriate context information.</span></span> <span data-ttu-id="e3ad0-130">L’exemple met en forme les annotations WSDL personnalisées et les insère comme commentaires dans le CodeDom.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-130">The sample formats the custom WSDL annotations and inserts them as comments into the CodeDom.</span></span>  
  
```csharp
public void GenerateContract(ServiceContractGenerationContext context)  
{  
    Debug.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(FormatComments(text));  
}  
  
public void GenerateOperation(OperationContractGenerationContext context)  
{  
    context.SyncMethod.Comments.AddRange(FormatComments(text));  
    Debug.WriteLine("In generate operation.");  
}  
```  
  
## <a name="the-client-application"></a><span data-ttu-id="e3ad0-131">L'application cliente</span><span class="sxs-lookup"><span data-stu-id="e3ad0-131">The Client Application</span></span>  
 <span data-ttu-id="e3ad0-132">L'application cliente charge l'importateur WSDL personnalisé en le spécifiant dans le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-132">The client application loads the custom WSDL importer by specifying it in the application configuration file.</span></span>  
  
```xml  
<client>  
  <endpoint address="http://localhost/servicemodelsamples/service.svc"
  binding="wsHttpBinding"
  contract="ICalculator" />  
  <metadata>  
    <wsdlImporters>  
      <extension type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
    </wsdlImporters>  
  </metadata>  
</client>  
```  
  
 <span data-ttu-id="e3ad0-133">Une fois que l’importateur personnalisé a été spécifié, le système <xref:System.ServiceModel.Description.WsdlImporter> de métadonnées WCF charge l’importateur personnalisé dans n’importe quel créé à cette fin.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-133">Once the custom importer has been specified, the WCF metadata system loads the custom importer into any <xref:System.ServiceModel.Description.WsdlImporter> created for that purpose.</span></span> <span data-ttu-id="e3ad0-134">Cet exemple utilise le <xref:System.ServiceModel.Description.MetadataExchangeClient> pour télécharger les métadonnées, l'<xref:System.ServiceModel.Description.WsdlImporter> correctement configuré pour importer les métadonnées à l'aide de l'importateur personnalisé que l'exemple crée, et le <xref:System.ServiceModel.Description.ServiceContractGenerator> pour compiler les informations de contrat modifiées à la fois dans le code client Visual Basic et C# qui peut être utilisé dans Visual Studio pour prendre en charge Intellisense ou être compilé dans la documentation XML.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-134">This sample uses the <xref:System.ServiceModel.Description.MetadataExchangeClient> to download the metadata, the <xref:System.ServiceModel.Description.WsdlImporter> properly configured to import the metadata using the custom importer the sample creates, and the <xref:System.ServiceModel.Description.ServiceContractGenerator> to compile the modified contract information into both Visual Basic and C# client code that can be used in Visual Studio to support Intellisense or compiled into XML documentation.</span></span>  
  
```csharp
/// From WSDL Documentation:  
///
/// <summary>The ICalculator contract performs basic calculation
/// services.</summary>
///
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.ServiceModel.Samples", ConfigurationName="ICalculator")]  
public interface ICalculator  
{  
  
    /// From WSDL Documentation:  
    ///
    /// <summary>The Add operation adds two numbers and returns the
    /// result.</summary><returns>The result of adding the two arguments
    /// together.</returns><param name="n1">The first value to add.</param><param
    /// name="n2">The second value to add.</param>
    ///
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Add", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/AddResponse")]  
    double Add(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///
    /// <summary>The Subtract operation subtracts the second argument from the
    /// first.</summary><returns>The result of the second argument subtracted from the
    /// first.</returns><param name="n1">The value from which the second is
    /// subtracted.</param><param name="n2">The value that is subtracted from the
    /// first.</param>
    ///
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Subtract", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/SubtractResponse")]  
    double Subtract(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///
    /// <summary>The Multiply operation multiplies two values.</summary><returns>The
    /// result of multiplying the first and second arguments.</returns><param
    /// name="n1">The first value to multiply.</param><param name="n2">The second value
    /// to multiply.</param>
    ///
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Multiply", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/MultiplyResponse")]  
    double Multiply(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///
    /// <summary>The Divide operation returns the value of the first argument divided
    /// by the second argument.</summary><returns>The result of dividing the first
    /// argument by the second.</returns><param name="n1">The numerator.</param><param
    /// name="n2">The denominator.</param>
    ///
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Divide", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/DivideResponse")]  
    double Divide(double n1, double n2);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e3ad0-135">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="e3ad0-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e3ad0-136">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)</span><span class="sxs-lookup"><span data-stu-id="e3ad0-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e3ad0-137">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e3ad0-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e3ad0-138">Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e3ad0-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e3ad0-139">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e3ad0-140">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-140">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e3ad0-141">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e3ad0-142">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="e3ad0-142">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
