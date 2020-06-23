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
# <a name="message-inspectors"></a><span data-ttu-id="dd45a-103">Message Inspectors</span><span class="sxs-lookup"><span data-stu-id="dd45a-103">Message Inspectors</span></span>
<span data-ttu-id="dd45a-104">Cet exemple montre comment implémenter et configurer des inspecteurs de message de service et client.</span><span class="sxs-lookup"><span data-stu-id="dd45a-104">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="dd45a-105">Un inspecteur de message est un objet d'extensibilité qui peut être utilisé dans l'exécution du répartiteur et du client du modèle de service par programme ou via la configuration, et qui peut inspecter et modifier des messages après leur réception ou avant leur envoi.</span><span class="sxs-lookup"><span data-stu-id="dd45a-105">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="dd45a-106">Cet exemple implémente un mécanisme de base de validation de message de service et client qui valide des messages entrants par rapport à un ensemble de documents XML Schema configurables.</span><span class="sxs-lookup"><span data-stu-id="dd45a-106">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="dd45a-107">Notez que cet exemple ne valide pas les messages de chaque opération.</span><span class="sxs-lookup"><span data-stu-id="dd45a-107">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="dd45a-108">Il s'agit d'une simplification intentionnelle.</span><span class="sxs-lookup"><span data-stu-id="dd45a-108">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="dd45a-109">Inspecteur de message</span><span class="sxs-lookup"><span data-stu-id="dd45a-109">Message Inspector</span></span>  
 <span data-ttu-id="dd45a-110">Les inspecteurs de message client et de service implémentent respectivement l'interface <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> et l'interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector>.</span><span class="sxs-lookup"><span data-stu-id="dd45a-110">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="dd45a-111">Les implémentations peuvent être combinées dans une classe unique pour former un inspecteur de message qui fonctionne pour les deux côtés.</span><span class="sxs-lookup"><span data-stu-id="dd45a-111">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="dd45a-112">Cet exemple implémente un inspecteur de message combiné de ce type.</span><span class="sxs-lookup"><span data-stu-id="dd45a-112">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="dd45a-113">L'inspecteur est construit en passant un jeu de schémas par rapport auquel les messages entrants et sortants sont validés. Il permet au développeur de spécifier si les messages entrants ou sortants sont validés et si l'inspecteur est en mode client ou répartiteur, ce qui affecte la gestion des erreurs tel que développé ultérieurement dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="dd45a-113">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
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
  
 <span data-ttu-id="dd45a-114">Tout inspecteur de message (répartiteur) de service doit implémenter les deux méthodes <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> et <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="dd45a-114">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="dd45a-115"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> est appelé par le répartiteur lorsqu'un message a été reçu, traité par la pile de canaux et assigné à un service, mais avant qu'il soit désérialisé et distribué à une opération.</span><span class="sxs-lookup"><span data-stu-id="dd45a-115"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="dd45a-116">Si le message entrant a été chiffré, le message est déjà déchiffré lorsqu'il atteint l'inspecteur de message.</span><span class="sxs-lookup"><span data-stu-id="dd45a-116">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="dd45a-117">La méthode obtient le message `request` passé comme paramètre de référence, qui autorise le message à être inspecté, manipulé ou remplacé selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="dd45a-117">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="dd45a-118">La valeur de retour peut être n'importe quel objet et est utilisée comme objet d'état de corrélation passé à <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> lorsque le service retourne une réponse au message actuel.</span><span class="sxs-lookup"><span data-stu-id="dd45a-118">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="dd45a-119">Dans cet exemple, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> délègue l'inspection (validation) du message à la méthode locale privée `ValidateMessageBody` et ne retourne pas d'objet d'état de corrélation.</span><span class="sxs-lookup"><span data-stu-id="dd45a-119">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="dd45a-120">Cette méthode garantit qu'aucun message non valide ne passe dans le service.</span><span class="sxs-lookup"><span data-stu-id="dd45a-120">This method ensures that no invalid messages pass into the service.</span></span>  
  
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
  
 <span data-ttu-id="dd45a-121"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> est appelé chaque fois qu'une réponse est prête à être renvoyée à un client, ou dans le cas de messages unidirectionnels, lorsque le message entrant a été traité.</span><span class="sxs-lookup"><span data-stu-id="dd45a-121"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="dd45a-122">Cela permet aux extensions d'être appelées symétriquement, indépendamment du MEP utilisé.</span><span class="sxs-lookup"><span data-stu-id="dd45a-122">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="dd45a-123">Comme avec <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, le message est passé comme paramètre de référence et peut être inspecté, modifié ou remplacé.</span><span class="sxs-lookup"><span data-stu-id="dd45a-123">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="dd45a-124">La validation du message effectuée dans cet exemple est de nouveau déléguée à la méthode `ValidMessageBody`, mais la gestion des erreurs de validation diffère légèrement dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="dd45a-124">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="dd45a-125">Si une erreur de validation se produit sur le service, la méthode `ValidateMessageBody` lève <xref:System.ServiceModel.FaultException> (exceptions dérivées).</span><span class="sxs-lookup"><span data-stu-id="dd45a-125">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="dd45a-126">Dans <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, ces exceptions peuvent être placées dans l'infrastructure de modèle de service où elles sont automatiquement transformées en erreurs SOAP et relayées au client.</span><span class="sxs-lookup"><span data-stu-id="dd45a-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="dd45a-127">Dans <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, les exceptions <xref:System.ServiceModel.FaultException> ne doivent pas être placées dans l'infrastructure, car la transformation des exceptions levées par le service se produit avant l'appel de l'inspecteur de message.</span><span class="sxs-lookup"><span data-stu-id="dd45a-127">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="dd45a-128">Par conséquent, l'implémentation suivante intercepte l'exception `ReplyValidationFault` connue et remplace le message de réponse par un message d'erreur explicite.</span><span class="sxs-lookup"><span data-stu-id="dd45a-128">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="dd45a-129">Cette méthode garantit qu'aucun message non valide n'est retourné par l'implémentation de service.</span><span class="sxs-lookup"><span data-stu-id="dd45a-129">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
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
  
 <span data-ttu-id="dd45a-130">L'inspecteur de message client est très semblable.</span><span class="sxs-lookup"><span data-stu-id="dd45a-130">The client message inspector is very similar.</span></span> <span data-ttu-id="dd45a-131">Les deux méthodes qui doivent être implémentées à partir de <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> sont <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> et <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span><span class="sxs-lookup"><span data-stu-id="dd45a-131">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="dd45a-132"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> est appelé lorsque le message a été composé par l'application cliente ou par le module de formatage de l'opération.</span><span class="sxs-lookup"><span data-stu-id="dd45a-132"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="dd45a-133">Comme avec les inspecteurs de message de répartiteur, le message peut être simplement inspecté ou être entièrement remplacé.</span><span class="sxs-lookup"><span data-stu-id="dd45a-133">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="dd45a-134">Dans cet exemple, l'inspecteur délègue à la même méthode d'assistance locale `ValidateMessageBody` qui est également utilisée pour les inspecteurs de message de répartiteur.</span><span class="sxs-lookup"><span data-stu-id="dd45a-134">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="dd45a-135">La différence de comportement entre la validation du client et du service (tel que spécifié dans le constructeur) est que la validation du client lève des exceptions locales qui sont placées dans le code utilisateur car elles se produisent localement et non pas à cause d’un échec du service.</span><span class="sxs-lookup"><span data-stu-id="dd45a-135">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="dd45a-136">En général, la règle veut que les inspecteurs de répartiteur de service génèrent des erreurs et que les inspecteurs de client lèvent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="dd45a-136">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="dd45a-137">L'implémentation <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> garantit qu'aucun message non valide n'est envoyé au service.</span><span class="sxs-lookup"><span data-stu-id="dd45a-137">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
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
  
 <span data-ttu-id="dd45a-138">L'implémentation `AfterReceiveReply` garantit qu'aucun message non valide reçu du service n'est relayé au code utilisateur client.</span><span class="sxs-lookup"><span data-stu-id="dd45a-138">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="dd45a-139">Le cœur de cet inspecteur de message spécifique est la méthode `ValidateMessageBody`.</span><span class="sxs-lookup"><span data-stu-id="dd45a-139">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="dd45a-140">Pour effectuer son travail, elle encapsule un <xref:System.Xml.XmlReader> de validation autour du sous-arbre du contenu du corps du message passé.</span><span class="sxs-lookup"><span data-stu-id="dd45a-140">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="dd45a-141">Le lecteur est rempli avec le jeu de schémas géré par l'inspecteur de message et le rappel de validation a pour valeur un délégué qui fait référence au `InspectionValidationHandler` défini avec cette méthode.</span><span class="sxs-lookup"><span data-stu-id="dd45a-141">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="dd45a-142">Pour effectuer la validation, le message est ensuite lu et mis en attente dans un <xref:System.Xml.XmlDictionaryWriter> reposant sur un flux de mémoire.</span><span class="sxs-lookup"><span data-stu-id="dd45a-142">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="dd45a-143">Si un avertissement ou une erreur de validation se produit dans le processus, la méthode de rappel est appelée.</span><span class="sxs-lookup"><span data-stu-id="dd45a-143">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="dd45a-144">Si aucune erreur ne se produit, un nouveau message est construit : il copie les propriétés ainsi que les en-têtes du message d'origine et utilise l'infoset maintenant validé dans le flux de mémoire, lequel est encapsulé par un <xref:System.Xml.XmlDictionaryReader> et ajouté au message de remplacement.</span><span class="sxs-lookup"><span data-stu-id="dd45a-144">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
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
  
 <span data-ttu-id="dd45a-145">La méthode `InspectionValidationHandler` est appelée par le <xref:System.Xml.XmlReader> de validation chaque fois qu’un avertissement ou qu’une erreur de validation du schéma se produit.</span><span class="sxs-lookup"><span data-stu-id="dd45a-145">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="dd45a-146">L'implémentation suivante fonctionne uniquement avec les erreurs et ignore tous les avertissements.</span><span class="sxs-lookup"><span data-stu-id="dd45a-146">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="dd45a-147">À première vue, il peut sembler possible d’injecter un <xref:System.Xml.XmlReader> de validation dans le message avec l’inspecteur de message et de laisser la validation se produire pendant le traitement du message sans avoir à le mettre en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="dd45a-147">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="dd45a-148">Toutefois, cela signifie que ce rappel lève les exceptions de validation quelque part dans l’infrastructure de modèle de service ou le code utilisateur car des nœuds XML non valides sont détectés, ce qui provoque un comportement imprévisible.</span><span class="sxs-lookup"><span data-stu-id="dd45a-148">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="dd45a-149">L'approche de mise en mémoire tampon protège l'ensemble du code utilisateur contre les messages non valides.</span><span class="sxs-lookup"><span data-stu-id="dd45a-149">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="dd45a-150">Comme indiqué précédemment, les exceptions levées par le gestionnaire diffèrent entre le client et le service.</span><span class="sxs-lookup"><span data-stu-id="dd45a-150">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="dd45a-151">Sur le service, les exceptions sont dérivées de <xref:System.ServiceModel.FaultException> ; sur le client, il s'agit d'exceptions personnalisées normales.</span><span class="sxs-lookup"><span data-stu-id="dd45a-151">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
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
  
