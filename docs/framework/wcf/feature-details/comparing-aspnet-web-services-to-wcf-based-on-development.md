---
title: Comparaison des services Web ASP.NET et de WCF du point de vue du développement
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: c5a2145a6d7b631a666df94eb0c1fc53cbc3c55f
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202262"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a>Comparaison des services Web ASP.NET et de WCF du point de vue du développement

Windows Communication Foundation (WCF) dispose d’une option de mode de compatibilité ASP.NET pour permettre aux applications WCF d’être programmées et configurées comme les services Web ASP.NET, et de reproduire leur comportement. Les sections suivantes comparent les services Web ASP.NET et WCF en fonction de ce qui est requis pour développer des applications à l’aide de ces deux technologies.

## <a name="data-representation"></a>Représentation des données

Le développement d'un service Web avec ASP.NET commence en général par la définition de tous les types de données complexes que le service doit utiliser. ASP.NET repose sur le <xref:System.Xml.Serialization.XmlSerializer> pour traduire en XML des données représentées par les types .NET Framework pour la transmission en direction ou depuis un service et pour traduire des données reçues comme XML en objets .NET Framework. La définition des types de données complexes à utiliser par un service ASP.NET nécessite de définir les classes .NET Framework que le <xref:System.Xml.Serialization.XmlSerializer> peut sérialiser depuis le XML ou vers celui-ci. Ces classes peuvent être écrites manuellement ou générées à partir des définitions des types dans le schéma XML à l'aide de l'utilitaire de prise en charge des types de données/schémas XML de ligne de commande, xsd.exe.

Les éléments suivants répertorient les problèmes clés à connaître lors de la définition des classes .NET Framework que le <xref:System.Xml.Serialization.XmlSerializer> peut sérialiser en XML ou depuis celui-ci :

- Seuls les champs et les propriétés publics des objets .NET Framework sont traduits en XML.

- Les instances de classes de collection peuvent être sérialisées en XML uniquement si les classes implémentent l’interface <xref:System.Collections.IEnumerable> ou <xref:System.Collections.ICollection>.

- Les classes qui implémentent l'interface <xref:System.Collections.IDictionary>, telles que <xref:System.Collections.Hashtable>, ne peuvent pas être sérialisées en XML.

- Le grand nombre de types d'attributs dans l'espace de noms <xref:System.Xml.Serialization> peut être ajouté à une classe .NET Framework et à ses membres pour contrôler le mode de représentation en XML des instances de la classe.

Le développement d’applications WCF commence généralement par la définition de types complexes. WCF peut être configuré pour utiliser les mêmes types de .NET Framework que les services Web ASP.NET.

WCF <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> peuvent être ajoutés aux types de .NET Framework pour indiquer que les instances du type doivent être sérialisées en XML, et quels champs ou propriétés particuliers du type doivent être sérialisés, comme indiqué dans l’exemple de code suivant.

```csharp
//Example One:
[DataContract]
public class LineItem
{
    [DataMember]
    public string ItemNumber;
    [DataMember]
    public decimal Quantity;
    [DataMember]
    public decimal UnitPrice;
}

//Example Two:
public class LineItem
{
    [DataMember]
    private string itemNumber;
    [DataMember]
    private decimal quantity;
    [DataMember]
    private decimal unitPrice;

    public string ItemNumber
    {
      get
      {
          return this.itemNumber;
      }

      set
      {
          this.itemNumber = value;
      }
    }

    public decimal Quantity
    {
        get
        {
            return this.quantity;
        }

        set
        {
            this.quantity = value;
        }
    }

    public decimal UnitPrice
    {
      get
      {
          return this.unitPrice;
      }

      set
      {
          this.unitPrice = value;
      }
    }
}

//Example Three:
public class LineItem
{
     private string itemNumber;
     private decimal quantity;
     private decimal unitPrice;

     [DataMember]
     public string ItemNumber
     {
       get
       {
          return this.itemNumber;
       }

       set
       {
           this.itemNumber = value;
       }
     }

     [DataMember]
     public decimal Quantity
     {
          get
          {
              return this.quantity;
          }

          set
          {
             this.quantity = value;
          }
     }

     [DataMember]
     public decimal UnitPrice
     {
          get
          {
              return this.unitPrice;
          }

          set
          {
              this.unitPrice = value;
          }
     }
}
```

<xref:System.Runtime.Serialization.DataContractAttribute> signifie que zéro ou plusieurs des champs ou des propriétés d'un type vont être sérialisés, alors que <xref:System.Runtime.Serialization.DataMemberAttribute> indique qu'une propriété ou un champ particulier va être sérialisé. <xref:System.Runtime.Serialization.DataContractAttribute> peut être appliqué à une classe ou à une structure. Le <xref:System.Runtime.Serialization.DataMemberAttribute> peut être appliqué à un champ ou à une propriété, et les champs et les propriétés auxquels l'attribut est appliqué peuvent être publics ou privés. Les instances de types qui ont <xref:System.Runtime.Serialization.DataContractAttribute> été appliquées à elles sont appelées contrats de données dans WCF. Elles sont sérialisées en XML à l'aide de <xref:System.Runtime.Serialization.DataContractSerializer>.

