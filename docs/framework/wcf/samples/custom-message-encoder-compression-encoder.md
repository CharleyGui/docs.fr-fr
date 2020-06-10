---
title: 'Encodeur de message personnalisé : Encodeur de compression'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: db20ec20579d6fcb0ec202920db0d7781b0676df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600618"
---
# <a name="custom-message-encoder-compression-encoder"></a>Encodeur de message personnalisé : Encodeur de compression

Cet exemple montre comment implémenter un encodeur personnalisé à l’aide de la plateforme Windows Communication Foundation (WCF).

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`

## <a name="sample-details"></a>Détails de l'exemple

Cet exemple se compose d'un programme de console cliente (.exe), d'un programme de console de service auto-hébergé (.exe) et d'une bibliothèque d'encodeurs de message de compression (.dll). Le service implémente un contrat qui définit un modèle de communication demande-réponse. Le contrat est défini par l'interface `ISampleServer`, laquelle expose la chaîne de base qui reproduit en écho les opérations (`Echo` et `BigEcho`). Le client adresse des demandes synchrones à une opération donnée et le service répond en répétant de nouveau le message au client. L'activité du client et du service est visible dans les fenêtres de console. Cet exemple montre comment écrire un encodeur personnalisé et présente l'impact de la compression d'un message sur le câble. Vous pouvez ajouter l'instrumentation à l'encodeur de message de compression afin de calculer la taille de message, le temps de traitement ou les deux.

> [!NOTE]
> Dans le .NET Framework 4, la décompression automatique a été activée sur un client WCF si le serveur envoie une réponse compressée (créée avec un algorithme tel que GZip ou deflate). Si le service est hébergé sur le Web dans Internet Information Server (IIS), IIS peut être configuré de sorte que le service envoie une réponse compressée. Cet exemple peut être utilisé si la compression et la décompression doivent s'effectuer sur le client et dans le service, ou si le service est auto-hébergé.

L’exemple montre comment créer et intégrer un encodeur de message personnalisé dans une application WCF. La bibliothèque GZipEncoder.dll est déployée avec le client et le service. Cet exemple montre également l'impact de la compression des messages. Le code dans GZipEncoder.dll présente les procédures suivantes :

- Création d'un encodeur personnalisé et d'une fabrique d'encodeur.

- Développement d’un élément de liaison pour un encodeur personnalisé.

- Utilisation de la configuration de liaison personnalisée permettant d’intégrer des éléments de liaison personnalisés.

- Développement d’un gestionnaire de configuration personnalisé afin de permettre la configuration de fichier d’un élément de liaison personnalisé.

Comme indiqué précédemment, plusieurs couches sont implémentées dans un encodeur personnalisé. Pour mieux illustrer la relation entre chacune d'elles, la liste suivante présente un ordre simplifié des événements de démarrage du service :

1. Le serveur démarre.

2. Les informations de configuration sont lues.

    1. La configuration du service enregistre le gestionnaire de configuration personnalisé.

    2. L'hôte de service est créé et ouvert.

    3. L’élément de configuration personnalisé crée et retourne l’élément de liaison personnalisé.

    4. L’élément de liaison personnalisé crée et retourne une fabrique d’encodeur de message.

3. Un message est reçu.

4. La fabrique retourne un encodeur de message permettant de lire dans le message et d'écrire la réponse.

5. La couche d'encodeur est implémentée sous forme de fabrique de classe. Seule la fabrique de classe d'encodeur doit être exposée publiquement pour l'encodeur personnalisé. L’objet de fabrique est retourné par l’élément de liaison lorsque l’objet <xref:System.ServiceModel.ServiceHost> ou <xref:System.ServiceModel.ChannelFactory%601> est créé. Les encodeurs de message peuvent fonctionner en mode de mise en mémoire tampon ou en mode de diffusion en continu. Cet exemple présente ces deux modes.

Chaque mode est associée à une méthode `ReadMessage` et `WriteMessage` sur la classe abstraite `MessageEncoder`. La majeure partie de l'encodage a lieu dans ces méthodes. L'exemple encapsule les encodeurs de message texte et binaire existants. Cela permet à l'exemple de déléguer la lecture et l'écriture de la représentation de câble des messages à l'encodeur interne, et à l'encodeur de compression de compresser ou décompresser les résultats. Étant donné qu’il n’existe aucun pipeline pour l’encodage des messages, il s’agit du seul modèle d’utilisation de plusieurs encodeurs dans WCF. Une fois que le message a été décompressé, le message résultant est passé en haut de la pile pour être géré par la pile de canaux. Pendant la compression, le message compressé résultant est écrit directement dans le flux fourni.

Cet exemple utilise des méthodes d'assistance (`CompressBuffer` et `DecompressBuffer`) permettant d'effectuer la conversion des mémoires tampon en flux afin d'utiliser la classe `GZipStream`.

Les classes `ReadMessage` et `WriteMessage` mises en mémoire tampon utilisent la classe `BufferManager`. L'encodeur est uniquement accessible via la fabrique d'encodeur. La classe abstraite `MessageEncoderFactory` fournit la propriété `Encoder` permettant d'accéder à l'encodeur actuel et la méthode `CreateSessionEncoder` permettant de créer un encodeur qui prend en charge les sessions. Un encodeur de ce type peut être utilisé dans le scénario où le canal prend en charge des sessions, est ordonné et est fiable. Ce scénario permet d'optimiser dans chaque session les données écrites sur le câble. Si cet objectif n'est pas souhaité, la méthode de base ne doit pas être surchargée. La propriété `Encoder` fournit un mécanisme permettant d'accéder à l'encodeur sans session, et l'implémentation par défaut de la méthode `CreateSessionEncoder` retourne la valeur de la propriété. Cet exemple encapsulant un encodeur existant pour fournir la compression, l'implémentation `MessageEncoderFactory` accepte un `MessageEncoderFactory` qui représente la fabrique d'encodeur interne.

Maintenant que l’encodeur et la fabrique d’encodeur sont définis, ils peuvent être utilisés avec un client et un service WCF. Toutefois, ces encodeurs doivent être ajoutés à la pile de canaux. Vous pouvez dériver des classes des classes <xref:System.ServiceModel.ServiceHost> et <xref:System.ServiceModel.ChannelFactory%601>, et substituer les méthodes `OnInitialize` pour ajouter cette fabrique d'encodeur manuellement. Vous pouvez également exposer la fabrique d’encodeur via un élément de liaison personnalisé.

Pour créer un élément de liaison personnalisé, dérivez une classe de la classe <xref:System.ServiceModel.Channels.BindingElement>. Cependant, il existe plusieurs types d'éléments de liaison. Pour s’assurer que l’élément de liaison personnalisé est reconnu en tant qu’élément de liaison d’encodage de message, vous devez également implémenter <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>. <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> expose une méthode permettant de créer une nouvelle fabrique d'encodeur de message (`CreateMessageEncoderFactory`), laquelle est implémentée pour retourner une instance de la fabrique d'encodeur de message correspondante. En outre, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> possède une propriété permettant d'indiquer la version d'adressage. Cet exemple encapsulant les encodeurs existants, l’implémentation encapsule également les éléments de liaison d’encodeur existants et fournit un élément de liaison d’encodeur interne comme paramètre au constructeur, puis l’expose via une propriété. L'exemple de code suivant présente l'implémentation de la classe `GZipMessageEncodingBindingElement`.

```csharp
public sealed class GZipMessageEncodingBindingElement
                        : MessageEncodingBindingElement //BindingElement
                        , IPolicyExportExtension
{

    //We use an inner binding element to store information
    //required for the inner encoder.
    MessageEncodingBindingElement innerBindingElement;

        //By default, use the default text encoder as the inner encoder.
        public GZipMessageEncodingBindingElement()
            : this(new TextMessageEncodingBindingElement()) { }

    public GZipMessageEncodingBindingElement(MessageEncodingBindingElement messageEncoderBindingElement)
    {
        this.innerBindingElement = messageEncoderBindingElement;
    }

    public MessageEncodingBindingElement InnerMessageEncodingBindingElement
    {
        get { return innerBindingElement; }
        set { innerBindingElement = value; }
    }

    //Main entry point into the encoder binding element.
    // Called by WCF to get the factory that creates the
    //message encoder.
    public override MessageEncoderFactory CreateMessageEncoderFactory()
    {
        return new
GZipMessageEncoderFactory(innerBindingElement.CreateMessageEncoderFactory());
    }

    public override MessageVersion MessageVersion
    {
        get { return innerBindingElement.MessageVersion; }
        set { innerBindingElement.MessageVersion = value; }
    }

    public override BindingElement Clone()
    {
        return new
        GZipMessageEncodingBindingElement(this.innerBindingElement);
    }

    public override T GetProperty<T>(BindingContext context)
    {
        if (typeof(T) == typeof(XmlDictionaryReaderQuotas))
        {
            return innerBindingElement.GetProperty<T>(context);
        }
        else
        {
            return base.GetProperty<T>(context);
        }
    }

    public override IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.BuildInnerChannelFactory<TChannel>();
    }

    public override IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.BuildInnerChannelListener<TChannel>();
    }

    public override bool CanBuildChannelListener<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.CanBuildInnerChannelListener<TChannel>();
    }

    void IPolicyExportExtension.ExportPolicy(MetadataExporter exporter, PolicyConversionContext policyContext)
    {
        if (policyContext == null)
        {
            throw new ArgumentNullException("policyContext");
        }
       XmlDocument document = new XmlDocument();
       policyContext.GetBindingAssertions().Add(document.CreateElement(
            GZipMessageEncodingPolicyConstants.GZipEncodingPrefix,
            GZipMessageEncodingPolicyConstants.GZipEncodingName,
            GZipMessageEncodingPolicyConstants.GZipEncodingNamespace));
    }
}
```

Notez que la classe `GZipMessageEncodingBindingElement` implémente l'interface `IPolicyExportExtension`, afin que cet élément de liaison puisse être exporté en tant que stratégie dans les métadonnées, tel qu'indiqué dans l'exemple suivant.

```xml
<wsp:Policy wsu:Id="BufferedHttpSampleServer_ISampleServer_policy">
    <wsp:ExactlyOne>
      <wsp:All>
        <gzip:text xmlns:gzip=
        "http://schemas.microsoft.com/ws/06/2004/mspolicy/netgzip1" />
       <wsaw:UsingAddressing />
     </wsp:All>
   </wsp:ExactlyOne>
