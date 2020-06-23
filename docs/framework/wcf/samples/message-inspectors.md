---
title: Message Inspectors
description: Découvrez comment implémenter et configurer des inspecteurs de messages de service et de client WCF, qui fournissent un mécanisme de validation des messages.
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 20abb655a58f9dce4a967ade9b51db90eed2375b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246205"
---
# <a name="message-inspectors"></a>Message Inspectors
Cet exemple montre comment implémenter et configurer des inspecteurs de message de service et client.  
  
 Un inspecteur de message est un objet d'extensibilité qui peut être utilisé dans l'exécution du répartiteur et du client du modèle de service par programme ou via la configuration, et qui peut inspecter et modifier des messages après leur réception ou avant leur envoi.  
  
 Cet exemple implémente un mécanisme de base de validation de message de service et client qui valide des messages entrants par rapport à un ensemble de documents XML Schema configurables. Notez que cet exemple ne valide pas les messages de chaque opération. Il s'agit d'une simplification intentionnelle.  
  
## <a name="message-inspector"></a>Inspecteur de message  
 Les inspecteurs de message client et de service implémentent respectivement l'interface <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> et l'interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector>. Les implémentations peuvent être combinées dans une classe unique pour former un inspecteur de message qui fonctionne pour les deux côtés. Cet exemple implémente un inspecteur de message combiné de ce type. L'inspecteur est construit en passant un jeu de schémas par rapport auquel les messages entrants et sortants sont validés. Il permet au développeur de spécifier si les messages entrants ou sortants sont validés et si l'inspecteur est en mode client ou répartiteur, ce qui affecte la gestion des erreurs tel que développé ultérieurement dans cette rubrique.  
  
```csharp
public class SchemaValidationMessageInspector : IClientMessageInspector, IDispatchMessageInspector  
{  
    XmlSchemaSet schemaSet;  
    bool validateRequest;  
    bool validateReply;  
    bool isClientSide;  
    [ThreadStatic]  
    bool isRequest;  
  
    public SchemaValidationMessageInspector(XmlSchemaSet schemaSet,  
         bool validateRequest, bool validateReply, bool isClientSide)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = validateReply;  
        this.validateRequest = validateRequest;  
        this.isClientSide = isClientSide;  
    }  
```  
  
 Tout inspecteur de message (répartiteur) de service doit implémenter les deux méthodes <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> et <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> est appelé par le répartiteur lorsqu'un message a été reçu, traité par la pile de canaux et assigné à un service, mais avant qu'il soit désérialisé et distribué à une opération. Si le message entrant a été chiffré, le message est déjà déchiffré lorsqu'il atteint l'inspecteur de message. La méthode obtient le message `request` passé comme paramètre de référence, qui autorise le message à être inspecté, manipulé ou remplacé selon les besoins. La valeur de retour peut être n'importe quel objet et est utilisée comme objet d'état de corrélation passé à <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> lorsque le service retourne une réponse au message actuel. Dans cet exemple, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> délègue l'inspection (validation) du message à la méthode locale privée `ValidateMessageBody` et ne retourne pas d'objet d'état de corrélation. Cette méthode garantit qu'aucun message non valide ne passe dans le service.  
  
