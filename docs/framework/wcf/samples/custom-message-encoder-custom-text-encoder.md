---
title: 'Encodeur de message personnalisé : Encodeur de texte personnalisé'
description: Utilisez cet exemple pour implémenter un encodeur de message texte personnalisé à l’aide de WCF. Cet encodeur prend en charge tous les encodages de caractères pris en charge par la plateforme pour l’interopérabilité.
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 89f0bf09ba6408e24f642a67f2e7ac8243608dcb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240964"
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Encodeur de message personnalisé : Encodeur de texte personnalisé

Cet exemple montre comment implémenter un encodeur de message texte personnalisé à l’aide de Windows Communication Foundation (WCF).

> [!WARNING]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

Le <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> de WCF prend en charge uniquement les encodages Unicode UTF-8, UTF-16 et Big-endian. Dans cet exemple, l’encodeur de message texte personnalisé prend en charge tous les encodages de caractères pris en charge par la plateforme qui peuvent être nécessaires pour l’interopérabilité. L’exemple se compose d’un programme de console client (. exe), d’une bibliothèque de service (. dll) hébergée par Internet Information Services (IIS) et d’une bibliothèque de codeur de message texte (. dll). Le service implémente un contrat qui définit un modèle de communication demande-réponse. Le contrat est défini par l'interface `ICalculator`, laquelle expose les opérations mathématiques suivantes : addition, soustraction, multiplication et division. Le client adresse des demandes synchrones à une opération mathématique donnée et le service répond avec le résultat. Le client et le service utilisent `CustomTextMessageEncoder` au lieu du <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> par défaut.

L’implémentation d’encodeur personnalisée se compose d’une fabrique d’encodeur de message, d’un encodeur de message, d’un élément de liaison d’encodage de message et d’un gestionnaire de configuration, et présente les éléments suivants :

- Création d'un encodeur personnalisé et d'une fabrique d'encodeur.

- Création d’un élément de liaison pour un encodeur personnalisé.

- Utilisation de la configuration de liaison personnalisée permettant d’intégrer des éléments de liaison personnalisés.

- Développement d’un gestionnaire de configuration personnalisé afin de permettre la configuration de fichier d’un élément de liaison personnalisé.

## <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Installez ASP.NET 4,0 à l’aide de la commande suivante.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

3. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).

4. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).

## <a name="message-encoder-factory-and-the-message-encoder"></a>Fabrique d'encodeur de message et encodeur de message

Lorsque <xref:System.ServiceModel.ServiceHost> ou le canal client est ouvert, le composant au moment du design `CustomTextMessageBindingElement` crée `CustomTextMessageEncoderFactory`. La fabrique crée `CustomTextMessageEncoder`. L'encodeur de message fonctionne à la fois en mode de diffusion en continu et en mode de mise en mémoire tampon. Il utilise <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter> pour respectivement lire et écrire les messages. Contrairement aux lecteurs et aux Writers XML optimisés de WCF qui ne prennent en charge que les enregistreurs Unicode UTF-8, UTF-16 et Big-endian, ces lecteurs et enregistreurs prennent en charge tous les encodages pris en charge par la plateforme.

L'exemple de code suivant présente CustomTextMessageEncoder.

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

L'exemple de code suivant montre comment créer la fabrique d'encodeur de message.

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

## <a name="message-encoding-binding-element"></a>Élément de liaison d'encodage de message

Les éléments de liaison autorisent la configuration de la pile Runtime WCF. Pour utiliser l’encodeur de message personnalisé dans une application WCF, vous devez disposer d’un élément de liaison qui crée la fabrique d’encodeur de message avec les paramètres appropriés au niveau approprié dans la pile Runtime.

`CustomTextMessageBindingElement` dérive de la classe de base <xref:System.ServiceModel.Channels.BindingElement> et hérite de la classe <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>. Cela permet à d’autres composants WCF de reconnaître cet élément de liaison comme étant un élément de liaison d’encodage de message. L'implémentation de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> retourne une instance de la fabrique d'encodeur de message correspondante avec les paramètres appropriés.

`CustomTextMessageBindingElement` expose des paramètres pour `MessageVersion`, `ContentType` et `Encoding` via des propriétés. L'encodeur prend en charge les versions Soap11Addressing et Soap12Addressing1. La valeur par défaut est Soap11Addressing1. La valeur par défaut de `ContentType` est "text/xml". La propriété `Encoding` vous permet de définir la valeur de l'encodage de caractères souhaité. L’exemple de client et de service utilise l’encodage de caractères ISO-8859-1 (Latin1), qui n’est pas pris en charge par le <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> de WCF.

Le code suivant montre comment créer la liaison par programme à l'aide de l'encodeur de message texte personnalisé.

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>Ajout de la prise en charge des métadonnées à l’élément de liaison d’encodage de message

Les types qui dérivent de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> sont chargés de mettre à jour la version de la liaison SOAP dans le document WSDL généré pour le service. Pour ce faire, implémentez la méthode `ExportEndpoint` sur l'interface <xref:System.ServiceModel.Description.IWsdlExportExtension>, puis modifiez le document WSDL généré. Dans cet exemple, `CustomTextMessageBindingElement` utilise la logique d'exportation WSDL de `TextMessageEncodingBindingElement`.

Pour cet exemple, la configuration du client est créée manuellement. Vous ne pouvez pas utiliser Svcutil.exe pour générer la configuration du client car `CustomTextMessageBindingElement` n'exporte pas d'assertion de stratégie pour décrire son comportement. Il est en général préférable d’implémenter l’interface <xref:System.ServiceModel.Description.IPolicyExportExtension> sur un élément de liaison personnalisé pour exporter une assertion de stratégie personnalisée qui décrit le comportement ou la fonctionnalité implémentée par l’élément de liaison. Pour obtenir un exemple d’exportation d’une assertion de stratégie pour un élément de liaison personnalisé, consultez l’exemple [transport : UDP](transport-udp.md) .

## <a name="message-encoding-binding-configuration-handler"></a>Gestionnaire de configuration de liaison d’encodage de message

La section précédente montre comment utiliser l'encodeur de message texte personnalisé par programme. `CustomTextMessageEncodingBindingSection` implémente un gestionnaire de configuration qui vous permet de spécifier l'utilisation d'un encodeur de message texte personnalisé dans un fichier de configuration. La classe `CustomTextMessageEncodingBindingSection` dérive de la classe <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> . La propriété `BindingElementType` indique au système de configuration le type d'élément de liaison à créer pour cette section.

Tous les paramètres définis par `CustomTextMessageBindingElement` sont exposés en tant que propriétés dans `CustomTextMessageEncodingBindingSection`. <xref:System.Configuration.ConfigurationPropertyAttribute> permet de mapper les attributs d'élément de configuration aux propriétés et d'affecter des valeurs par défaut si les attributs ne sont pas définis. Après avoir chargé et appliqué les valeurs de la configuration aux propriétés du type, la méthode <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> est appelée et convertit les propriétés en instance concrète d’un élément de liaison.

Ce gestionnaire de configuration mappe à la représentation suivante dans le fichier App.config ou Web.config du service ou du client.

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

L'exemple utilise l'encodage ISO-8859-1.

Pour utiliser ce gestionnaire de configuration, il doit être enregistré à l'aide de l'élément de configuration suivant.

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type="
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