Les éléments suivants répertorient une liste des différences principales entre l'utilisation de <xref:System.Runtime.Serialization.DataContractSerializer> et celle de <xref:System.Xml.Serialization.XmlSerializer> et les divers attributs de l'espace de noms <xref:System.Xml.Serialization>.

- Le <xref:System.Xml.Serialization.XmlSerializer> et les attributs de l'espace de noms <xref:System.Xml.Serialization> sont conçus pour vous permettre de mapper des types .NET Framework à des types valides définis dans le schéma XML, ils fournissent ainsi un contrôle très précis sur la manière de représenter un type en XML. Les <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> fournissent très peu de contrôle sur la manière de représenter un type en XML. Vous pouvez spécifier uniquement les espaces de noms et les noms utilisés pour représenter le type et ses champs ou propriétés dans le XML, et la séquence dans laquelle les champs et propriétés apparaissent dans le XML :

  ```csharp
  [DataContract(
  Namespace="urn:Contoso:2006:January:29",
  Name="LineItem")]
  public class LineItem
  {
        [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]
        public string itemNumber;
        [DataMember(Name="Quantity",IsRequired=false,Order = 1)]
        public decimal quantity;
        [DataMember(Name="Price",IsRequired=false,Order = 2)]
        public decimal unitPrice;
  }
  ```

  Tout ce qui concerne la structure du XML utilisé pour représenter le type .NET est déterminé par le <xref:System.Runtime.Serialization.DataContractSerializer>.

- En ne permettant qu'un contrôle limité sur la manière de représenter un type en XML, le processus de sérialisation devient très prévisible pour le <xref:System.Runtime.Serialization.DataContractSerializer>, et, par conséquent, plus facile à optimiser. Un avantage pratique de la conception de <xref:System.Runtime.Serialization.DataContractSerializer> est d'offrir de meilleures performances, une amélioration d'environ dix pour cent.

- Les attributs à utiliser avec le <xref:System.Xml.Serialization.XmlSerializer> n'indiquent pas quels champs ou propriétés du type sont sérialisés en XML, alors que le <xref:System.Runtime.Serialization.DataMemberAttribute> à utiliser avec le <xref:System.Runtime.Serialization.DataContractSerializer> indique explicitement les champs ou les propriétés sérialisées. Par conséquent, les contrats de données sont des contrats explicites sur la structure des données qu'une application doit envoyer et recevoir.

- Le <xref:System.Xml.Serialization.XmlSerializer> peut traduire uniquement les membres publics d’un objet .NET en XML, le <xref:System.Runtime.Serialization.DataContractSerializer> peut traduire les membres des objets en XML indépendamment des modificateurs d’accès de ces membres.

- Étant donné qu'il peut sérialiser en XML les membres non publics des types, le <xref:System.Runtime.Serialization.DataContractSerializer> offre moins de restrictions sur la variété des types .NET qu'il peut sérialiser en XML. En particulier, il peut traduire en XML des types tels que <xref:System.Collections.Hashtable> qui implémentent l'interface <xref:System.Collections.IDictionary>. Il est plus probable que <xref:System.Runtime.Serialization.DataContractSerializer> puisse sérialiser les instances d'un type .NET préexistant en XML sans avoir à modifier la définition du type ou à développer un wrapper qui lui sera destiné.

- Une autre conséquence de la capacité de <xref:System.Runtime.Serialization.DataContractSerializer> d'accéder aux membres non publics d'un type est qu'il requiert une confiance totale, ce qui n'est pas le cas de <xref:System.Xml.Serialization.XmlSerializer>. L’autorisation d’accès au code de confiance totale donne un accès complet à toutes les ressources sur un ordinateur accessibles à l’aide des informations d’identification sous lesquelles le code s’exécute. Cette option doit être utilisée avec précaution, car le code d’un niveau de confiance totale accède à toutes les ressources de votre ordinateur.

- Le <xref:System.Runtime.Serialization.DataContractSerializer> incorpore une prise en charge du suivi des versions :

  - Le <xref:System.Runtime.Serialization.DataMemberAttribute> a une propriété <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> qui peut prendre une valeur false pour les membres ajoutés aux nouvelles versions d'un contrat de données qui ne figuraient pas dans les versions antérieures, ce qui permet aux applications avec la version plus récente du contrat de traiter des versions antérieures.

  - En implémentant l'interface <xref:System.Runtime.Serialization.IExtensibleDataObject> par le contrat de données, il est possible pour le <xref:System.Runtime.Serialization.DataContractSerializer> de passer des membres définis dans des versions plus récentes d'un contrat de données par l'intermédiaire d'applications avec des versions antérieures du contrat.

En dépit de toutes ces différences, le XML dans lequel <xref:System.Xml.Serialization.XmlSerializer> sérialise un type par défaut est sémantiquement identique au XML dans lequel <xref:System.Runtime.Serialization.DataContractSerializer> sérialise un type, à condition que l'espace de noms du XML soit défini explicitement. La classe suivante, qui a des attributs à utiliser avec les deux sérialiseurs, est traduite en XML sémantiquement identique par le <xref:System.Xml.Serialization.XmlSerializer> et par le <xref:System.Runtime.Serialization.DataContractAttribute> :

```csharp
[Serializable]
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]
[DataContract(Namespace="urn:Contoso:2006:January:29")]
public class LineItem
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}
```