```csharp  
object IDispatchMessageInspector.AfterReceiveRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel, System.ServiceModel.InstanceContext instanceContext)  
{  
    if (validateRequest)  
    {  
        // inspect the message. If a validation error occurs,  
        // the thrown fault exception bubbles up.  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> est appelé chaque fois qu'une réponse est prête à être renvoyée à un client, ou dans le cas de messages unidirectionnels, lorsque le message entrant a été traité. Cela permet aux extensions d'être appelées symétriquement, indépendamment du MEP utilisé. Comme avec <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, le message est passé comme paramètre de référence et peut être inspecté, modifié ou remplacé. La validation du message effectuée dans cet exemple est de nouveau déléguée à la méthode `ValidMessageBody`, mais la gestion des erreurs de validation diffère légèrement dans ce cas.  
  
 Si une erreur de validation se produit sur le service, la méthode `ValidateMessageBody` lève <xref:System.ServiceModel.FaultException> (exceptions dérivées). Dans <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, ces exceptions peuvent être placées dans l'infrastructure de modèle de service où elles sont automatiquement transformées en erreurs SOAP et relayées au client. Dans <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, les exceptions <xref:System.ServiceModel.FaultException> ne doivent pas être placées dans l'infrastructure, car la transformation des exceptions levées par le service se produit avant l'appel de l'inspecteur de message. Par conséquent, l'implémentation suivante intercepte l'exception `ReplyValidationFault` connue et remplace le message de réponse par un message d'erreur explicite. Cette méthode garantit qu'aucun message non valide n'est retourné par l'implémentation de service.  
  
```csharp  
void IDispatchMessageInspector.BeforeSendReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        // Inspect the reply, catch a possible validation error
        try  
        {  
            ValidateMessageBody(ref reply, false);  
        }  
        catch (ReplyValidationFault fault)  
        {  
            // if a validation error occurred, the message is replaced  
            // with the validation fault.  
            reply = Message.CreateMessage(reply.Version,
                    fault.CreateMessageFault(), reply.Headers.Action);  
        }  
    }  
```  
  
 L'inspecteur de message client est très semblable. Les deux méthodes qui doivent être implémentées à partir de <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> sont <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> et <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> est appelé lorsque le message a été composé par l'application cliente ou par le module de formatage de l'opération. Comme avec les inspecteurs de message de répartiteur, le message peut être simplement inspecté ou être entièrement remplacé. Dans cet exemple, l'inspecteur délègue à la même méthode d'assistance locale `ValidateMessageBody` qui est également utilisée pour les inspecteurs de message de répartiteur.  
  
 La différence de comportement entre la validation du client et du service (tel que spécifié dans le constructeur) est que la validation du client lève des exceptions locales qui sont placées dans le code utilisateur car elles se produisent localement et non pas à cause d’un échec du service. En général, la règle veut que les inspecteurs de répartiteur de service génèrent des erreurs et que les inspecteurs de client lèvent des exceptions.  
  
 L'implémentation <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> garantit qu'aucun message non valide n'est envoyé au service.  
  
```csharp  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 L'implémentation `AfterReceiveReply` garantit qu'aucun message non valide reçu du service n'est relayé au code utilisateur client.  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 Le cœur de cet inspecteur de message spécifique est la méthode `ValidateMessageBody`. Pour effectuer son travail, elle encapsule un <xref:System.Xml.XmlReader> de validation autour du sous-arbre du contenu du corps du message passé. Le lecteur est rempli avec le jeu de schémas géré par l'inspecteur de message et le rappel de validation a pour valeur un délégué qui fait référence au `InspectionValidationHandler` défini avec cette méthode. Pour effectuer la validation, le message est ensuite lu et mis en attente dans un <xref:System.Xml.XmlDictionaryWriter> reposant sur un flux de mémoire. Si un avertissement ou une erreur de validation se produit dans le processus, la méthode de rappel est appelée.  
  
 Si aucune erreur ne se produit, un nouveau message est construit : il copie les propriétés ainsi que les en-têtes du message d'origine et utilise l'infoset maintenant validé dans le flux de mémoire, lequel est encapsulé par un <xref:System.Xml.XmlDictionaryReader> et ajouté au message de remplacement.  
  