## <a name="behavior"></a><span data-ttu-id="dd45a-152">Comportement</span><span class="sxs-lookup"><span data-stu-id="dd45a-152">Behavior</span></span>  
 <span data-ttu-id="dd45a-153">Les inspecteurs de message sont des extensions vers l'exécution du client ou du répartiteur.</span><span class="sxs-lookup"><span data-stu-id="dd45a-153">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="dd45a-154">Ces extensions sont configurées à l’aide de *comportements*.</span><span class="sxs-lookup"><span data-stu-id="dd45a-154">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="dd45a-155">Un comportement est une classe qui change le comportement de l’exécution de modèle de service en modifiant la configuration par défaut ou en lui ajoutant des extensions (telles que des inspecteurs de message).</span><span class="sxs-lookup"><span data-stu-id="dd45a-155">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="dd45a-156">La classe `SchemaValidationBehavior` suivante est le comportement utilisé pour ajouter l'inspecteur de message de cet exemple à l'exécution du client ou du répartiteur.</span><span class="sxs-lookup"><span data-stu-id="dd45a-156">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="dd45a-157">L'implémentation est plutôt basique dans les deux cas.</span><span class="sxs-lookup"><span data-stu-id="dd45a-157">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="dd45a-158">Dans <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> et <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, l'inspecteur de message est créé et ajouté à la collection <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> de l'exécution respective.</span><span class="sxs-lookup"><span data-stu-id="dd45a-158">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
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
> <span data-ttu-id="dd45a-159">Ce comportement spécifique ne joue pas le rôle d'attribut et, par conséquent, ne peut pas être ajouté de façon déclarative sur un type de contrat d'un type de service.</span><span class="sxs-lookup"><span data-stu-id="dd45a-159">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="dd45a-160">Cette décision de conception a été prise car la collection de schémas ne peut pas être chargée dans une déclaration attribute, et faire référence à un emplacement de configuration supplémentaire (par exemple aux paramètres d’application) dans cet attribut revient à créer un élément de configuration qui n’est pas cohérent avec le reste de la configuration de modèle de service.</span><span class="sxs-lookup"><span data-stu-id="dd45a-160">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="dd45a-161">Par conséquent, ce comportement peut uniquement être ajouté de façon impérative via le code et une extension de configuration de modèle de service.</span><span class="sxs-lookup"><span data-stu-id="dd45a-161">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="dd45a-162">Ajout de l'inspecteur de message via la configuration</span><span class="sxs-lookup"><span data-stu-id="dd45a-162">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="dd45a-163">Pour configurer un comportement personnalisé sur un point de terminaison dans le fichier de configuration de l’application, le modèle de service requiert des implémenteurs pour créer un *élément d’extension* de configuration représenté par une classe dérivée de <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> .</span><span class="sxs-lookup"><span data-stu-id="dd45a-163">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="dd45a-164">Cette extension doit être ensuite ajoutée à la section de configuration du modèle de service pour les extensions, tel qu’indiqué pour l’extension suivante traitée dans cette section.</span><span class="sxs-lookup"><span data-stu-id="dd45a-164">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
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
  
 <span data-ttu-id="dd45a-165">Des extensions peuvent être ajoutées dans le fichier de configuration de l'application ou ASP.NET (ce qui est le choix le plus courant), ou bien dans le fichier de configuration de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dd45a-165">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="dd45a-166">Lorsque l’extension est ajoutée à une étendue de configuration, le comportement peut être ajouté à une configuration de comportement, tel qu’indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="dd45a-166">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="dd45a-167">Les configurations de comportement sont des éléments réutilisables qui peuvent être appliqués à plusieurs points de terminaison selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="dd45a-167">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="dd45a-168">Le comportement spécifique à configurer dans ce cas implémentant <xref:System.ServiceModel.Description.IEndpointBehavior>, il est uniquement valide dans la section de configuration respective du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="dd45a-168">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="dd45a-169">L'élément `<schemaValidator>` qui configure l'inspecteur de message est soutenu par la classe `SchemaValidationBehaviorExtensionElement`.</span><span class="sxs-lookup"><span data-stu-id="dd45a-169">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="dd45a-170">La classe expose deux propriétés publiques booléennes appelées `ValidateRequest` et `ValidateReply`.</span><span class="sxs-lookup"><span data-stu-id="dd45a-170">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="dd45a-171">Elles sont marquées avec <xref:System.Configuration.ConfigurationPropertyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="dd45a-171">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="dd45a-172">Cet attribut constitue le lien entre les propriétés de code et les attributs XML qui peuvent être observés sur l'élément de configuration XML précédent.</span><span class="sxs-lookup"><span data-stu-id="dd45a-172">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="dd45a-173">La classe possède également la propriété `Schemas` qui est en outre marquée avec <xref:System.Configuration.ConfigurationCollectionAttribute> et qui est du type `SchemaCollection`, lequel fait également partie de cet exemple mais a été omis de ce document pour des raisons de concision.</span><span class="sxs-lookup"><span data-stu-id="dd45a-173">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="dd45a-174">Cette propriété, ainsi que la collection et la classe d'élément de collection `SchemaConfigElement`, soutient l'élément `<schemas>` dans l'extrait de code de configuration précédent et permet d'ajouter une collection de schémas à l'ensemble de validation.</span><span class="sxs-lookup"><span data-stu-id="dd45a-174">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="dd45a-175">La méthode `CreateBehavior` substituée change les données de configuration en objet de comportement lorsque l'exécution évalue les données de configuration car elle génère un client ou un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="dd45a-175">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="dd45a-176">Ajout d'inspecteurs de message de façon impérative</span><span class="sxs-lookup"><span data-stu-id="dd45a-176">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="dd45a-177">Excepté via les attributs (approche qui n'est pas prise en charge dans cet exemple pour la raison précédemment citée) et la configuration, des comportements peuvent être assez facilement ajoutés à une exécution de client et de service à l'aide de code impératif.</span><span class="sxs-lookup"><span data-stu-id="dd45a-177">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="dd45a-178">Dans cet exemple, cette opération s'effectue dans l'application cliente afin de tester l'inspecteur de message client.</span><span class="sxs-lookup"><span data-stu-id="dd45a-178">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="dd45a-179">La classe `GenericClient` est dérivée de <xref:System.ServiceModel.ClientBase%601>, qui expose la configuration de point de terminaison au code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="dd45a-179">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="dd45a-180">Avant que le client ne soit implicitement ouvert, la configuration de point de terminaison peut être modifiée, par exemple en ajoutant des comportements tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="dd45a-180">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="dd45a-181">L'ajout du comportement sur le service est en grande partie équivalent à la technique du client présentée ici et doit être effectué avant que l'hôte de service ne soit ouvert.</span><span class="sxs-lookup"><span data-stu-id="dd45a-181">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dd45a-182">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="dd45a-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="dd45a-183">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dd45a-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="dd45a-184">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dd45a-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="dd45a-185">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dd45a-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dd45a-186">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dd45a-186">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dd45a-187">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="dd45a-187">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="dd45a-188">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="dd45a-188">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dd45a-189">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="dd45a-189">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