Le kit de développement logiciel (SDK) Windows comprend un outil en ligne de commande appelé outil de l' [utilitaire de métadonnées ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). À l’instar de l’outil Xsd. exe utilisé avec les services Web ASP.NET, Svcutil. exe peut générer des définitions de types de données .NET à partir d’un schéma XML. Les types sont des contrats de données si le <xref:System.Runtime.Serialization.DataContractSerializer> peut émettre du XML au format défini par le schéma XML ; sinon, ils sont destinés à être sérialisés à l'aide du <xref:System.Xml.Serialization.XmlSerializer>. Svcutil. exe peut également générer un schéma XML à partir de contrats de données à l’aide de son `dataContractOnly` commutateur.

> [!NOTE]
> Bien que les services Web ASP.NET utilisent le <xref:System.Xml.Serialization.XmlSerializer> , et le mode de compatibilité ASP.net WCF fait que les services WCF imitent le comportement des services web ASP.net, l’option de compatibilité ASP.net ne limite pas l’utilisation de <xref:System.Xml.Serialization.XmlSerializer> . Il est toujours possible d'utiliser le <xref:System.Runtime.Serialization.DataContractSerializer> avec des services qui s'exécutent en mode de compatibilité ASP.NET.

## <a name="service-development"></a>Développement des services

Pour développer un service à l'aide d'ASP.NET, il est d'usage d'ajouter l'attribut <xref:System.Web.Services.WebService> à une classe, et le <xref:System.Web.Services.WebMethodAttribute> à une des méthodes de cette classe qui servent d'opérations du service :

```csharp
[WebService]
public class Service : T:System.Web.Services.WebService
{
    [WebMethod]
    public string Echo(string input)
    {
       return input;
    }
}
```

ASP.NET 2.0 introduit la possibilité d'ajouter l'attribut <xref:System.Web.Services.WebService> et <xref:System.Web.Services.WebMethodAttribute> à une interface plutôt qu'à une classe, et d'écrire une classe pour implémenter l'interface :

```csharp
[WebService]
public interface IEcho
{
    [WebMethod]
    string Echo(string input);
}

public class Service : IEcho
{

   public string Echo(string input)
   {
        return input;
    }
}
```

L'utilisation de cette option est recommandée, car l'interface avec l'attribut <xref:System.Web.Services.WebService> représente un contrat pour les opérations effectuées par le service qui peuvent être réutilisées avec différentes classes qui implémentent éventuellement ce même contrat de différentes façons.

Un service WCF est fourni en définissant un ou plusieurs points de terminaison WCF. Un point de terminaison est défini par une adresse, une liaison et un contrat de service. L'adresse définit l'emplacement du service. La liaison spécifie le mode de communication avec le service. Le contrat de service définit les opérations que le service peut effectuer.

Le contrat de service est défini habituellement en premier en ajoutant <xref:System.ServiceModel.ServiceContractAttribute> et <xref:System.ServiceModel.OperationContractAttribute> à une interface :

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

<xref:System.ServiceModel.ServiceContractAttribute>Spécifie que l’interface définit un contrat de service WCF et le <xref:System.ServiceModel.OperationContractAttribute> indique, le cas échéant, les méthodes de l’interface qui définissent les opérations du contrat de service.

Une fois qu'un contrat de service a été défini, il est implémenté dans une classe, en implémentant par la classe l'interface qui définit le contrat de service :

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

Une classe qui implémente un contrat de service est appelée type de service dans WCF.

L’étape suivante consiste à associer une adresse et une liaison à un type de service. Cela s’effectue généralement dans un fichier de configuration, soit en modifiant le fichier directement, soit à l’aide d’un éditeur de configuration fourni avec WCF. Voici un exemple d'un fichier de configuration.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
     <system.serviceModel>
      <services>
      <service name="Service ">
       <endpoint
        address="EchoService"
        binding="basicHttpBinding"
        contract="IEchoService "/>
      </service>
      </services>
     </system.serviceModel>