</wsp:Policy>
```

La classe `GZipMessageEncodingBindingElementImporter` implémente l'interface `IPolicyImportExtension` et importe la stratégie pour `GZipMessageEncodingBindingElement`. L'outil Svcutil.exe permet d'importer des stratégies dans le fichier de configuration et de gérer `GZipMessageEncodingBindingElement` ; les éléments suivants doivent être ajoutés à Svcutil.exe.config.

```xml
<configuration>
  <system.serviceModel>
    <extensions>
      <bindingElementExtensions>
        <add name="gzipMessageEncoding"
          type=
            "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
      </bindingElementExtensions>
    </extensions>
    <client>
      <metadata>
        <policyImporters>
          <remove type=
"System.ServiceModel.Channels.MessageEncodingBindingElementImporter, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
          <extension type=
"Microsoft.ServiceModel.Samples.GZipMessageEncodingBindingElementImporter, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </policyImporters>
      </metadata>
    </client>
  </system.serviceModel>
</configuration>
```

Maintenant qu’un élément de liaison correspondant existe pour l’encodeur de compression, il peut être raccordé par programme au service ou au client en construisant un nouvel objet de liaison personnalisé et en lui ajoutant l’élément de liaison personnalisé, tel qu’indiqué dans l’exemple de code suivant.

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();
bindingElements.Add(compBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
binding.Name = "SampleBinding";
binding.Namespace = "http://tempuri.org/bindings";
```

