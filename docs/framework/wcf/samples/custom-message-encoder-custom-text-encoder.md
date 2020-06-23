---
title: 'Encodeur de message personnalisé : Encodeur de texte personnalisé'
description: Utilisez cet exemple pour implémenter un encodeur de message texte personnalisé à l’aide de WCF. Cet encodeur prend en charge tous les encodages de caractères pris en charge par la plateforme pour l’interopérabilité.
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 88ddc79e6cc1df654aea851cedb0e60c6fbcd017
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246270"
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="aa844-104">Encodeur de message personnalisé : Encodeur de texte personnalisé</span><span class="sxs-lookup"><span data-stu-id="aa844-104">Custom Message Encoder: Custom Text Encoder</span></span>

<span data-ttu-id="aa844-105">Cet exemple montre comment implémenter un encodeur de message texte personnalisé à l’aide de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="aa844-105">This sample demonstrates how to implement a custom text message encoder using Windows Communication Foundation (WCF).</span></span>

> [!WARNING]
> <span data-ttu-id="aa844-106">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aa844-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="aa844-107">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="aa844-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="aa844-108">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="aa844-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aa844-109">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="aa844-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

<span data-ttu-id="aa844-110">Le <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> de WCF prend en charge uniquement les encodages Unicode UTF-8, UTF-16 et Big-endian.</span><span class="sxs-lookup"><span data-stu-id="aa844-110">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF supports only the UTF-8, UTF-16 and big-endian Unicode encodings.</span></span> <span data-ttu-id="aa844-111">Dans cet exemple, l’encodeur de message texte personnalisé prend en charge tous les encodages de caractères pris en charge par la plateforme qui peuvent être nécessaires pour l’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="aa844-111">The custom text message encoder in this sample supports all platform-supported character encodings that may be required for interoperability.</span></span> <span data-ttu-id="aa844-112">L’exemple se compose d’un programme de console client (. exe), d’une bibliothèque de service (. dll) hébergée par Internet Information Services (IIS) et d’une bibliothèque de codeur de message texte (. dll).</span><span class="sxs-lookup"><span data-stu-id="aa844-112">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS), and a text message encoder library (.dll).</span></span> <span data-ttu-id="aa844-113">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="aa844-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="aa844-114">Le contrat est défini par l'interface `ICalculator`, laquelle expose les opérations mathématiques suivantes : addition, soustraction, multiplication et division.</span><span class="sxs-lookup"><span data-stu-id="aa844-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="aa844-115">Le client adresse des demandes synchrones à une opération mathématique donnée et le service répond avec le résultat.</span><span class="sxs-lookup"><span data-stu-id="aa844-115">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="aa844-116">Le client et le service utilisent `CustomTextMessageEncoder` au lieu du <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> par défaut.</span><span class="sxs-lookup"><span data-stu-id="aa844-116">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>

<span data-ttu-id="aa844-117">L’implémentation d’encodeur personnalisée se compose d’une fabrique d’encodeur de message, d’un encodeur de message, d’un élément de liaison d’encodage de message et d’un gestionnaire de configuration, et présente les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="aa844-117">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>

- <span data-ttu-id="aa844-118">Création d'un encodeur personnalisé et d'une fabrique d'encodeur.</span><span class="sxs-lookup"><span data-stu-id="aa844-118">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="aa844-119">Création d’un élément de liaison pour un encodeur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="aa844-119">Creating a binding element for a custom encoder.</span></span>

- <span data-ttu-id="aa844-120">Utilisation de la configuration de liaison personnalisée permettant d’intégrer des éléments de liaison personnalisés.</span><span class="sxs-lookup"><span data-stu-id="aa844-120">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="aa844-121">Développement d’un gestionnaire de configuration personnalisé afin de permettre la configuration de fichier d’un élément de liaison personnalisé.</span><span class="sxs-lookup"><span data-stu-id="aa844-121">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="aa844-122">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="aa844-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="aa844-123">Installez ASP.NET 4,0 à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="aa844-123">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="aa844-124">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa844-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="aa844-125">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa844-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="aa844-126">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa844-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="aa844-127">Fabrique d'encodeur de message et encodeur de message</span><span class="sxs-lookup"><span data-stu-id="aa844-127">Message Encoder Factory and the Message Encoder</span></span>