</configuration>
```

La liaison spécifie le jeu de protocoles permettant de communiquer avec l’application. Le tableau suivant répertorie les liaisons fournies par le système qui représentent des options courantes.

|Nom|Objectif|
|----------|-------------|
|BasicHttpBinding|Interopérabilité avec les services et les clients Web qui prennent en charge WS-BasicProfile 1.1 et Basic Security Profile 1.0.|
|WSHttpBinding|Interopérabilité avec les services et clients Web qui prennent en charge les protocoles WS-* sur HTTP.|
|WSDualHttpBinding|Communication HTTP en duplex au cours de laquelle le récepteur d'un message initial ne répond pas directement à l'expéditeur initial, mais peut transmettre pendant un certain temps un nombre illimité de réponses à l'aide de HTTP conformément aux protocoles WS-*.|
|WSFederationBinding|Communication HTTP au cours de laquelle l'accès aux ressources d'un service peut être contrôlé en fonction des informations d'identification émises par un fournisseur d'informations d'identification identifié explicitement.|
|NetTcpBinding|Communication sécurisée, fiable et hautes performances entre les entités logicielles WCF sur un réseau.|
|NetNamedPipeBinding|Communication sécurisée, fiable et hautes performances entre les entités logicielles WCF sur le même ordinateur.|
|NetMsmqBinding|Communication entre les entités de logiciels WCF à l’aide de MSMQ.|
|MsmqIntegrationBinding|Communication entre une entité de logiciel WCF et une autre entité logicielle à l’aide de MSMQ.|
|NetPeerTcpBinding|Communication entre les entités logicielles WCF à l’aide de la mise en réseau pair à pair Windows.|

La liaison fournie par le système, <xref:System.ServiceModel.BasicHttpBinding>, incorpore le jeu de protocoles pris en charge par les services Web ASP.NET.

Les liaisons personnalisées pour les applications WCF sont facilement définies en tant que collections des classes d’éléments de liaison que WCF utilise pour implémenter des protocoles individuels. Les nouveaux éléments de liaison peuvent être écrits pour représenter des protocoles supplémentaires.

Le comportement interne des types de service peut être ajusté à l'aide des propriétés d'une famille de classes appelées des comportements. Dans ce contexte, la classe <xref:System.ServiceModel.ServiceBehaviorAttribute> est utilisée pour spécifier que le type de service doit être multithread.

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple)]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

Certains comportements, comme <xref:System.ServiceModel.ServiceBehaviorAttribute>, sont des attributs. Ceux dont les propriétés peuvent être définies par les administrateurs, peuvent être modifiés dans la configuration d'une application.

Pour programmer des types de service, la classe <xref:System.ServiceModel.OperationContext> est fréquemment utilisée. Sa propriété statique <xref:System.ServiceModel.OperationContext.Current%2A> fournit l'accès aux informations du contexte d'exécution d'une opération. <xref:System.ServiceModel.OperationContext> est semblable aux classes <xref:System.Web.HttpContext> et <xref:System.EnterpriseServices.ContextUtil>.

## <a name="hosting"></a>Hébergement

Les services Web ASP.NET sont compilés dans un assembly de bibliothèque de classes. Un fichier appelé le fichier de service est fourni avec l'extension .asmx et contient une directive `@ WebService` qui identifie la classe qui contient le code pour le service et l'assembly qui la contient.

`<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>`

Le fichier de service est copié dans une racine d'application ASP.NET dans les services IIS (Internet Information Services), et l'assembly est copié dans le sous-répertoire \bin de cette racine de l'application. L'application est ensuite accessible depuis l'URL du fichier de service dans la racine de l'application.

Les services WCF peuvent être hébergés facilement dans IIS 5,1 ou 6,0, le service d’activation des processus Windows (WAS) fourni dans le cadre d’IIS 7,0 et dans toute application .NET. Pour héberger un service dans les services IIS 5.1 ou 6.0, le service doit utiliser HTTP comme protocole de transport de communications.

Pour héberger un service dans les services IIS 5.1, 6.0 ou dans le service WAS, procédez comme suit :

1. Compilez le type de service dans un assembly de bibliothèque de classes.

2. Créez un fichier de service avec une extension .svc et une directive `@ ServiceHost` pour identifier le type de service :

    `<%@ServiceHost language="c#" Service="MyService" %>`

3. Copiez le fichier de service dans un répertoire virtuel, et l'assembly dans le sous-répertoire \bin de ce répertoire virtuel.

4. Copiez le fichier de configuration dans le répertoire virtuel et nommez-le Web.config.

L'application est ensuite accessible depuis l'URL du fichier de service dans la racine de l'application.

Pour héberger un service WCF dans une application .NET, compilez le type de service dans un assembly de bibliothèque de classes référencé par l’application et programmez l’application pour héberger le service à l’aide de la <xref:System.ServiceModel.ServiceHost> classe. Les éléments suivants sont un exemple de la programmation de base requise :

```csharp
string httpBaseAddress = "http://www.contoso.com:8000/";
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";

Uri httpBaseAddressUri = new Uri(httpBaseAddress);
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);

Uri[] baseAddresses = new Uri[] {
 httpBaseAddressUri,
 tcpBaseAddressUri};