```csharp  
void ValidateMessageBody(ref System.ServiceModel.Channels.Message message, bool isRequest)  
{  
    if (!message.IsFault)  
    {  
        XmlDictionaryReaderQuotas quotas =
                new XmlDictionaryReaderQuotas();  
        XmlReader bodyReader =
            message.GetReaderAtBodyContents().ReadSubtree();  
        XmlReaderSettings wrapperSettings =
                              new XmlReaderSettings();  
        wrapperSettings.CloseInput = true;  
        wrapperSettings.Schemas = schemaSet;  
        wrapperSettings.ValidationFlags =
                                XmlSchemaValidationFlags.None;  
        wrapperSettings.ValidationType = ValidationType.Schema;  
        wrapperSettings.ValidationEventHandler += new
           ValidationEventHandler(InspectionValidationHandler);  
        XmlReader wrappedReader = XmlReader.Create(bodyReader,
                                            wrapperSettings);  
  
        // pull body into a memory backed writer to validate  
        this.isRequest = isRequest;  
        MemoryStream memStream = new MemoryStream();  
        XmlDictionaryWriter xdw =  
              XmlDictionaryWriter.CreateBinaryWriter(memStream);  
        xdw.WriteNode(wrappedReader, false);  
        xdw.Flush(); memStream.Position = 0;  
        XmlDictionaryReader xdr =
        XmlDictionaryReader.CreateBinaryReader(memStream, quotas);  
  
        // reconstruct the message with the validated body  
        Message replacedMessage =
            Message.CreateMessage(message.Version, null, xdr);  
        replacedMessage.Headers.CopyHeadersFrom(message.Headers);  
        replacedMessage.Properties.CopyProperties(message.Properties);  
        message = replacedMessage;  
    }  
}  
```  
  
 La méthode `InspectionValidationHandler` est appelée par le <xref:System.Xml.XmlReader> de validation chaque fois qu’un avertissement ou qu’une erreur de validation du schéma se produit. L'implémentation suivante fonctionne uniquement avec les erreurs et ignore tous les avertissements.  
  
 À première vue, il peut sembler possible d’injecter un <xref:System.Xml.XmlReader> de validation dans le message avec l’inspecteur de message et de laisser la validation se produire pendant le traitement du message sans avoir à le mettre en mémoire tampon. Toutefois, cela signifie que ce rappel lève les exceptions de validation quelque part dans l’infrastructure de modèle de service ou le code utilisateur car des nœuds XML non valides sont détectés, ce qui provoque un comportement imprévisible. L'approche de mise en mémoire tampon protège l'ensemble du code utilisateur contre les messages non valides.  
  
 Comme indiqué précédemment, les exceptions levées par le gestionnaire diffèrent entre le client et le service. Sur le service, les exceptions sont dérivées de <xref:System.ServiceModel.FaultException> ; sur le client, il s'agit d'exceptions personnalisées normales.  
  
```csharp  
        void InspectionValidationHandler(object sender, ValidationEventArgs e)  
{  
    if (e.Severity == XmlSeverityType.Error)  
    {  
        // We are treating client and service side validation errors  
        // differently here. Client side errors cause exceptions  
        // and are thrown straight up to the user code. Service side  
        // validations cause faults.  
        if (isClientSide)  
        {  
            if (isRequest)  
            {  
                throw new RequestClientValidationException(e.Message);  
            }  
            else  
            {  
                throw new ReplyClientValidationException(e.Message);  
            }  
        }  
        else  
        {  
            if (isRequest)  
            {  
                // this fault is caught by the ServiceModel
                // infrastructure and turned into a fault reply.  
                throw new RequestValidationFault(e.Message);  
             }  
             else  
             {  
                // this fault is caught and turned into a fault message  
                // in BeforeSendReply in this class  
                throw new ReplyValidationFault(e.Message);  
              }  
          }  
      }  
    }  
```  
  
## <a name="behavior"></a>Comportement  
 Les inspecteurs de message sont des extensions vers l'exécution du client ou du répartiteur. Ces extensions sont configurées à l’aide de *comportements*. Un comportement est une classe qui change le comportement de l’exécution de modèle de service en modifiant la configuration par défaut ou en lui ajoutant des extensions (telles que des inspecteurs de message).  
  
 La classe `SchemaValidationBehavior` suivante est le comportement utilisé pour ajouter l'inspecteur de message de cet exemple à l'exécution du client ou du répartiteur. L'implémentation est plutôt basique dans les deux cas. Dans <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> et <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, l'inspecteur de message est créé et ajouté à la collection <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> de l'exécution respective.  
  