<span data-ttu-id="aa844-128">Lorsque <xref:System.ServiceModel.ServiceHost> ou le canal client est ouvert, le composant au moment du design `CustomTextMessageBindingElement` crée `CustomTextMessageEncoderFactory`.</span><span class="sxs-lookup"><span data-stu-id="aa844-128">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="aa844-129">La fabrique crée `CustomTextMessageEncoder`.</span><span class="sxs-lookup"><span data-stu-id="aa844-129">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="aa844-130">L'encodeur de message fonctionne à la fois en mode de diffusion en continu et en mode de mise en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="aa844-130">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="aa844-131">Il utilise <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter> pour respectivement lire et écrire les messages.</span><span class="sxs-lookup"><span data-stu-id="aa844-131">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="aa844-132">Contrairement aux lecteurs et aux Writers XML optimisés de WCF qui ne prennent en charge que les enregistreurs Unicode UTF-8, UTF-16 et Big-endian, ces lecteurs et enregistreurs prennent en charge tous les encodages pris en charge par la plateforme.</span><span class="sxs-lookup"><span data-stu-id="aa844-132">As opposed to the optimized XML readers and writers of WCF that support only UTF-8, UTF-16 and big-endian Unicode, these readers and writers support all platform-supported encoding.</span></span>

<span data-ttu-id="aa844-133">L'exemple de code suivant présente CustomTextMessageEncoder.</span><span class="sxs-lookup"><span data-stu-id="aa844-133">The following code example shows the CustomTextMessageEncoder.</span></span>

```csharp
public class CustomTextMessageEncoder : MessageEncoder
{
    private CustomTextMessageEncoderFactory factory;
    private XmlWriterSettings writerSettings;
    private string contentType;

    public CustomTextMessageEncoder(CustomTextMessageEncoderFactory factory)
    {
        this.factory = factory;

        this.writerSettings = new XmlWriterSettings();
        this.writerSettings.Encoding = Encoding.GetEncoding(factory.CharSet);
        this.contentType = $"{this.factory.MediaType}; charset={this.writerSettings.Encoding.HeaderName}";
    }

    public override string ContentType
    {
        get
        {
            return this.contentType;
        }
    }

    public override string MediaType
    {
        get
        {
            return factory.MediaType;
        }
    }

    public override MessageVersion MessageVersion
    {
        get
        {
            return this.factory.MessageVersion;
        }
    }

    public override Message ReadMessage(ArraySegment<byte> buffer, BufferManager bufferManager, string contentType)
    {
        byte[] msgContents = new byte[buffer.Count];
        Array.Copy(buffer.Array, buffer.Offset, msgContents, 0, msgContents.Length);
        bufferManager.ReturnBuffer(buffer.Array);

        MemoryStream stream = new MemoryStream(msgContents);
        return ReadMessage(stream, int.MaxValue);
    }

    public override Message ReadMessage(Stream stream, int maxSizeOfHeaders, string contentType)
    {
        XmlReader reader = XmlReader.Create(stream);
        return Message.CreateMessage(reader, maxSizeOfHeaders, this.MessageVersion);
    }

    public override ArraySegment<byte> WriteMessage(Message message, int maxMessageSize, BufferManager bufferManager, int messageOffset)
    {
        MemoryStream stream = new MemoryStream();
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);
        message.WriteMessage(writer);
        writer.Close();

        byte[] messageBytes = stream.GetBuffer();
        int messageLength = (int)stream.Position;
        stream.Close();

        int totalLength = messageLength + messageOffset;
        byte[] totalBytes = bufferManager.TakeBuffer(totalLength);
        Array.Copy(messageBytes, 0, totalBytes, messageOffset, messageLength);

        ArraySegment<byte> byteArray = new ArraySegment<byte>(totalBytes, messageOffset, messageLength);
        return byteArray;
    }

    public override void WriteMessage(Message message, Stream stream)
    {
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);
        message.WriteMessage(writer);
        writer.Close();
    }
}
```