using(ServiceHost host = new ServiceHost(
typeof(Service), //"Service" is the name of the service type baseAddresses))
{
     host.Open();

     […] //Wait to receive messages
     host.Close();
}
```

Cet exemple indique comment les adresses pour un ou plusieurs protocoles de transport sont spécifiées dans la construction d'un <xref:System.ServiceModel.ServiceHost>. Ces adresses sont connues sous le nom d'adresses de base.

L’adresse fournie pour tout point de terminaison d’un service WCF est une adresse relative à l’adresse de base de l’hôte du point de terminaison. L'hôte peut avoir une adresse de base pour chaque protocole de transport de communication. Dans l'exemple de configuration du fichier de configuration précédent, l'objet <xref:System.ServiceModel.BasicHttpBinding> sélectionné comme point de terminaison fait appel à HTTP comme protocole de transport, l'adresse du point de terminaison, `EchoService`, est donc relative à l'adresse de base HTTP de l'hôte. Dans le cas de l’hôte dans l’exemple précédent, l’adresse de base HTTP est `http://www.contoso.com:8000/` . Pour un service hébergé dans les services IIS ou WAS, l'adresse de base est l'URL du fichier de service du service.

Seuls les services hébergés dans IIS ou WAS, et ceux qui sont configurés avec HTTP comme protocole de transport exclusivement, peuvent être utilisés pour utiliser l’option de mode de compatibilité WCF ASP.NET. L'activation de cette option requiert les étapes suivantes.

1. Le programmeur doit ajouter l'attribut <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> au type de service et spécifier que le mode de compatibilité ASP.NET est autorisé ou requis.

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. L'administrateur doit configurer l'application pour qu'elle utilise le mode de compatibilité ASP.NET.

    ```xml
    <configuration>
         <system.serviceModel>
          <services>
          […]
          </services>
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
        </system.serviceModel>
    </configuration>
    ```

    Les applications WCF peuvent également être configurées pour utiliser le fichier. asmx en tant qu’extension de leurs fichiers de service plutôt que. svc.

    ```xml
    <system.web>
         <compilation>
          <compilation debug="true">
          <buildProviders>
           <remove extension=".asmx"/>
           <add extension=".asmx"
            type="System.ServiceModel.ServiceBuildProvider,
            System.ServiceModel,
            Version=3.0.0.0,
            Culture=neutral,
            PublicKeyToken=b77a5c561934e089" />
          </buildProviders>
          </compilation>
         </compilation>
    </system.web>
    ```

    Cette option peut vous éviter d’avoir à modifier les clients configurés pour utiliser les URL des fichiers de service. asmx lors de la modification d’un service pour utiliser WCF.

## <a name="client-development"></a>Développement client

Les clients pour les services Web ASP.NET sont générés à l'aide de l'outil de ligne de commande, WSDL.exe, qui fournit l'URL du fichier .asmx comme entrée. L’outil correspondant fourni par WCF est l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Il génère un module de code avec la définition du contrat de service et la définition d’une classe de client WCF. Il génère également un fichier de configuration avec l'adresse et la liaison du service.

Pour programmer un client d’un service distant, il est généralement recommandé de programmer selon un modèle asynchrone. Le code généré par l'outil WSDL.exe fournit toujours un modèle synchrone et asynchrone par défaut. Le code généré par l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) peut fournir l’un ou l’autre modèle. Il fournit le modèle synchrone par défaut. Si l’outil est exécuté avec le commutateur `/async`, le code généré fournit le modèle asynchrone.

Il n’y a aucune garantie que les noms des classes de client WCF générées par ASP. Par défaut, l’outil WSDL. exe du réseau correspond aux noms des classes de client WCF générées par l’outil Svcutil. exe. En particulier, les noms des propriétés des classes qui doivent être sérialisées à l'aide du <xref:System.Xml.Serialization.XmlSerializer> reçoivent par défaut le suffixe Property dans le code généré par l'outil Svcutil.exe, ce qui n'est pas le cas avec l'outil WSDL.exe.

## <a name="message-representation"></a>Représentation de message

Les en-têtes des messages SOAP envoyés et reçus par les services Web ASP.NET peuvent être personnalisés. Une classe est dérivée de <xref:System.Web.Services.Protocols.SoapHeader> pour définir la structure de l'en-tête, puis, le <xref:System.Web.Services.Protocols.SoapHeaderAttribute> est utilisé pour indiquer la présence de l'en-tête.

```csharp
public class SomeProtocol : SoapHeader
{
     public long CurrentValue;
     public long Total;
}

[WebService]
public interface IEcho
{
     SomeProtocol ProtocolHeader
     {
      get;
     set;
     }

     [WebMethod]
     [SoapHeader("ProtocolHeader")]
     string PlaceOrders(PurchaseOrderType order);
}

public class Service: WebService, IEcho
{
     private SomeProtocol protocolHeader;

     public SomeProtocol ProtocolHeader
     {
         get
         {
              return this.protocolHeader;
         }

         set
         {
              this.protocolHeader = value;
         }
     }

     string PlaceOrders(PurchaseOrderType order)
     {
         long currentValue = this.protocolHeader.CurrentValue;
     }
}
```

WCF fournit les attributs,, <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.MessageHeaderAttribute> et <xref:System.ServiceModel.MessageBodyMemberAttribute> pour décrire la structure des messages SOAP envoyés et reçus par un service.

```csharp
[DataContract]
public class SomeProtocol
{
     [DataMember]
     public long CurrentValue;
     [DataMember]
     public long Total;
}

[DataContract]
public class Item
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}

[MessageContract]
public class ItemMessage
{
     [MessageHeader]
     public SomeProtocol ProtocolHeader;
     [MessageBody]
     public Item Content;
}

[ServiceContract]
public interface IItemService
{
     [OperationContract]
     public void DeliverItem(ItemMessage itemMessage);
}
```

Cette syntaxe génère une représentation explicite de la structure des messages, alors que la structure des messages est impliquée par le code d'un service Web ASP.NET. En outre, dans la syntaxe ASP.NET, les en-têtes de message sont représentés comme des propriétés du service, telles que la `ProtocolHeader` propriété dans l’exemple précédent, tandis que dans la syntaxe WCF, elles sont représentées plus précisément comme des propriétés de messages. WCF permet également d’ajouter des en-têtes de message à la configuration des points de terminaison.

```xml
<service name="Service ">
     <endpoint
      address="EchoService"
      binding="basicHttpBinding"
      contract="IEchoService ">
      <headers>
      <dsig:X509Certificate
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">
       ...
      </dsig:X509Certificate>
      </headers>
     </endpoint>
</service>
```

Cette option vous permet d'éviter toute référence aux en-têtes de protocole d'infrastructure dans le code pour un client ou un service : les en-têtes sont ajoutés aux messages selon le mode de configuration du point de terminaison.

## <a name="service-description"></a>Description du service

L'émission d'une demande HTTP GET pour le fichier .asmx d'un service Web ASP.NET avec la requête WSDL entraîne la génération de WSDL par ASP.NET pour décrire le service. Il retourne ce WSDL en réponse à la demande.

ASP.NET 2.0 permet de valider la conformité d'un service avec Basic Profile 1.1 de Web Services-Interoperability Organization (WS-I), et d'insérer une revendication que le service est conforme dans son WSDL. Cette opération est effectuée à l'aide des paramètres `ConformsTo` et `EmitConformanceClaims` de l'attribut <xref:System.Web.Services.WebServiceBindingAttribute>.

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

Le WSDL généré par ASP.NET pour un service peut être personnalisé. Les personnalisations s'effectuent en créant une classe dérivée de <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> pour ajouter des éléments au WSDL.

L’émission d’une requête HTTP-HTTP avec la requête WSDL pour le fichier. svc d’un service WCF avec un point de terminaison HTTP hébergé dans IIS 51, 6,0 ou WAS a pour effet que WCF répondait avec WSDL pour décrire le service. L'émission d'une demande HTTP GET avec la requête WSDL à l'adresse de base HTTP d'un service hébergé dans une application .NET a le même effet si httpGetEnabled a la valeur true.

Toutefois, WCF répond également aux demandes WS-MetadataExchange avec WSDL qu’il génère pour décrire un service. Les services Web ASP.NET n'offrent pas de prise en charge intégrée pour les demandes WS-MetadataExchange.

Le WSDL généré par WCF peut être largement personnalisé. La classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> fournit des fonctions pour personnaliser le WSDL. Le WCF peut également être configuré pour ne pas générer WSDL, mais plutôt pour utiliser un fichier WSDL statique à une URL donnée.

```xml
<behaviors>
     <behavior name="DescriptionBehavior">
     <metadataPublishing
      enableMetadataExchange="true"
      enableGetWsdl="true"
      enableHelpPage="true"
      metadataLocation=
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>
     </behavior>
</behaviors>
```

## <a name="exception-handling"></a>Gestion des exceptions

Dans les services Web ASP.NET, les exceptions non prises en charge sont retournées aux clients comme des erreurs SOAP. Vous pouvez aussi lever explicitement des instances de la classe <xref:System.Web.Services.Protocols.SoapException> et avoir plus de contrôle sur le contenu de l'erreur SOAP transmise au client.

Dans les services WCF, les exceptions non gérées ne sont pas retournées aux clients en tant qu’erreurs SOAP pour empêcher les informations sensibles d’être exposées par inadvertance par le biais des exceptions. Un paramètre de configuration est fourni pour que les exceptions non prises en charge soient retournées aux clients à des fins de débogage.

Pour retourner des erreurs SOAP aux clients, vous pouvez lever des instances du type générique, <xref:System.ServiceModel.FaultException%601>, à l'aide du type de contrat de données comme type générique. Vous pouvez aussi ajouter des attributs <xref:System.ServiceModel.FaultContractAttribute> aux opérations pour spécifier les erreurs qu'une opération peut générer.

```csharp
[DataContract]
public class MathFault
{
     [DataMember]
     public string operation;
     [DataMember]
     public string problemType;
}

[ServiceContract]
public interface ICalculator
{
     [OperationContract]
     [FaultContract(typeof(MathFault))]
     int Divide(int n1, int n2);
}
```

Cette opération entraîne la publication des erreurs possibles dans le WSDL pour le service, ce qui permet aux programmeurs du client d‘anticiper sur les erreurs possibles à l‘issue d‘une opération, et d‘écrire les instructions catch appropriées.

```csharp
try
{
     result = client.Divide(value1, value2);
}
catch (FaultException<MathFault> e)
{
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "
  + e.Detail.operation
  + ". Problem: "
  + e.Detail.problemType);
}
```

## <a name="state-management"></a>Gestion des états

La classe utilisée pour implémenter un service Web ASP.NET peut être dérivée de <xref:System.Web.Services.WebService>.

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

Dans ce cas, la classe peut être programmée pour utiliser la propriété Context de la classe de base <xref:System.Web.Services.WebService> pour accéder à un objet <xref:System.Web.HttpContext>. L'objet <xref:System.Web.HttpContext> peut être utilisé pour mettre à jour et récupérer des informations d'état d'application en utilisant sa propriété Application, et pour mettre à jour et récupérer des informations d'état de session en utilisant sa propriété Session.

ASP.NET permet un contrôle important sur l'emplacement de stockage réel des informations d'état de session accessibles à l'aide de la propriété Session du <xref:System.Web.HttpContext>. Elles peuvent être stockées dans des cookies, une base de données, la mémoire du serveur actuel ou la mémoire d'un serveur désigné. Le choix s'opère dans le fichier de configuration du service.

WCF fournit des objets extensibles pour la gestion des États. Les objets extensibles sont des objets qui implémentent <xref:System.ServiceModel.IExtensibleObject%601>. Les objets extensibles les plus importants sont <xref:System.ServiceModel.ServiceHostBase> et <xref:System.ServiceModel.InstanceContext>. `ServiceHostBase` vous permet de maintenir l'état accessible par toutes les instances de tous les types de services sur le même hôte, alors que `InstanceContext` vous permet de maintenir l'état accessible par tout code s'exécutant dans la même instance d'un type de service.

Ici, le type de service, `TradingSystem` , a un <xref:System.ServiceModel.ServiceBehaviorAttribute> qui spécifie que tous les appels de la même instance de client WCF sont acheminés vers la même instance du type de service.

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

La classe, `DealData`, définit l'état accessible par tout code qui s'exécute dans la même instance d'un type de service.

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

Dans le code du type de service qui implémente l'une des opérations du contrat de service, un objet d'état `DealData` est ajouté à l'état de l'instance actuelle du type de service.

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

Cet objet d'état peut être ensuite récupéré et modifié par le code qui implémente une autre opération des opérations du contrat de service.

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

Tandis que ASP.NET permet de contrôler l’emplacement où les informations d’État dans la <xref:System.Web.HttpContext> classe sont réellement stockées, WCF, au moins dans sa version initiale, ne fournit aucun contrôle sur l’emplacement de stockage des objets extensibles. Cela constitue la meilleure raison de sélectionner le mode de compatibilité ASP.NET pour un service WCF. Si la gestion d'état configurable est impérative, choisir ensuite le mode de compatibilité ASP.NET vous permet d'utiliser les fonctions de la classe <xref:System.Web.HttpContext> exactement telles qu'elles sont utilisées dans ASP.NET, et de configurer aussi l'emplacement de stockage des informations d'état gérées à l'aide de la classe <xref:System.Web.HttpContext>.

## <a name="security"></a>Sécurité

Les options permettant de sécuriser les services Web ASP.NET sont celles qui permettent de sécuriser toute application IIS. Étant donné que les applications WCF peuvent être hébergées non seulement dans IIS, mais également dans n’importe quel exécutable .NET, les options de sécurisation des applications WCF doivent être indépendantes des fonctionnalités d’IIS. Toutefois, les fonctionnalités fournies pour les services Web ASP.NET sont également disponibles pour les services WCF qui s’exécutent en mode de compatibilité ASP.NET.

### <a name="security-authentication"></a>Sécurité : authentification

Les services IIS fournissent des fonctions de contrôle de l’accès aux applications qui permettent de sélectionner un accès anonyme ou un ensemble de modes d’authentification : l’authentification Windows, l’authentification Digest, l’authentification de base et l’authentification .NET Passport. L'option d'authentification Windows peut être utilisée pour contrôler l'accès aux services Web ASP.NET. Toutefois, lorsque les applications WCF sont hébergées dans IIS, IIS doit être configuré pour autoriser l’accès anonyme à l’application, afin que l’authentification puisse être gérée par WCF, qui prend en charge l’authentification Windows parmi d’autres options. Les autres options intégrées incluent les jetons de nom d'utilisateur, les certificats X.509, les jetons SAML et la carte CardSpace, mais il est possible de définir aussi des mécanismes d'authentification personnalisés.

### <a name="security-impersonation"></a>Sécurité : emprunt d'identité

ASP.NET fournit un élément d'identité qui permet à un service Web ASP.NET d'emprunter à un utilisateur particulier son identité ou les informations d'identification de l'utilisateur fournies dans la demande actuelle. Cet élément peut être utilisé pour configurer l’emprunt d’identité dans les applications WCF s’exécutant en mode de compatibilité ASP.NET.

Le système de configuration WCF fournit son propre élément Identity pour désigner un utilisateur particulier dont l’identité doit être empruntée. En outre, les clients et services WCF peuvent être configurés indépendamment pour l’emprunt d’identité. Les clients peuvent être configurés pour emprunter l'identité de l'utilisateur actuel lorsqu'ils transmettent des demandes.

```xml
<behaviors>
     <behavior name="DerivativesCalculatorClientBehavior">
      <clientCredentials>
      <windows allowedImpersonationLevel="Impersonation"/>
      </clientCredentials>
     </behavior>
</behaviors>
```

Les opérations de service peuvent être configurées pour emprunter les informations d'identification de l'utilisateur qui fourni la demande actuelle.

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a>Sécurité : autorisation à l'aide des listes de contrôle d'accès

Les listes de contrôle d'accès (ACL) peuvent être utilisées pour restreindre l'accès aux fichiers .asmx. Toutefois, les listes de contrôle d’accès des fichiers. svc WCF sont ignorées, sauf en mode de compatibilité ASP.NET.

### <a name="security-role-based-authorization"></a>Sécurité : autorisation basée sur les rôles

L'option d'authentification IIS Windows peut être utilisée conjointement avec l'élément d'autorisation fourni par le langage de configuration ASP.NET pour faciliter l'autorisation basée sur les rôles pour les services Web ASP.NET selon les groupes Windows auxquels les utilisateurs sont assignés. ASP.NET 2.0 introduit un mécanisme plus général d'autorisation basée sur les rôles : les fournisseurs de rôles.

Les fournisseurs de rôles sont des classes qui implémentent toutes une interface de base pour s'informer des rôles auxquels un utilisateur est assigné, mais chaque fournisseur de rôle sait comment récupérer ces information issues d'une source différente. ASP.NET 2.0 fournit un fournisseur de rôles qui peut récupérer des affectations de rôle d'une base de données Microsoft SQL Server, ainsi qu'un autre fournisseur qui peut récupérer des affectations de rôles issues du Gestionnaire d'autorisations Windows Server 2003.

Le mécanisme de fournisseur de rôle peut en fait être utilisé indépendamment de ASP.NET dans n’importe quelle application .NET, y compris une application WCF. L’exemple de configuration suivant pour une application WCF montre comment l’utilisation d’un fournisseur de rôle ASP.NET est une option sélectionnée au moyen du <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> .

```xml
<system.serviceModel>
     <services>
         <service name="Service.ResourceAccessServiceType"
             behaviorConfiguration="ServiceBehavior">
             <endpoint
              address="ResourceAccessService"
              binding="wsHttpBinding"
              contract="Service.IResourceAccessContract"/>
         </service>
     </services>
     <behaviors>
       <behavior name="ServiceBehavior">
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>
      </behavior>
     </behaviors>
</system.serviceModel>
```

### <a name="security-claims-based-authorization"></a>Sécurité : autorisation basée sur les revendications

L’une des innovations les plus importantes de WCF est sa prise en charge complète pour autoriser l’accès aux ressources protégées basées sur les revendications. Les revendications se composent d'un type, d'un droit et d'une valeur, un permis de conduire, par exemple. Elle produit un jeu de revendications relatives au porteur, dont l'une d'entre elles est la date de naissance du porteur. Le type de cette revendication est la date de naissance, la valeur de la revendication est la date de naissance du conducteur. Le droit que confère une revendication au porteur spécifie ce que le porteur peut faire avec la valeur de la revendication. Dans le cas de la revendication de la date de naissance du conducteur, ce droit est la propriété : le conducteur possède cette date de naissance mais il ne peut pas, par exemple, la modifier. L'autorisation basée sur les revendications intègre l'autorisation basée sur les rôles, parce que les rôles sont un type de revendication.

L'autorisation basée sur les revendications s'accomplit en comparant un jeu de revendications aux spécifications d'accès de l'opération et, selon le résultat de cette comparaison, l'accès à l'opération est accordé ou refusé. Dans WCF, vous pouvez spécifier une classe à utiliser pour exécuter l’autorisation basée sur les revendications, une fois encore, en affectant une valeur à la `ServiceAuthorizationManager` propriété de <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> .

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

Les classes utilisées pour exécuter l'autorisation basée sur les revendications doivent dériver de <xref:System.ServiceModel.ServiceAuthorizationManager>, qui contient une méthode à substituer, `AccessCheck()`. WCF appelle cette méthode chaque fois qu’une opération du service est appelée et fournit un <xref:System.ServiceModel.OperationContext> objet, qui a les revendications pour l’utilisateur dans sa `ServiceSecurityContext.AuthorizationContext` propriété. WCF effectue le travail d’assemblage des revendications relatives à l’utilisateur à partir du jeton de sécurité fourni par l’utilisateur pour l’authentification, ce qui laisse la tâche d’évaluer si ces revendications suffisent pour l’opération en question.

WCF assemble automatiquement les revendications à partir de n’importe quel type de jeton de sécurité est une innovation très importante, car elle rend le code d’autorisation basé sur les revendications entièrement indépendantes du mécanisme d’authentification. Par contraste, l'autorisation à l'aide des listes de contrôle d'accès ou des rôles dans ASP.NET est étroitement liée à l'authentification Windows.

### <a name="security-confidentiality"></a>Sécurité : confidentialité

La confidentialité des messages échangés avec les services Web ASP.NET peut être garantie au niveau du transport en configurant l'application dans les services IIS pour qu'elle utilise le protocole HTTPS (Secure Hypertext Transfer Protocol). Il en est de même pour les applications WCF hébergées dans IIS. Toutefois, les applications WCF hébergées en dehors d’IIS peuvent également être configurées pour utiliser un protocole de transport sécurisé. Plus important, les applications WCF peuvent également être configurées pour sécuriser les messages avant leur transport, à l’aide du protocole WS-Security. La sécurisation uniquement du corps d'un message à l'aide de WS-Security lui permet d'être transmis confidentiellement par des intermédiaires avant d'atteindre sa destination finale.

## <a name="globalization"></a>Globalisation

Le langage de configuration ASP.NET vous permet de spécifier la culture pour les services individuels. WCF ne prend pas en charge ce paramètre de configuration, sauf en mode de compatibilité ASP.NET. Pour localiser un service WCF qui n’utilise pas le mode de compatibilité ASP.NET, compilez le type de service dans des assemblys spécifiques à la culture et avez des points de terminaison spécifiques à la culture distincts pour chaque assembly spécifique à la culture.

## <a name="see-also"></a>Voir aussi

- [Comparaison des services Web ASP.NET et de WCF en fonction de l'objectif et des normes utilisées](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
