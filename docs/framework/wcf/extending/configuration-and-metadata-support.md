---
title: Prise en charge de la configuration et des métadonnées
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: fb4e1cc51b827f083e580362f57df27ced770179
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345294"
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="0235a-102">Prise en charge de la configuration et des métadonnées</span><span class="sxs-lookup"><span data-stu-id="0235a-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="0235a-103">Cette rubrique décrit comment activer la prise en charge de la configuration et des métadonnées pour les liaisons et éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="0235a-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="0235a-104">Vue d'ensemble de la configuration et des métadonnées</span><span class="sxs-lookup"><span data-stu-id="0235a-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="0235a-105">Ce sujet traite des tâches suivantes, qui sont des éléments optionnels 1, 2 et 4 dans la liste [des tâches de Developing Channels.](developing-channels.md)</span><span class="sxs-lookup"><span data-stu-id="0235a-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](developing-channels.md) task list.</span></span>  
  
- <span data-ttu-id="0235a-106">Activation de la prise en charge du fichier de configuration pour un élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="0235a-106">Enabling configuration file support for a binding element.</span></span>  
  
- <span data-ttu-id="0235a-107">Activation de la prise en charge du fichier de configuration pour une liaison.</span><span class="sxs-lookup"><span data-stu-id="0235a-107">Enabling configuration file support for a binding.</span></span>  
  