<span data-ttu-id="aa844-134">L'exemple de code suivant montre comment créer la fabrique d'encodeur de message.</span><span class="sxs-lookup"><span data-stu-id="aa844-134">The following code example shows how to build the message encoder factory.</span></span>

```csharp
public class CustomTextMessageEncoderFactory : MessageEncoderFactory
{
    private MessageEncoder encoder;
    private MessageVersion version;
    private string mediaType;
    private string charSet;

    internal CustomTextMessageEncoderFactory(string mediaType, string charSet,
        MessageVersion version)
    {
        this.version = version;
        this.mediaType = mediaType;
        this.charSet = charSet;
        this.encoder = new CustomTextMessageEncoder(this);
    }

    public override MessageEncoder Encoder
    {
        get
        {
            return this.encoder;
        }
    }

    public override MessageVersion MessageVersion
    {
        get
        {
            return this.version;
        }
    }

    internal string MediaType
    {
        get
        {
            return this.mediaType;
        }
    }

    internal string CharSet
    {
        get
        {
            return this.charSet;
        }
    }
}
```

## <a name="message-encoding-binding-element"></a><span data-ttu-id="aa844-135">Élément de liaison d'encodage de message</span><span class="sxs-lookup"><span data-stu-id="aa844-135">Message Encoding Binding Element</span></span>

<span data-ttu-id="aa844-136">Les éléments de liaison autorisent la configuration de la pile Runtime WCF.</span><span class="sxs-lookup"><span data-stu-id="aa844-136">The binding elements allow the configuration of the WCF run-time stack.</span></span> <span data-ttu-id="aa844-137">Pour utiliser l’encodeur de message personnalisé dans une application WCF, vous devez disposer d’un élément de liaison qui crée la fabrique d’encodeur de message avec les paramètres appropriés au niveau approprié dans la pile Runtime.</span><span class="sxs-lookup"><span data-stu-id="aa844-137">To use the custom message encoder in a WCF application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>

<span data-ttu-id="aa844-138">`CustomTextMessageBindingElement` dérive de la classe de base <xref:System.ServiceModel.Channels.BindingElement> et hérite de la classe <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="aa844-138">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="aa844-139">Cela permet à d’autres composants WCF de reconnaître cet élément de liaison comme étant un élément de liaison d’encodage de message.</span><span class="sxs-lookup"><span data-stu-id="aa844-139">This allows other WCF components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="aa844-140">L'implémentation de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> retourne une instance de la fabrique d'encodeur de message correspondante avec les paramètres appropriés.</span><span class="sxs-lookup"><span data-stu-id="aa844-140">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>

<span data-ttu-id="aa844-141">`CustomTextMessageBindingElement` expose des paramètres pour `MessageVersion`, `ContentType` et `Encoding` via des propriétés.</span><span class="sxs-lookup"><span data-stu-id="aa844-141">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="aa844-142">L'encodeur prend en charge les versions Soap11Addressing et Soap12Addressing1.</span><span class="sxs-lookup"><span data-stu-id="aa844-142">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="aa844-143">La valeur par défaut est Soap11Addressing1.</span><span class="sxs-lookup"><span data-stu-id="aa844-143">The default is Soap11Addressing1.</span></span> <span data-ttu-id="aa844-144">La valeur par défaut de `ContentType` est "text/xml".</span><span class="sxs-lookup"><span data-stu-id="aa844-144">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="aa844-145">La propriété `Encoding` vous permet de définir la valeur de l'encodage de caractères souhaité.</span><span class="sxs-lookup"><span data-stu-id="aa844-145">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="aa844-146">L’exemple de client et de service utilise l’encodage de caractères ISO-8859-1 (Latin1), qui n’est pas pris en charge par le <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> de WCF.</span><span class="sxs-lookup"><span data-stu-id="aa844-146">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF.</span></span>

<span data-ttu-id="aa844-147">Le code suivant montre comment créer la liaison par programme à l'aide de l'encodeur de message texte personnalisé.</span><span class="sxs-lookup"><span data-stu-id="aa844-147">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="aa844-148">Ajout de la prise en charge des métadonnées à l’élément de liaison d’encodage de message</span><span class="sxs-lookup"><span data-stu-id="aa844-148">Adding Metadata Support to the Message Encoding Binding Element</span></span>