```csharp
public class SchemaValidationBehavior : IEndpointBehavior  
{  
    XmlSchemaSet schemaSet;
    bool validateRequest;
    bool validateReply;  
  
    public SchemaValidationBehavior(XmlSchemaSet schemaSet, bool
                           inspectRequest, bool inspectReply)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = inspectReply;  
        this.validateRequest = inspectRequest;  
    }  
    #region IEndpointBehavior Members  
  
    public void AddBindingParameters(ServiceEndpoint endpoint,
       System.ServiceModel.Channels.BindingParameterCollection
                                            bindingParameters)  
    {  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint,
            System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
    {  
        SchemaValidationMessageInspector inspector =
           new SchemaValidationMessageInspector(schemaSet,
                      validateRequest, validateReply, true);  
            clientRuntime.MessageInspectors.Add(inspector);  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint,
         System.ServiceModel.Dispatcher.EndpointDispatcher
                                          endpointDispatcher)  
    {  
        SchemaValidationMessageInspector inspector =
           new SchemaValidationMessageInspector(schemaSet,
                        validateRequest, validateReply, false);  
   endpointDispatcher.DispatchRuntime.MessageInspectors.Add(inspector);  
    }  
  
   public void Validate(ServiceEndpoint endpoint)  
   {  
   }  
  
    #endregion  
}  
```  
  
> [!NOTE]
> Ce comportement spécifique ne joue pas le rôle d'attribut et, par conséquent, ne peut pas être ajouté de façon déclarative sur un type de contrat d'un type de service. Cette décision de conception a été prise car la collection de schémas ne peut pas être chargée dans une déclaration attribute, et faire référence à un emplacement de configuration supplémentaire (par exemple aux paramètres d’application) dans cet attribut revient à créer un élément de configuration qui n’est pas cohérent avec le reste de la configuration de modèle de service. Par conséquent, ce comportement peut uniquement être ajouté de façon impérative via le code et une extension de configuration de modèle de service.  
  
## <a name="adding-the-message-inspector-through-configuration"></a>Ajout de l'inspecteur de message via la configuration  
 Pour configurer un comportement personnalisé sur un point de terminaison dans le fichier de configuration de l’application, le modèle de service requiert des implémenteurs pour créer un *élément d’extension* de configuration représenté par une classe dérivée de <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> . Cette extension doit être ensuite ajoutée à la section de configuration du modèle de service pour les extensions, tel qu’indiqué pour l’extension suivante traitée dans cette section.  
  
```xml  
<system.serviceModel>  
…  
   <extensions>  
      <behaviorExtensions>  
        <add name="schemaValidator" type="Microsoft.ServiceModel.Samples.SchemaValidationBehaviorExtensionElement, MessageInspectors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
      </behaviorExtensions>  
    </extensions>  
…  
</system.serviceModel>  
```  
  
 Des extensions peuvent être ajoutées dans le fichier de configuration de l'application ou ASP.NET (ce qui est le choix le plus courant), ou bien dans le fichier de configuration de l'ordinateur.  
  
 Lorsque l’extension est ajoutée à une étendue de configuration, le comportement peut être ajouté à une configuration de comportement, tel qu’indiqué dans le code suivant. Les configurations de comportement sont des éléments réutilisables qui peuvent être appliqués à plusieurs points de terminaison selon les besoins. Le comportement spécifique à configurer dans ce cas implémentant <xref:System.ServiceModel.Description.IEndpointBehavior>, il est uniquement valide dans la section de configuration respective du fichier de configuration.  
  
```xml  
<system.serviceModel>  
   <behaviors>  
      …  
     <endpointBehaviors>  
        <behavior name="HelloServiceEndpointBehavior">  
          <schemaValidator validateRequest="True" validateReply="True">  
            <schemas>  
              <add location="messages.xsd" />
            </schemas>  
          </schemaValidator>  
        </behavior>  
      </endpointBehaviors>  
      …  
    </behaviors>  
</system.serviceModel>  
```  
  
 L'élément `<schemaValidator>` qui configure l'inspecteur de message est soutenu par la classe `SchemaValidationBehaviorExtensionElement`. La classe expose deux propriétés publiques booléennes appelées `ValidateRequest` et `ValidateReply`. Elles sont marquées avec <xref:System.Configuration.ConfigurationPropertyAttribute>. Cet attribut constitue le lien entre les propriétés de code et les attributs XML qui peuvent être observés sur l'élément de configuration XML précédent. La classe possède également la propriété `Schemas` qui est en outre marquée avec <xref:System.Configuration.ConfigurationCollectionAttribute> et qui est du type `SchemaCollection`, lequel fait également partie de cet exemple mais a été omis de ce document pour des raisons de concision. Cette propriété, ainsi que la collection et la classe d'élément de collection `SchemaConfigElement`, soutient l'élément `<schemas>` dans l'extrait de code de configuration précédent et permet d'ajouter une collection de schémas à l'ensemble de validation.  
  
 La méthode `CreateBehavior` substituée change les données de configuration en objet de comportement lorsque l'exécution évalue les données de configuration car elle génère un client ou un point de terminaison.  
  