- <span data-ttu-id="0235a-108">Exportation des assertions WSDL et de stratégie pour un élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="0235a-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
- <span data-ttu-id="0235a-109">Identification des assertions WSDL et de stratégie afin d’insérer et de configurer votre liaison ou élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="0235a-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="0235a-110">Pour plus d’informations sur la création de liaisons définies par l’utilisateur et d’éléments [contraignants, voir créer des liaisons définies par l’utilisateur](creating-user-defined-bindings.md) et [créer un bindingElement](creating-a-bindingelement.md), respectivement.</span><span class="sxs-lookup"><span data-stu-id="0235a-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](creating-user-defined-bindings.md) and [Creating a BindingElement](creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="0235a-111">Ajout de la prise en charge de la configuration</span><span class="sxs-lookup"><span data-stu-id="0235a-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="0235a-112">Pour activer la prise en charge du fichier de configuration pour un canal, vous devez implémenter deux sections de configuration : <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> qui active la prise en charge de la configuration pour les éléments de liaison, et <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> et <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType> qui activent la prise en charge de la configuration pour les liaisons.</span><span class="sxs-lookup"><span data-stu-id="0235a-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="0235a-113">Un moyen plus facile de le faire est d’utiliser l’outil d’échantillon [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) pour générer du code de configuration pour vos liaisons et éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="0235a-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="0235a-114">Extension de BindingElementExtensionElement</span><span class="sxs-lookup"><span data-stu-id="0235a-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="0235a-115">L’exemple suivant est tiré de l’échantillon [Transport: UDP.](../samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="0235a-115">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span> <span data-ttu-id="0235a-116">`UdpTransportElement` est un objet <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> qui expose `UdpTransportBindingElement` au système de configuration.</span><span class="sxs-lookup"><span data-stu-id="0235a-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="0235a-117">Avec quelques substitutions de base, l’exemple définit le nom de section de configuration, le type de l’élément de liaison et la méthode utilisée pour le créer.</span><span class="sxs-lookup"><span data-stu-id="0235a-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="0235a-118">Les utilisateurs peuvent ensuite enregistrer la section d’extension dans un fichier de configuration comme suit.</span><span class="sxs-lookup"><span data-stu-id="0235a-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport" />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="0235a-119">L'extension peut être référencée à partir des liaisons personnalisées pour utiliser UDP comme transport.</span><span class="sxs-lookup"><span data-stu-id="0235a-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="0235a-120">Ajout de la configuration pour une liaison</span><span class="sxs-lookup"><span data-stu-id="0235a-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="0235a-121">La section `SampleProfileUdpBindingCollectionElement` est un <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> qui expose `SampleProfileUdpBinding` au système de configuration.</span><span class="sxs-lookup"><span data-stu-id="0235a-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="0235a-122">Le bloc de l'implémentation est délégué à `SampleProfileUdpBindingConfigurationElement`, qui dérive de <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="0235a-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="0235a-123">Le `SampleProfileUdpBindingConfigurationElement` a des propriétés `SampleProfileUdpBinding`qui correspondent aux propriétés `ConfigurationElement` sur , et fonctionne pour cartographier à partir de la liaison.</span><span class="sxs-lookup"><span data-stu-id="0235a-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="0235a-124">Enfin, la méthode `OnApplyConfiguration` est substituée dans `SampleProfileUdpBinding`, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="0235a-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                var expectedType = typeof(SampleProfileUdpBinding).AssemblyQualifiedName;
                var typePassedIn = binding.GetType().AssemblyQualifiedName;
                throw new ArgumentException($"Invalid type for binding. Expected type: {expectedType}. Type passed in: {typePassedIn}.");  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 <span data-ttu-id="0235a-125">Pour enregistrer ce gestionnaire avec le système de configuration, ajoutez la section suivante au fichier de configuration approprié.</span><span class="sxs-lookup"><span data-stu-id="0235a-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="0235a-126">Il peut ensuite être référencé à partir de la [ \<section de configuration system.serviceModel>.](../../configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0235a-126">It can then be referenced from the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="0235a-127">Ajout de la prise en charge des métadonnées pour un élément de liaison</span><span class="sxs-lookup"><span data-stu-id="0235a-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="0235a-128">Pour intégrer un canal dans le système de métadonnées, il doit à la fois prendre en charge l'importation et l'exportation de stratégie.</span><span class="sxs-lookup"><span data-stu-id="0235a-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="0235a-129">Cela permet à des outils tels que [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) de générer des clients de l’élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="0235a-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="0235a-130">Ajout de la prise en charge WSDL</span><span class="sxs-lookup"><span data-stu-id="0235a-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="0235a-131">L’élément de liaison de transport d’une liaison est chargé d’exporter et d’importer les informations d’adressage dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="0235a-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="0235a-132">Lors de l'utilisation d'une liaison SOAP, l'élément de liaison de transport doit également exporter un URI de transport correct dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="0235a-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="0235a-133">L’exemple suivant est tiré de l’échantillon [Transport: UDP.](../samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="0235a-133">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="0235a-134">Exportation WSDL</span><span class="sxs-lookup"><span data-stu-id="0235a-134">WSDL Export</span></span>  
 <span data-ttu-id="0235a-135">Pour exporter des informations `UdpTransportBindingElement` d’adressant, l’interface implémente. <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="0235a-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="0235a-136">La méthode <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> ajoute les informations d'adressage correctes au port WSDL.</span><span class="sxs-lookup"><span data-stu-id="0235a-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="0235a-137">L’implémentation `UdpTransportBindingElement` de la méthode <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> exporte également un URI de transport lorsque le point de terminaison utilise une liaison SOAP :</span><span class="sxs-lookup"><span data-stu-id="0235a-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="0235a-138">Importation WSDL</span><span class="sxs-lookup"><span data-stu-id="0235a-138">WSDL Import</span></span>  
 <span data-ttu-id="0235a-139">Pour étendre le système d'importation WSDL afin de gérer l'importation des adresses, ajoutez la configuration suivante au fichier de configuration de Svcutil.exe, tel qu'indiqué dans le fichier Svcutil.exe.config :</span><span class="sxs-lookup"><span data-stu-id="0235a-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </wsdlImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="0235a-140">Lorsque vous exécutez Svcutil.exe, deux méthodes permettent de faire en sorte que Svcutil.exe charge les extensions d’importation WSDL :</span><span class="sxs-lookup"><span data-stu-id="0235a-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="0235a-141">Point Svcutil.exe au fichier de configuration à l’aide\<du /SvcutilConfig: fichier>.</span><span class="sxs-lookup"><span data-stu-id="0235a-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="0235a-142">Ajoutez la section de configuration à Svcutil.exe.config dans le répertoire où se trouve Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="0235a-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="0235a-143">Le type `UdpBindingElementImporter` implémente l'interface <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0235a-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="0235a-144">La méthode `ImportEndpoint` importe l'adresse à partir du port WSDL :</span><span class="sxs-lookup"><span data-stu-id="0235a-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="0235a-145">Ajout de la prise en charge de la stratégie</span><span class="sxs-lookup"><span data-stu-id="0235a-145">Adding Policy Support</span></span>  
 <span data-ttu-id="0235a-146">L’élément de liaison personnalisé peut exporter des assertions de stratégie dans la liaison WSDL d’un point de terminaison de service pour exprimer les fonctionnalités de cet élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="0235a-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="0235a-147">L’exemple suivant est tiré de l’échantillon [Transport: UDP.](../samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="0235a-147">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="0235a-148">Exportation de stratégie</span><span class="sxs-lookup"><span data-stu-id="0235a-148">Policy Export</span></span>  
 <span data-ttu-id="0235a-149">Le `UdpTransportBindingElement` type <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> met en œuvre pour renforcer la politique d’exportation.</span><span class="sxs-lookup"><span data-stu-id="0235a-149">The `UdpTransportBindingElement` type implements <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="0235a-150">En conséquence, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> inclut `UdpTransportBindingElement` dans la génération de stratégie des liaisons qui l’incluent.</span><span class="sxs-lookup"><span data-stu-id="0235a-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="0235a-151">Dans <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, ajoutez une assertion pour UDP et une autre si le canal est en mode multicast.</span><span class="sxs-lookup"><span data-stu-id="0235a-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="0235a-152">Cela est dû au fait que le mode multicast affecte la manière dont la pile est construite, et doit donc être coordonné entre les deux côtés.</span><span class="sxs-lookup"><span data-stu-id="0235a-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp  
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.MulticastAssertion,     UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="0235a-153">Les éléments de liaison de transport personnalisés étant chargés de gérer l’adressage, l’implémentation <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> sur `UdpTransportBindingElement` doit également gérer l’exportation des assertions de stratégie WS-Addressing appropriées pour indiquer la version de WS-Addressing utilisée.</span><span class="sxs-lookup"><span data-stu-id="0235a-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="0235a-154">Importation de stratégie</span><span class="sxs-lookup"><span data-stu-id="0235a-154">Policy Import</span></span>  
 <span data-ttu-id="0235a-155">Pour étendre le système d'importation de stratégie, ajoutez la configuration suivante au fichier de configuration de Svcutil.exe, tel qu'indiqué dans le fichier Svcutil.exe.config :</span><span class="sxs-lookup"><span data-stu-id="0235a-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="0235a-156">Puis nous implémentons <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> à partir de la classe enregistrée (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="0235a-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="0235a-157">Dans <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examinez les assertions dans l'espace de noms approprié et traitez celles permettant de générer le transport et de vérifier s'il est multicast.</span><span class="sxs-lookup"><span data-stu-id="0235a-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="0235a-158">En outre, supprimez les assertions gérées par l'importateur de la liste des assertions de liaison.</span><span class="sxs-lookup"><span data-stu-id="0235a-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="0235a-159">Une fois encore, il existe deux méthodes d'intégration possibles lorsque vous exécutez Svcutil.exe :</span><span class="sxs-lookup"><span data-stu-id="0235a-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="0235a-160">Point Svcutil.exe à notre fichier de configuration à l’aide de la /SvcutilConfig:\<fichier>.</span><span class="sxs-lookup"><span data-stu-id="0235a-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="0235a-161">Ajoutez la section de configuration à Svcutil.exe.config dans le répertoire où se trouve Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="0235a-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="0235a-162">Ajout d'un importateur de liaison standard personnalisé</span><span class="sxs-lookup"><span data-stu-id="0235a-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="0235a-163">Par défaut, Svcutil.exe et le type <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> reconnaissent et importent les liaisons fournies par le système.</span><span class="sxs-lookup"><span data-stu-id="0235a-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="0235a-164">Sinon, la liaison est importée en tant qu'instance <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0235a-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="0235a-165">Pour permettre à Svcutil.exe et <xref:System.ServiceModel.Description.WsdlImporter> d’importer `SampleProfileUdpBinding`, `UdpBindingElementImporter` agit également comme un importateur de liaison standard personnalisé.</span><span class="sxs-lookup"><span data-stu-id="0235a-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="0235a-166">Un importateur de liaison `ImportEndpoint` standard personnalisé <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> implémente la méthode de l’interface pour examiner l’instance <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> importée des métadonnées pour voir si elle aurait pu être générée par une liaison standard spécifique.</span><span class="sxs-lookup"><span data-stu-id="0235a-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
```csharp  
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="0235a-167">En général, l’implémentation d’un importateur de liaison standard personnalisé implique la vérification des propriétés des éléments de liaison importés afin de s’assurer que seules les propriétés pouvant avoir été définies par la liaison standard ont été modifiées et que toutes les autres ont été définies à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="0235a-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="0235a-168">L’une des stratégies de base permettant d’implémenter un importateur de liaison standard consiste à créer une instance de la liaison standard, à propager les propriétés des éléments de liaison vers l’instance de liaison standard que la liaison standard prend en charge, et à comparer les éléments de liaison de la liaison standard avec les éléments de liaison importés.</span><span class="sxs-lookup"><span data-stu-id="0235a-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