<span data-ttu-id="aa844-149">Les types qui dérivent de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> sont chargés de mettre à jour la version de la liaison SOAP dans le document WSDL généré pour le service.</span><span class="sxs-lookup"><span data-stu-id="aa844-149">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="aa844-150">Pour ce faire, implémentez la méthode `ExportEndpoint` sur l'interface <xref:System.ServiceModel.Description.IWsdlExportExtension>, puis modifiez le document WSDL généré.</span><span class="sxs-lookup"><span data-stu-id="aa844-150">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="aa844-151">Dans cet exemple, `CustomTextMessageBindingElement` utilise la logique d'exportation WSDL de `TextMessageEncodingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="aa844-151">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBindingElement`.</span></span>

<span data-ttu-id="aa844-152">Pour cet exemple, la configuration du client est créée manuellement.</span><span class="sxs-lookup"><span data-stu-id="aa844-152">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="aa844-153">Vous ne pouvez pas utiliser Svcutil.exe pour générer la configuration du client car `CustomTextMessageBindingElement` n'exporte pas d'assertion de stratégie pour décrire son comportement.</span><span class="sxs-lookup"><span data-stu-id="aa844-153">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="aa844-154">Il est en général préférable d’implémenter l’interface <xref:System.ServiceModel.Description.IPolicyExportExtension> sur un élément de liaison personnalisé pour exporter une assertion de stratégie personnalisée qui décrit le comportement ou la fonctionnalité implémentée par l’élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="aa844-154">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="aa844-155">Pour obtenir un exemple d’exportation d’une assertion de stratégie pour un élément de liaison personnalisé, consultez l’exemple [transport : UDP](transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="aa844-155">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](transport-udp.md) sample.</span></span>

## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="aa844-156">Gestionnaire de configuration de liaison d’encodage de message</span><span class="sxs-lookup"><span data-stu-id="aa844-156">Message Encoding Binding Configuration Handler</span></span>
<span data-ttu-id="aa844-157">La section précédente montre comment utiliser l'encodeur de message texte personnalisé par programme.</span><span class="sxs-lookup"><span data-stu-id="aa844-157">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="aa844-158">`CustomTextMessageEncodingBindingSection` implémente un gestionnaire de configuration qui vous permet de spécifier l'utilisation d'un encodeur de message texte personnalisé dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="aa844-158">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="aa844-159">La classe `CustomTextMessageEncodingBindingSection` dérive de la classe <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> .</span><span class="sxs-lookup"><span data-stu-id="aa844-159">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="aa844-160">La propriété `BindingElementType` indique au système de configuration le type d'élément de liaison à créer pour cette section.</span><span class="sxs-lookup"><span data-stu-id="aa844-160">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>

<span data-ttu-id="aa844-161">Tous les paramètres définis par `CustomTextMessageBindingElement` sont exposés en tant que propriétés dans `CustomTextMessageEncodingBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="aa844-161">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="aa844-162"><xref:System.Configuration.ConfigurationPropertyAttribute> permet de mapper les attributs d'élément de configuration aux propriétés et d'affecter des valeurs par défaut si les attributs ne sont pas définis.</span><span class="sxs-lookup"><span data-stu-id="aa844-162">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="aa844-163">Après avoir chargé et appliqué les valeurs de la configuration aux propriétés du type, la méthode <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> est appelée et convertit les propriétés en instance concrète d’un élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="aa844-163">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>

<span data-ttu-id="aa844-164">Ce gestionnaire de configuration mappe à la représentation suivante dans le fichier App.config ou Web.config du service ou du client.</span><span class="sxs-lookup"><span data-stu-id="aa844-164">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

<span data-ttu-id="aa844-165">L'exemple utilise l'encodage ISO-8859-1.</span><span class="sxs-lookup"><span data-stu-id="aa844-165">The sample uses the ISO-8859-1 encoding.</span></span>

<span data-ttu-id="aa844-166">Pour utiliser ce gestionnaire de configuration, il doit être enregistré à l'aide de l'élément de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="aa844-166">To use this configuration handler it must be registered using the following configuration element.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type="
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
