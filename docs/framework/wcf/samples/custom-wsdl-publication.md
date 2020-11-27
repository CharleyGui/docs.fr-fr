---
title: Publication WSDL personnalisée
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: 83377e1c72ef5774c909729abd1312cce5364ab0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262864"
---
# <a name="custom-wsdl-publication"></a>Publication WSDL personnalisée

Cet exemple montre comment :  
  
- Implémenter une <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> sur un attribut <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> personnalisé pour exporter les propriétés de l'attribut en tant qu'annotations WSDL ;  
  
- Implémenter <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> pour importer les annotations WSDL personnalisées ;  
  
- Implémenter <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> et <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> sur un comportement de contrat personnalisé et un comportement d’opération personnalisé, respectivement, pour écrire des annotations importées en tant que commentaires dans le CodeDom pour le contrat et l’opération importés ;  
  
- Utilisez le <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> pour télécharger le WSDL, un <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> pour importer le WSDL à l’aide de l’importateur WSDL personnalisé, et le <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> pour générer le code client Windows Communication Foundation (WCF) avec les annotations WSDL en tant que commentaires///et' ' 'en C# et Visual Basic.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
## <a name="service"></a>Service  

 Le service dans cet exemple est marqué avec deux attributs personnalisés. Le premier, `WsdlDocumentationAttribute`, accepte une chaîne dans le constructeur et peut être appliqué pour fournir une interface de contrat ou d'opération avec une chaîne qui décrit son utilisation. Le second, `WsdlParamOrReturnDocumentationAttribute`, peut être appliqué aux valeurs ou aux paramètres de retour pour décrire ces valeurs dans l'opération. L'exemple suivant illustre un contrat de service, `ICalculator`, décrit à l'aide de ces attributs.  
  
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
  
 L'`WsdlDocumentationAttribute` implémente <xref:System.ServiceModel.Description.IContractBehavior> et <xref:System.ServiceModel.Description.IOperationBehavior>, donc les instances d'attribut sont ajoutées à la <xref:System.ServiceModel.Description.ContractDescription> correspondante ou à la <xref:System.ServiceModel.Description.OperationDescription> lorsque le service est ouvert. L'attribut implémente également <xref:System.ServiceModel.Description.IWsdlExportExtension>. Lorsque <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> est appelée, le <xref:System.ServiceModel.Description.WsdlExporter> utilisé pour exporter les métadonnées et le <xref:System.ServiceModel.Description.WsdlContractConversionContext> qui contient les objets de description du service sont passés comme des paramètres permettant la modification des métadonnées exportées.  
  
 Dans cet exemple, selon que l’objet de contexte d’exportation a une <xref:System.ServiceModel.Description.ContractDescription> ou une <xref:System.ServiceModel.Description.OperationDescription>, un commentaire est extrait de l’attribut à l’aide de la propriété de texte et est ajouté à l’élément d’annotation WSDL comme le montre le code suivant.  
  
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
  
 Si une opération est en cours d'exportation, l'exemple utilise la réflexion pour obtenir toutes valeurs `WsdlParamOrReturnDocumentationAttribute` pour les paramètres et les valeurs de retour et les ajoute aux éléments d'annotation WSDL pour cette opération comme suit.  
  
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
  
 L'exemple publie ensuite les métadonnées de la manière standard, à l'aide du fichier de configuration suivant.  
  
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
  
## <a name="svcutil-client"></a>Client Svcutil  

 Cet exemple n'utilise pas Svcutil.exe. Le contrat est fourni dans le fichier generatedClient.cs ; ainsi, après que l'exemple a illustré l'importation WSDL personnalisée et la génération de code, le service peut être appelé. Pour utiliser l’importateur WSDL personnalisé suivant pour cet exemple, vous pouvez exécuter Svcutil.exe et spécifier l’option `/svcutilConfig`, pour donner le chemin d’accès au fichier de configuration client utilisé dans cet exemple, qui fait référence à la bibliothèque `WsdlDocumentation.dll`. Pour charger l'`WsdlDocumentationImporter`, toutefois, Svuctil.exe doit être en mesure de localiser et charger la bibliothèque `WsdlDocumentation.dll`, ce qui signifie soit qu'elle est enregistrée dans le Global Assembly Cache, dans le chemin d'accès, soit qu'elle se trouve dans le même répertoire que Svcutil.exe. Pour un exemple de base tel que celui-ci, le plus simple est de copier Svcutil.exe et le fichier de configuration client dans le même répertoire que `WsdlDocumentation.dll` et l'exécuter à partir de là.  
  
## <a name="the-custom-wsdl-importer"></a>L'importateur WSDL personnalisé  

 L'objet <xref:System.ServiceModel.Description.IWsdlImportExtension> personnalisé `WsdlDocumentationImporter` implémente également <xref:System.ServiceModel.Description.IContractBehavior> et <xref:System.ServiceModel.Description.IOperationBehavior> pour être ajouté aux ServiceEndpoints importés et <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> et <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> pour être appelé afin de modifier la génération du code lorsque le code du contrat ou de l'opération est créé.  
  
 En premier lieu, dans la méthode <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29>, l'exemple détermine si l'annotation WSDL se trouve au niveau du contrat ou de l'opération, et s'ajoute lui-même en tant que comportement à l'étendue appropriée, en passant le texte d'annotation importé à son constructeur.  
  
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
  
 Ensuite, lorsque le code est généré, le système appelle les méthodes<xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> et  <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29>, en passant les informations de contexte appropriées. L’exemple met en forme les annotations WSDL personnalisées et les insère comme commentaires dans le CodeDom.  
  
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
  
## <a name="the-client-application"></a>L'application cliente  

 L'application cliente charge l'importateur WSDL personnalisé en le spécifiant dans le fichier de configuration de l'application.  
  
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
  
 Une fois que l’importateur personnalisé a été spécifié, le système de métadonnées WCF charge l’importateur personnalisé dans n’importe quel <xref:System.ServiceModel.Description.WsdlImporter> objet créé à cet effet. Cet exemple utilise le <xref:System.ServiceModel.Description.MetadataExchangeClient> pour télécharger les métadonnées, l'<xref:System.ServiceModel.Description.WsdlImporter> correctement configuré pour importer les métadonnées à l'aide de l'importateur personnalisé que l'exemple crée, et le <xref:System.ServiceModel.Description.ServiceContractGenerator> pour compiler les informations de contrat modifiées à la fois dans le code client Visual Basic et C# qui peut être utilisé dans Visual Studio pour prendre en charge Intellisense ou être compilé dans la documentation XML.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