```csharp
public class SchemaValidationBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public SchemaValidationBehaviorExtensionElement()  
    {  
    }  
  
    public override Type BehaviorType
    {
        get  
        {  
            return typeof(SchemaValidationBehavior);  
        }
    }  
  
    protected override object CreateBehavior()  
    {  
        XmlSchemaSet schemaSet = new XmlSchemaSet();  
        foreach (SchemaConfigElement schemaCfg in this.Schemas)  
        {  
            Uri baseSchema = new
                Uri(AppDomain.CurrentDomain.BaseDirectory);  
            string location = new
                Uri(baseSchema,schemaCfg.Location).ToString();  
            XmlSchema schema =
                XmlSchema.Read(new XmlTextReader(location), null);  
            schemaSet.Add(schema);  
        }  
     return new
     SchemaValidationBehavior(schemaSet,ValidateRequest,ValidateReply);  
    }  
  
[ConfigurationProperty("validateRequest",DefaultValue=false,IsRequired=false)]  
public bool ValidateRequest  
{  
    get { return (bool)base["validateRequest"]; }  
    set { base["validateRequest"] = value; }  
}  
  
[ConfigurationProperty("validateReply", DefaultValue = false, IsRequired = false)]  
        public bool ValidateReply  
        {  
            get { return (bool)base["validateReply"]; }  
            set { base["validateReply"] = value; }  
        }  
  
     //Declare the Schema collection property.  
     //Note: the "IsDefaultCollection = false" instructs
     //.NET Framework to build a nested section of
     //the kind <Schema> ...</Schema>.  
    [ConfigurationProperty("schemas", IsDefaultCollection = true)]  
    [ConfigurationCollection(typeof(SchemasCollection),  
        AddItemName = "add",  
        ClearItemsName = "clear",  
        RemoveItemName = "remove")]  
    public SchemasCollection Schemas  
    {  
        get  
        {  
            SchemasCollection SchemasCollection =  
            (SchemasCollection)base["schemas"];  
            return SchemasCollection;  
        }  
    }  
}  
```  
  
## <a name="adding-message-inspectors-imperatively"></a>Ajout d'inspecteurs de message de façon impérative  
 Excepté via les attributs (approche qui n'est pas prise en charge dans cet exemple pour la raison précédemment citée) et la configuration, des comportements peuvent être assez facilement ajoutés à une exécution de client et de service à l'aide de code impératif. Dans cet exemple, cette opération s'effectue dans l'application cliente afin de tester l'inspecteur de message client. La classe `GenericClient` est dérivée de <xref:System.ServiceModel.ClientBase%601>, qui expose la configuration de point de terminaison au code utilisateur. Avant que le client ne soit implicitement ouvert, la configuration de point de terminaison peut être modifiée, par exemple en ajoutant des comportements tel qu'indiqué dans le code suivant. L'ajout du comportement sur le service est en grande partie équivalent à la technique du client présentée ici et doit être effectué avant que l'hôte de service ne soit ouvert.  
  
```csharp  
try  
{  
    Console.WriteLine("*** Call 'Hello' with generic client, with client behavior");  
    GenericClient client = new GenericClient();  
  
    // Configure client programmatically, adding behavior  
    XmlSchema schema = XmlSchema.Read(new StreamReader("messages.xsd"),
                                                          null);  
    XmlSchemaSet schemaSet = new XmlSchemaSet();  
    schemaSet.Add(schema);  
    client.Endpoint.Behaviors.Add(new
                SchemaValidationBehavior(schemaSet, true, true));  
  
    Console.WriteLine("--- Sending valid client request:");  
    GenericCallValid(client, helloAction);  
    Console.WriteLine("--- Sending invalid client request:");  
    GenericCallInvalid(client, helloAction);  
  
    client.Close();  
}  
catch (Exception e)  
{  
    DumpException(e);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