Même si cela peut s'avérer suffisant pour la majorité de scénarios utilisateur, la prise en charge d'une configuration de fichier est critique si un service doit être hébergé sur le Web. Pour prendre en charge le scénario hébergé sur le Web, vous devez développer un gestionnaire de configuration personnalisé afin de permettre la configuration d'un élément de liaison personnalisé dans un fichier.

Vous pouvez créer un gestionnaire de configuration pour l’élément de liaison en plus du système de configuration. Ce gestionnaire de configuration doit dériver de la classe <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType>Indique au système de configuration le type d’élément de liaison à créer pour cette section. Tous les aspects de `BindingElement` qui peuvent être définis doivent être exposés en tant que propriétés dans la classe dérivée <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>. L' <xref:System.Configuration.ConfigurationPropertyAttribute> aide à mapper les attributs d’élément de configuration aux propriétés et à définir des valeurs par défaut si des attributs sont manquants. Après avoir chargé et appliqué les valeurs de la configuration aux propriétés, la méthode <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> est appelée et convertit les propriétés en instance concrète d'un élément de liaison. La <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType> méthode permet de convertir les propriétés sur la <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> classe dérivée en valeurs à définir sur l’élément de liaison nouvellement créé.

L'exemple de code suivant présente l'implémentation de `GZipMessageEncodingElement`.

```csharp
public class GZipMessageEncodingElement : BindingElementExtensionElement
{
    public GZipMessageEncodingElement()
    {
    }

//Called by the WCF to discover the type of binding element this
//config section enables
    public override Type BindingElementType
    {
        get { return typeof(GZipMessageEncodingBindingElement); }
    }

    //The only property we need to configure for our binding element is
    //the type of inner encoder to use. Here, we support text and
    //binary.
    [ConfigurationProperty("innerMessageEncoding",
                         DefaultValue = "textMessageEncoding")]
    public string InnerMessageEncoding
    {
        get { return (string)base["innerMessageEncoding"]; }
        set { base["innerMessageEncoding"] = value; }
    }

    //Called by the WCF to apply the configuration settings (the
    //property above) to the binding element
    public override void ApplyConfiguration(BindingElement bindingElement)
    {
        GZipMessageEncodingBindingElement binding =
                (GZipMessageEncodingBindingElement)bindingElement;
        PropertyInformationCollection propertyInfo =
                    this.ElementInformation.Properties;
        if (propertyInfo["innerMessageEncoding"].ValueOrigin !=
                                     PropertyValueOrigin.Default)
        {
            switch (this.InnerMessageEncoding)
            {
                case "textMessageEncoding":
                    binding.InnerMessageEncodingBindingElement =
                      new TextMessageEncodingBindingElement();
                    break;
                case "binaryMessageEncoding":
                    binding.InnerMessageEncodingBindingElement =
                         new BinaryMessageEncodingBindingElement();
                    break;
            }
        }
    }

    //Called by the WCF to create the binding element
    protected override BindingElement CreateBindingElement()
    {
        GZipMessageEncodingBindingElement bindingElement =
                new GZipMessageEncodingBindingElement();
        this.ApplyConfiguration(bindingElement);
        return bindingElement;
    }
}
```

Ce gestionnaire de configuration mappe à la représentation suivante dans le fichier App.config ou Web.config du service ou du client.

```xml
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />
```

Pour utiliser ce gestionnaire de configuration, il doit être enregistré dans l' [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) élément, comme illustré dans l’exemple de configuration suivant.

```xml
<extensions>
    <bindingElementExtensions>
       <add
           name="gzipMessageEncoding"
           type=
           "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement,
           GZipEncoder, Version=1.0.0.0, Culture=neutral,
           PublicKeyToken=null" />
      </bindingElementExtensions>
</extensions>
```

Lorsque vous exécutez le serveur, les demandes et réponses d'opération s'affichent dans la fenêtre de console. Appuyez sur ENTER dans la fenêtre pour arrêter le serveur.

```console
Press Enter key to Exit.

        Server Echo(string input) called:
        Client message: Simple hello

        Server BigEcho(string[] input) called:
        64 client messages
```

Lorsque vous exécutez le client, les demandes et réponses d'opération s'affichent dans la fenêtre de console. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.

```console
Calling Echo(string):
Server responds: Simple hello Simple hello

Calling BigEcho(string[]):
Server responds: Hello 0

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Installez ASP.NET 4,0 à l’aide de la commande suivante :

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

3. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).

4. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`
