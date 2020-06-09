---
title: Utilisation de contrats de message
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: 1b102b97c62df0bb8b031ded0f9165a11f8a8911
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600268"
---
# <a name="using-message-contracts"></a><span data-ttu-id="11315-102">Utilisation de contrats de message</span><span class="sxs-lookup"><span data-stu-id="11315-102">Using Message Contracts</span></span>
<span data-ttu-id="11315-103">En général, lors de la création d’applications Windows Communication Foundation (WCF), les développeurs prêtent une attention particulière aux structures de données et aux problèmes de sérialisation, et n’ont pas besoin de se préoccuper de la structure des messages dans lesquels les données sont transportées.</span><span class="sxs-lookup"><span data-stu-id="11315-103">Typically when building Windows Communication Foundation (WCF) applications, developers pay close attention to the data structures and serialization issues and do not need to concern themselves with the structure of the messages in which the data is carried.</span></span> <span data-ttu-id="11315-104">Pour ces applications, créer des contrats de données pour les paramètres ou les valeurs de retour est une procédure simple.</span><span class="sxs-lookup"><span data-stu-id="11315-104">For these applications, creating data contracts for the parameters or return values is straightforward.</span></span> <span data-ttu-id="11315-105">(Pour plus d’informations, consultez [spécification d’transfert de données dans les contrats de service](specifying-data-transfer-in-service-contracts.md).)</span><span class="sxs-lookup"><span data-stu-id="11315-105">(For more information, see [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md).)</span></span>  
  
 <span data-ttu-id="11315-106">Toutefois, le contrôle complet sur la structure d'un message SOAP est parfois aussi important que celui sur son contenu.</span><span class="sxs-lookup"><span data-stu-id="11315-106">However, sometimes complete control over the structure of a SOAP message is just as important as control over its contents.</span></span> <span data-ttu-id="11315-107">Cela se vérifie tout particulièrement lorsque l'interopérabilité est importante ou pour contrôler spécifiquement des problèmes de sécurité au niveau du message ou de la partie de message.</span><span class="sxs-lookup"><span data-stu-id="11315-107">This is especially true when interoperability is important or to specifically control security issues at the level of the message or message part.</span></span> <span data-ttu-id="11315-108">Dans ce cas, vous pouvez créer un *contrat de message* qui vous permet de spécifier la structure du message SOAP précis requis.</span><span class="sxs-lookup"><span data-stu-id="11315-108">In these cases, you can create a *message contract* that enables you to specify the structure of the precise SOAP message required.</span></span>  
  
 <span data-ttu-id="11315-109">Cette rubrique explique comment utiliser les divers attributs de contrat de message afin de créer un contrat de message spécifique pour votre opération.</span><span class="sxs-lookup"><span data-stu-id="11315-109">This topic discusses how to use the various message contract attributes to create a specific message contract for your operation.</span></span>  
  
## <a name="using-message-contracts-in-operations"></a><span data-ttu-id="11315-110">Utilisation de contrats de message dans les opérations</span><span class="sxs-lookup"><span data-stu-id="11315-110">Using Message Contracts in Operations</span></span>  
 <span data-ttu-id="11315-111">WCF prend en charge les opérations modélisées sur le *style d’appel de procédure distante (RPC)* ou le *style de messagerie*.</span><span class="sxs-lookup"><span data-stu-id="11315-111">WCF supports operations modeled on either the *remote procedure call (RPC) style* or the *messaging style*.</span></span> <span data-ttu-id="11315-112">Dans une opération de style RPC, vous pouvez utiliser n’importe quel type sérialisable, et vous avez accès aux fonctionnalités disponibles aux appels locaux, tels que plusieurs paramètres et les paramètres `ref` et `out`.</span><span class="sxs-lookup"><span data-stu-id="11315-112">In an RPC-style operation, you can use any serializable type, and you have access to the features that are available to local calls, such as multiple parameters and `ref` and `out` parameters.</span></span> <span data-ttu-id="11315-113">Dans ce style, le formulaire de sérialisation choisi contrôle la structure des données dans les messages sous-jacents, et le runtime WCF crée les messages pour prendre en charge l’opération.</span><span class="sxs-lookup"><span data-stu-id="11315-113">In this style, the form of serialization chosen controls the structure of the data in the underlying messages, and the WCF runtime creates the messages to support the operation.</span></span> <span data-ttu-id="11315-114">Cela permet aux développeurs qui ne sont pas familiarisés avec SOAP et les messages SOAP de créer et d'utiliser rapidement et facilement des applications de service.</span><span class="sxs-lookup"><span data-stu-id="11315-114">This enables developers who are not familiar with SOAP and SOAP messages to quickly and easily create and use service applications.</span></span>  
  
 <span data-ttu-id="11315-115">L'exemple de code suivant présente une opération de service modélisée sur le style RPC.</span><span class="sxs-lookup"><span data-stu-id="11315-115">The following code example shows a service operation modeled on the RPC style.</span></span>  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 <span data-ttu-id="11315-116">Habituellement, un contrat de données est suffisant pour définir le schéma des messages.</span><span class="sxs-lookup"><span data-stu-id="11315-116">Normally, a data contract is sufficient to define the schema for the messages.</span></span> <span data-ttu-id="11315-117">Par exemple, cela est suffisant pour la plupart des applications dans l'exemple précédent si `BankingTransaction` et `BankingTransactionResponse` ont des contrats de données pour définir le contenu des messages SOAP sous-jacents.</span><span class="sxs-lookup"><span data-stu-id="11315-117">For instance, in the preceding example, it is sufficient for most applications if `BankingTransaction` and `BankingTransactionResponse` have data contracts to define the contents of the underlying SOAP messages.</span></span> <span data-ttu-id="11315-118">Pour plus d’informations sur les contrats de données, consultez [utilisation de contrats de données](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="11315-118">For more information about data contracts, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="11315-119">Toutefois, il peut parfois s'avérer nécessaire de contrôler de manière précise la façon dont la structure du message SOAP est transmise sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="11315-119">However, occasionally it is necessary to precisely control how the structure of the SOAP message transmitted over the wire.</span></span> <span data-ttu-id="11315-120">Le scénario le plus courant dans ce cas consiste à insérer des en-têtes SOAP personnalisés.</span><span class="sxs-lookup"><span data-stu-id="11315-120">The most common scenario for this is inserting custom SOAP headers.</span></span> <span data-ttu-id="11315-121">Un autre consiste à définir des propriétés de sécurité pour le corps et les en-têtes du message, c'est à-dire, à déterminer si ces éléments sont chiffrés et signés numériquement.</span><span class="sxs-lookup"><span data-stu-id="11315-121">Another common scenario is to define security properties for the message's headers and body, that is, to decide whether these elements are digitally signed and encrypted.</span></span> <span data-ttu-id="11315-122">Enfin, certaines piles SOAP tiers requièrent que les messages soient dans un format spécifique.</span><span class="sxs-lookup"><span data-stu-id="11315-122">Finally, some third-party SOAP stacks require messages be in a specific format.</span></span> <span data-ttu-id="11315-123">Les opérations de style de messagerie fournissent ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="11315-123">Messaging-style operations provide this control.</span></span>  
  
 <span data-ttu-id="11315-124">Une opération de style de messagerie a au plus un paramètre et une valeur de retour où les deux types sont des types de messages ; autrement dit, ils sérialisent directement dans une structure de message SOAP spécifiée.</span><span class="sxs-lookup"><span data-stu-id="11315-124">A messaging-style operation has at most one parameter and one return value where both types are message types; that is, they serialize directly into a specified SOAP message structure.</span></span> <span data-ttu-id="11315-125">Il peut s'agir de n'importe quel type marqué avec le type <xref:System.ServiceModel.MessageContractAttribute> ou <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="11315-125">This may be any type marked with the <xref:System.ServiceModel.MessageContractAttribute> or the <xref:System.ServiceModel.Channels.Message> type.</span></span> <span data-ttu-id="11315-126">L'exemple de code suivant présente une opération similaire au style RCP précédent, mais qui utilise le style de messagerie.</span><span class="sxs-lookup"><span data-stu-id="11315-126">The following code example shows an operation similar to the preceding RCP-style, but which uses the messaging style.</span></span>  
  
 <span data-ttu-id="11315-127">Par exemple, si `BankingTransaction` et `BankingTransactionResponse` sont les deux types qui sont des contrats de message, alors le code dans les opérations suivantes est valide.</span><span class="sxs-lookup"><span data-stu-id="11315-127">For example, if `BankingTransaction` and `BankingTransactionResponse` are both types that are message contracts, then the code in the following operations is valid.</span></span>  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 <span data-ttu-id="11315-128">Toutefois, le code suivant n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="11315-128">However, the following code is invalid.</span></span>  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 <span data-ttu-id="11315-129">Une exception est levée pour toute opération qui implique un type de contrat de message et ne suit pas l’un des modèles valides.</span><span class="sxs-lookup"><span data-stu-id="11315-129">An exception is thrown for any operation that involves a message contract type and that does not follow one of the valid patterns.</span></span> <span data-ttu-id="11315-130">Bien évidemment, les opérations qui n'impliquent pas de types de contrats de message ne sont pas soumises à ces restrictions.</span><span class="sxs-lookup"><span data-stu-id="11315-130">Of course, operations that do not involve message contract types are not subject to these restrictions.</span></span>  
  
 <span data-ttu-id="11315-131">Si un type dispose à la fois d'un contrat de message et d'un contrat de données, seul son contrat de message est pris en compte lorsque le type est utilisé dans une opération.</span><span class="sxs-lookup"><span data-stu-id="11315-131">If a type has both a message contract and a data contract, only its message contract is considered when the type is used in an operation.</span></span>  
  
## <a name="defining-message-contracts"></a><span data-ttu-id="11315-132">Définition de contrats de message</span><span class="sxs-lookup"><span data-stu-id="11315-132">Defining Message Contracts</span></span>  
 <span data-ttu-id="11315-133">Pour définir un contrat de message pour un type (autrement dit, définir le mappage entre le type et une enveloppe SOAP), appliquez <xref:System.ServiceModel.MessageContractAttribute> au type.</span><span class="sxs-lookup"><span data-stu-id="11315-133">To define a message contract for a type (that is, to define the mapping between the type and a SOAP envelope), apply the <xref:System.ServiceModel.MessageContractAttribute> to the type.</span></span> <span data-ttu-id="11315-134">Puis appliquez <xref:System.ServiceModel.MessageHeaderAttribute> aux membres du type que vous souhaitez créer dans les en-têtes SOAP et appliquez <xref:System.ServiceModel.MessageBodyMemberAttribute> aux membres que vous souhaitez créer dans les parties du corps SOAP du message.</span><span class="sxs-lookup"><span data-stu-id="11315-134">Then apply the <xref:System.ServiceModel.MessageHeaderAttribute> to those members of the type you want to make into SOAP headers, and apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to those members you want to make into parts of the SOAP body of the message.</span></span>  
  
 <span data-ttu-id="11315-135">Le code suivant fournit un exemple d'utilisation d'un contrat de message.</span><span class="sxs-lookup"><span data-stu-id="11315-135">The following code provides an example of using a message contract.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader] public DateTime transactionDate;  
  [MessageBodyMember] private Account sourceAccount;  
  [MessageBodyMember] private Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 <span data-ttu-id="11315-136">En utilisant ce type comme paramètre d'opération, l'enveloppe SOAP suivante est générée :</span><span class="sxs-lookup"><span data-stu-id="11315-136">When using this type as an operation parameter, the following SOAP envelope is generated:</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
    <h:transactionDate xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">2012-02-16T16:10:00</h:transactionDate>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <BankingTransaction xmlns="http://tempuri.org/">  
      <amount>0</amount>  
      <sourceAccount xsi:nil="true"/>  
      <targetAccount xsi:nil="true"/>  
    </BankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="11315-137">Notez que `operation` et `transactionDate` apparaissent comme des en-têtes SOAP et le corps SOAP se compose d'un élément wrapper `BankingTransaction` contenant `sourceAccount`,`targetAccount` et `amount`.</span><span class="sxs-lookup"><span data-stu-id="11315-137">Notice that `operation` and `transactionDate` appear as SOAP headers and the SOAP body consists of a wrapper element `BankingTransaction` containing `sourceAccount`,`targetAccount`, and `amount`.</span></span>  
  
 <span data-ttu-id="11315-138">Vous pouvez appliquer <xref:System.ServiceModel.MessageHeaderAttribute> et <xref:System.ServiceModel.MessageBodyMemberAttribute> à l'ensemble des champs, propriétés et événements, indépendamment du fait qu'ils soient publics, privés, protégés ou internes.</span><span class="sxs-lookup"><span data-stu-id="11315-138">You can apply the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> to all fields, properties, and events, regardless of whether they are public, private, protected, or internal.</span></span>  
  
 <span data-ttu-id="11315-139"><xref:System.ServiceModel.MessageContractAttribute> vous permet de spécifier les attributs WrapperName et WrapperNamespace qui contrôlent le nom de l'élément wrapper dans le corps du message SOAP.</span><span class="sxs-lookup"><span data-stu-id="11315-139">The <xref:System.ServiceModel.MessageContractAttribute> allows you to specify the WrapperName and WrapperNamespace attributes which control the name of the wrapper element in the body of the SOAP message.</span></span> <span data-ttu-id="11315-140">Par défaut le nom du type de contrat de message est utilisé pour le wrapper et l'espace de noms dans lequel le contrat de message est défini `http://tempuri.org/` est utilisé comme espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="11315-140">By default the name of the message contract type is used for the wrapper and the namespace in which the message contract is defined `http://tempuri.org/` is used as the default namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11315-141">Les attributs <xref:System.Runtime.Serialization.KnownTypeAttribute> sont ignorés dans les contrats de message.</span><span class="sxs-lookup"><span data-stu-id="11315-141"><xref:System.Runtime.Serialization.KnownTypeAttribute> attributes are ignored in message contracts.</span></span> <span data-ttu-id="11315-142">Si un <xref:System.Runtime.Serialization.KnownTypeAttribute> est requis, placez-le sur l'opération qui utilise le contrat de message en question.</span><span class="sxs-lookup"><span data-stu-id="11315-142">If a <xref:System.Runtime.Serialization.KnownTypeAttribute> is required, place it on the operation that is using the message contract in question.</span></span>  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a><span data-ttu-id="11315-143">Contrôle des espaces de noms et noms des en-têtes et parties du corps</span><span class="sxs-lookup"><span data-stu-id="11315-143">Controlling Header and Body Part Names and Namespaces</span></span>  
 <span data-ttu-id="11315-144">Dans la représentation SOAP d'un contrat de message, chaque en-tête et le partie du corps mappe à un élément XML ayant un nom et un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="11315-144">In the SOAP representation of a message contract, each header and body part maps to an XML element that has a name and a namespace.</span></span>  
  
 <span data-ttu-id="11315-145">Par défaut, l'espace de noms est le même que celui du contrat de service auquel le message participe, et le nom est déterminé par le nom de membre auquel les attributs <xref:System.ServiceModel.MessageHeaderAttribute> ou <xref:System.ServiceModel.MessageBodyMemberAttribute> sont appliqués.</span><span class="sxs-lookup"><span data-stu-id="11315-145">By default, the namespace is the same as the namespace of the service contract that the message is participating in, and the name is determined by the member name to which the <xref:System.ServiceModel.MessageHeaderAttribute> or the <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes are applied.</span></span>  
  
 <span data-ttu-id="11315-146">Vous pouvez modifier ces valeurs par défaut en manipulant <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> et <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (sur la classe parente des attributs <xref:System.ServiceModel.MessageHeaderAttribute> et <xref:System.ServiceModel.MessageBodyMemberAttribute>).</span><span class="sxs-lookup"><span data-stu-id="11315-146">You can change these defaults by manipulating the <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (on the parent class of the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes).</span></span>  
  
 <span data-ttu-id="11315-147">Examinons la classe dans l'exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="11315-147">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="11315-148">Dans cet exemple, l'en-tête `IsAudited` est dans l'espace de noms spécifié dans le code, et le corps qui représente le membre `theData` est représenté par un élément XML avec le nom `transactionData`.</span><span class="sxs-lookup"><span data-stu-id="11315-148">In this example, the `IsAudited` header is in the namespace specified in the code, and the body part that represents the `theData` member is represented by an XML element with the name `transactionData`.</span></span> <span data-ttu-id="11315-149">Le code suivant montre le XML généré pour ce contrat de message.</span><span class="sxs-lookup"><span data-stu-id="11315-149">The following shows the XML generated for this message contract.</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:IsAudited xmlns:h="http://schemas.contoso.com/auditing/2005" xmlns="http://schemas.contoso.com/auditing/2005">false</h:IsAudited>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <AuditedBankingTransaction xmlns="http://tempuri.org/">  
      <transactionData/>  
    </AuditedBankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a><span data-ttu-id="11315-150">Contrôle de l'encapsulation des parties de corps SOAP</span><span class="sxs-lookup"><span data-stu-id="11315-150">Controlling Whether the SOAP Body Parts Are Wrapped</span></span>  
 <span data-ttu-id="11315-151">Par défaut, les parties de corps SOAP sont sérialisées à l'intérieur d'un élément encapsulé.</span><span class="sxs-lookup"><span data-stu-id="11315-151">By default, the SOAP body parts are serialized inside a wrapped element.</span></span> <span data-ttu-id="11315-152">Par exemple, le code suivant affiche l'élément wrapper `HelloGreetingMessage` généré à partir du nom du type <xref:System.ServiceModel.MessageContractAttribute> dans le contrat de message du message `HelloGreetingMessage`.</span><span class="sxs-lookup"><span data-stu-id="11315-152">For example, the following code shows the `HelloGreetingMessage` wrapper element generated from the name of the <xref:System.ServiceModel.MessageContractAttribute> type in the message contract for the `HelloGreetingMessage` message.</span></span>  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 <span data-ttu-id="11315-153">Pour supprimer l'élément wrapper, affectez <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> à la propriété `false`.</span><span class="sxs-lookup"><span data-stu-id="11315-153">To suppress the wrapper element, set the <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> property to `false`.</span></span> <span data-ttu-id="11315-154">Pour contrôler le nom et l'espace de noms de l'élément wrapper, utilisez les propriétés <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> et <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A>.</span><span class="sxs-lookup"><span data-stu-id="11315-154">To control the name and the namespace of the wrapper element, use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> and <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11315-155">La présence de plusieurs parties de corps de messages non encapsulées n'est pas conforme à WS-I Basic Profile 1.1 et n'est pas recommandée lors de la conception de nouveaux contrats de message.</span><span class="sxs-lookup"><span data-stu-id="11315-155">Having more than one message body part in messages that are not wrapped is not compliant with WS-I Basic Profile 1.1 and is not recommended when designing new message contracts.</span></span> <span data-ttu-id="11315-156">Toutefois, il peut s'avérer nécessaire d'avoir plusieurs parties de corps du message non encapsulées dans certains scénarios d'interopérabilité spécifiques.</span><span class="sxs-lookup"><span data-stu-id="11315-156">However, it may be necessary to have more than one unwrapped message body part in certain specific interoperability scenarios.</span></span> <span data-ttu-id="11315-157">Si vous prévoyez de transmettre plusieurs éléments de données dans un corps de message, il est recommandé d'utiliser le mode (encapsulé) par défaut.</span><span class="sxs-lookup"><span data-stu-id="11315-157">If you are going to transmit more than one piece of data in a message body, it is recommended to use the default (wrapped) mode.</span></span> <span data-ttu-id="11315-158">La présence de plusieurs en-têtes de message dans des messages non encapsulés est complètement acceptable.</span><span class="sxs-lookup"><span data-stu-id="11315-158">Having more than one message header in unwrapped messages is completely acceptable.</span></span>  
  
## <a name="using-custom-types-inside-message-contracts"></a><span data-ttu-id="11315-159">Utilisation de types personnalisés dans des contrats de message</span><span class="sxs-lookup"><span data-stu-id="11315-159">Using Custom Types Inside Message Contracts</span></span>  
 <span data-ttu-id="11315-160">Chaque partie de corps de message et en-tête de message individuel est sérialisé (converti en XML) à l'aide du moteur de sérialisation choisi du contrat de service dans lequel le message est utilisé.</span><span class="sxs-lookup"><span data-stu-id="11315-160">Each individual message header and message body part is serialized (turned into XML) using the chosen serialization engine for the service contract where the message is used.</span></span> <span data-ttu-id="11315-161">Le moteur de sérialisation par défaut, `XmlFormatter`, peut gérer n'importe quel type ayant un contrat de données, soit explicitement (en ayant <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) ou implicitement (en étant un type primitif, en ayant <xref:System.SerializableAttribute?displayProperty=nameWithType>, etc.).</span><span class="sxs-lookup"><span data-stu-id="11315-161">The default serialization engine, the `XmlFormatter`, can handle any type that has a data contract, either explicitly (by having the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) or implicitly (by being a primitive type, having the <xref:System.SerializableAttribute?displayProperty=nameWithType>, and so on).</span></span> <span data-ttu-id="11315-162">Pour plus d’informations, consultez [utilisation de contrats de données](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="11315-162">For more information, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="11315-163">Dans l'exemple précédent, les types `Operation` et `BankingTransactionData` doivent avoir un contrat de données, et `transactionDate` est sérialisable car <xref:System.DateTime> est un type primitif (et a ainsi un contrat de données implicite).</span><span class="sxs-lookup"><span data-stu-id="11315-163">In the preceding example, the `Operation` and `BankingTransactionData` types must have a data contract, and `transactionDate` is serializable because <xref:System.DateTime> is a primitive (and so has an implicit data contract).</span></span>  
  
 <span data-ttu-id="11315-164">Cependant, il est possible de basculer sur un autre moteur de sérialisation, `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="11315-164">However, it is possible to switch to a different serialization engine, the `XmlSerializer`.</span></span> <span data-ttu-id="11315-165">Dans ce cas, vous devez vous assurer que tous les types utilisés pour les en-têtes de message et les parties du corps sont sérialisables à l'aide de `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="11315-165">If you make such a switch, you should ensure that all of the types used for message headers and body parts are serializable using the `XmlSerializer`.</span></span>  
  
## <a name="using-arrays-inside-message-contracts"></a><span data-ttu-id="11315-166">Utilisation de tableaux dans des contrats de message</span><span class="sxs-lookup"><span data-stu-id="11315-166">Using Arrays Inside Message Contracts</span></span>  
 <span data-ttu-id="11315-167">Vous pouvez utiliser des tableaux d'éléments répétitifs dans des contrats de message de deux manières différentes.</span><span class="sxs-lookup"><span data-stu-id="11315-167">You can use arrays of repeating elements in message contracts in two ways.</span></span>  
  
 <span data-ttu-id="11315-168">La première méthode consiste à utiliser <xref:System.ServiceModel.MessageHeaderAttribute> ou <xref:System.ServiceModel.MessageBodyMemberAttribute> directement sur le tableau.</span><span class="sxs-lookup"><span data-stu-id="11315-168">The first is to use a <xref:System.ServiceModel.MessageHeaderAttribute> or a <xref:System.ServiceModel.MessageBodyMemberAttribute> directly on the array.</span></span> <span data-ttu-id="11315-169">Dans ce cas, l'ensemble du tableau est sérialisé comme un seul élément (c'est-à-dire, un seul en-tête ou un seul corps) avec plusieurs éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="11315-169">In this case, the entire array is serialized as one element (that is, one header or one body part) with multiple child elements.</span></span> <span data-ttu-id="11315-170">Examinons la classe dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="11315-170">Consider the class in the following example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 <span data-ttu-id="11315-171">Les en-têtes SOAP sont similaires aux éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="11315-171">This results in SOAP headers is similar to the following.</span></span>  
  
```xml  
<BankingDepositLog>  
<numRecords>3</numRecords>  
<records>  
  <DepositRecord>Record1</DepositRecord>  
  <DepositRecord>Record2</DepositRecord>  
  <DepositRecord>Record3</DepositRecord>  
</records>  
<branchID>20643</branchID>  
</BankingDepositLog>  
```  
  
 <span data-ttu-id="11315-172">L'autre méthode consiste à utiliser <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="11315-172">An alternative to this is to use the <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span></span> <span data-ttu-id="11315-173">Dans ce cas, chaque élément de tableau est sérialisé indépendamment et de manière à n'avoir qu'un seul en-tête comme suit.</span><span class="sxs-lookup"><span data-stu-id="11315-173">In this case, each array element is serialized independently and so that each array element has one header, similar to the following.</span></span>  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 <span data-ttu-id="11315-174">Le nom par défaut des entrées de tableau correspond à celui du membre auquel l'attribut <xref:System.ServiceModel.MessageHeaderArrayAttribute> est appliqué.</span><span class="sxs-lookup"><span data-stu-id="11315-174">The default name for array entries is the name of the member to which the <xref:System.ServiceModel.MessageHeaderArrayAttribute> attributes is applied.</span></span>  
  
 <span data-ttu-id="11315-175">L'attribut <xref:System.ServiceModel.MessageHeaderArrayAttribute> hérite de <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="11315-175">The <xref:System.ServiceModel.MessageHeaderArrayAttribute> attribute inherits from the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="11315-176">Il a le même jeu de fonctionnalités que les attributs non-tableau ; il est possible, par exemple, de définir l’ordre, le nom et l’espace de noms d’un tableau d’en-têtes de la même façon que pour un en-tête unique.</span><span class="sxs-lookup"><span data-stu-id="11315-176">It has the same set of features as the non-array attributes, for example, it is possible to set the order, name, and namespace for an array of headers in the same way you set it for a single header.</span></span> <span data-ttu-id="11315-177">Lorsque vous utilisez la propriété `Order` sur un tableau, elle s'applique à l'ensemble de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="11315-177">When you use the `Order` property on an array, it applies to the entire array.</span></span>  
  
 <span data-ttu-id="11315-178">Vous ne pouvez appliquer <xref:System.ServiceModel.MessageHeaderArrayAttribute> qu’aux tableaux, et non pas aux collections.</span><span class="sxs-lookup"><span data-stu-id="11315-178">You can apply the <xref:System.ServiceModel.MessageHeaderArrayAttribute> only to arrays, not collections.</span></span>  
  
## <a name="using-byte-arrays-in-message-contracts"></a><span data-ttu-id="11315-179">Utilisation de tableaux d'octets dans des contrats de message</span><span class="sxs-lookup"><span data-stu-id="11315-179">Using Byte Arrays in Message Contracts</span></span>  
 <span data-ttu-id="11315-180">Les tableaux d'octets, lorsqu'ils sont utilisés avec des attributs non-tableau (<xref:System.ServiceModel.MessageBodyMemberAttribute> et <xref:System.ServiceModel.MessageHeaderAttribute>), ne sont pas traités comme des tableaux mais comme un type primitif spécial représenté sous forme de données encodées en base 64 dans le XML résultant.</span><span class="sxs-lookup"><span data-stu-id="11315-180">Byte arrays, when used with the non-array attributes (<xref:System.ServiceModel.MessageBodyMemberAttribute> and <xref:System.ServiceModel.MessageHeaderAttribute>), are not treated as arrays but as a special primitive type represented as Base64-encoded data in the resulting XML.</span></span>  
  
 <span data-ttu-id="11315-181">Lorsque vous utilisez des tableaux d'octets avec l'attribut de tableau <xref:System.ServiceModel.MessageHeaderArrayAttribute>, les résultats varient en fonction du sérialiseur utilisé.</span><span class="sxs-lookup"><span data-stu-id="11315-181">When you use byte arrays with the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the results depend on the serializer in use.</span></span> <span data-ttu-id="11315-182">Avec le sérialiseur par défaut, le tableau est représenté sous forme d'une entrée individuelle pour chaque octet.</span><span class="sxs-lookup"><span data-stu-id="11315-182">With the default serializer, the array is represented as an individual entry for each byte.</span></span> <span data-ttu-id="11315-183">Toutefois, lorsque `XmlSerializer` est sélectionné, (à l'aide de <xref:System.ServiceModel.XmlSerializerFormatAttribute> sur le contrat de service), les tableaux d'octets sont traités comme des données Base64, indépendamment de l'utilisation d'attributs de tableau ou non-tableau.</span><span class="sxs-lookup"><span data-stu-id="11315-183">However, when the `XmlSerializer` is selected, (using the <xref:System.ServiceModel.XmlSerializerFormatAttribute> on the service contract), byte arrays are treated as Base64 data regardless of whether the array or non-array attributes are used.</span></span>  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a><span data-ttu-id="11315-184">Signature et chiffrement des parties du message</span><span class="sxs-lookup"><span data-stu-id="11315-184">Signing and Encrypting Parts of the Message</span></span>  
 <span data-ttu-id="11315-185">Un contrat de message peut indiquer si les en-têtes et/ou le corps du message doivent être signés numériquement et chiffrés.</span><span class="sxs-lookup"><span data-stu-id="11315-185">A message contract can indicate whether the headers and/or body of the message should be digitally signed and encrypted.</span></span>  
  
 <span data-ttu-id="11315-186">Pour ce faire, définissez la propriété <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> sur les attributs <xref:System.ServiceModel.MessageHeaderAttribute> et <xref:System.ServiceModel.MessageBodyMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="11315-186">This is done by setting the <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> property on the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="11315-187">La propriété est une énumération du type <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> et peut être définie à <xref:System.Net.Security.ProtectionLevel.None> (pas de chiffrement ni de signature), <xref:System.Net.Security.ProtectionLevel.Sign> (signature numérique uniquement) ou <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (chiffrement et signature numérique).</span><span class="sxs-lookup"><span data-stu-id="11315-187">The property is an enumeration of the <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> type and can be set to <xref:System.Net.Security.ProtectionLevel.None> (no encryption or signature), <xref:System.Net.Security.ProtectionLevel.Sign> (digital signature only), or <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (both encryption and a digital signature).</span></span> <span data-ttu-id="11315-188">Par défaut, il s’agit de <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="11315-188">The default is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
 <span data-ttu-id="11315-189">Pour que ces fonctionnalités de sécurité fonctionnent, vous devez configurer la liaison et les comportements correctement.</span><span class="sxs-lookup"><span data-stu-id="11315-189">For these security features to work, you must properly configure the binding and behaviors.</span></span> <span data-ttu-id="11315-190">Si vous utilisez ces fonctionnalités de sécurité sans configuration correcte (par exemple, essayer de signer un message sans fournir vos informations d’identification), une exception est levée lors de la validation.</span><span class="sxs-lookup"><span data-stu-id="11315-190">If you use these security features without the proper configuration (for example, attempting to sign a message without supplying your credentials), an exception is thrown at validation time.</span></span>  
  
 <span data-ttu-id="11315-191">Pour les en-têtes de message, le niveau de protection est déterminé individuellement pour chaque en-tête.</span><span class="sxs-lookup"><span data-stu-id="11315-191">For message headers, the protection level is determined individually for each header.</span></span>  
  
 <span data-ttu-id="11315-192">Pour les parties de corps de message, le niveau de protection peut être considéré comme le « niveau de protection minimal ».</span><span class="sxs-lookup"><span data-stu-id="11315-192">For message body parts, the protection level can be thought of as the "minimum protection level."</span></span> <span data-ttu-id="11315-193">Le corps a un seul niveau de protection, quel que soit le nombre de parties du corps.</span><span class="sxs-lookup"><span data-stu-id="11315-193">The body has only one protection level, regardless of the number of body parts.</span></span> <span data-ttu-id="11315-194">Le niveau de protection du corps est déterminé par le paramètre de propriété <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> le plus élevé de toutes les parties du corps.</span><span class="sxs-lookup"><span data-stu-id="11315-194">The protection level of the body is determined by the highest <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> property setting of all the body parts.</span></span> <span data-ttu-id="11315-195">Toutefois, vous devez définir le niveau de protection de chaque partie du corps au niveau de protection minimal réel requis.</span><span class="sxs-lookup"><span data-stu-id="11315-195">However, you should set the protection level of each body part to the actual minimum protection level required.</span></span>  
  
 <span data-ttu-id="11315-196">Examinons la classe dans l'exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="11315-196">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class PatientRecord  
{  
   [MessageHeader(ProtectionLevel=None)] public int recordID;  
   [MessageHeader(ProtectionLevel=Sign)] public string patientName;  
   [MessageHeader(ProtectionLevel=EncryptAndSign)] public string SSN;  
   [MessageBodyMember(ProtectionLevel=None)] public string comments;  
   [MessageBodyMember(ProtectionLevel=Sign)] public string diagnosis;  
   [MessageBodyMember(ProtectionLevel=EncryptAndSign)] public string medicalHistory;  
}  
```  
  
 <span data-ttu-id="11315-197">Dans cet exemple, l'en-tête `recordID` n'est pas protégé, `patientName` est `signed`, et `SSN` est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="11315-197">In this example, the `recordID` header is not protected, `patientName` is `signed`, and `SSN` is encrypted and signed.</span></span> <span data-ttu-id="11315-198">`medicalHistory` étant appliqué sur au moins une partie du corps (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>), l'ensemble du message est donc chiffré et signé, même si les commentaires et les parties de corps de diagnostic spécifient des niveaux de protection inférieurs.</span><span class="sxs-lookup"><span data-stu-id="11315-198">At least one body part, `medicalHistory`, has <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> applied, and thus the entire message body is encrypted and signed, even though the comments and diagnosis body parts specify lower protection levels.</span></span>  
  
## <a name="soap-action"></a><span data-ttu-id="11315-199">Action SOAP</span><span class="sxs-lookup"><span data-stu-id="11315-199">SOAP Action</span></span>  
 <span data-ttu-id="11315-200">SOAP et les standards de services Web associés définissent une propriété appelée `Action` qui peut être présente pour chaque message SOAP envoyé.</span><span class="sxs-lookup"><span data-stu-id="11315-200">SOAP and related Web services standards define a property called `Action` that can be present for every SOAP message sent.</span></span> <span data-ttu-id="11315-201">Les propriétés <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> et <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> de l'opération contrôlent la valeur de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="11315-201">The operation's <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> properties control the value of this property.</span></span>  
  
## <a name="soap-header-attributes"></a><span data-ttu-id="11315-202">Attributs d'en-tête SOAP</span><span class="sxs-lookup"><span data-stu-id="11315-202">SOAP Header Attributes</span></span>  
 <span data-ttu-id="11315-203">Le standard SOAP définit les attributs suivants qui peuvent exister dans un en-tête :</span><span class="sxs-lookup"><span data-stu-id="11315-203">The SOAP standard defines the following attributes that may exist on a header:</span></span>  
  
- <span data-ttu-id="11315-204">`Actor/Role` (`Actor` dans SOAP 1.1, `Role` dans SOAP 1.2)</span><span class="sxs-lookup"><span data-stu-id="11315-204">`Actor/Role` (`Actor` in SOAP 1.1, `Role` in SOAP 1.2)</span></span>  
  
- `MustUnderstand`  
  
- `Relay`  
  
 <span data-ttu-id="11315-205">L'attribut `Actor` ou `Role` spécifie l'URI (Uniform Resource Identifier) du nœud auquel un en-tête donné est destiné.</span><span class="sxs-lookup"><span data-stu-id="11315-205">The `Actor` or `Role` attribute specifies the Uniform Resource Identifier (URI) of the node for which a given header is intended.</span></span> <span data-ttu-id="11315-206">L'attribut `MustUnderstand` spécifie si le nœud qui traite cet en-tête doit le comprendre.</span><span class="sxs-lookup"><span data-stu-id="11315-206">The `MustUnderstand` attribute specifies whether the node processing the header must understand it.</span></span> <span data-ttu-id="11315-207">L'attribut `Relay` spécifie si l'en-tête sera relayé aux nœuds en aval.</span><span class="sxs-lookup"><span data-stu-id="11315-207">The `Relay` attribute specifies whether the header is to be relayed to downstream nodes.</span></span> <span data-ttu-id="11315-208">WCF n’effectue aucun traitement de ces attributs sur les messages entrants, à l’exception de l' `MustUnderstand` attribut, tel que spécifié dans la section « contrôle de version des contrats de message » plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="11315-208">WCF does not perform any processing of these attributes on incoming messages, except for the `MustUnderstand` attribute, as specified in the "Message Contract Versioning" section later in this topic.</span></span> <span data-ttu-id="11315-209">Toutefois, il vous permet de lire et d'écrire ces attributs si nécessaire, comme dans la description suivante.</span><span class="sxs-lookup"><span data-stu-id="11315-209">However, it allows you to read and write these attributes as necessary, as in the following description.</span></span>  
  
 <span data-ttu-id="11315-210">Lors de l'envoi d'un message, ces attributs ne sont pas émis par défaut.</span><span class="sxs-lookup"><span data-stu-id="11315-210">When sending a message, these attributes are not emitted by default.</span></span> <span data-ttu-id="11315-211">Vous pouvez modifier ce paramètre de deux façons :</span><span class="sxs-lookup"><span data-stu-id="11315-211">You can change this in two ways.</span></span> <span data-ttu-id="11315-212">La première méthode consiste à affecter statiquement aux attributs les valeurs souhaitées en modifiant les propriétés <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType> et <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType>, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="11315-212">First, you may statically set the attributes to any desired values by changing the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, and <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> properties, as shown in the following code example.</span></span> <span data-ttu-id="11315-213">(Notez qu'il n'y a pas de propriété `Role` ; la définition de la propriété <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> entraîne l'émission de l'attribut `Role` si vous utilisez SOAP 1.2).</span><span class="sxs-lookup"><span data-stu-id="11315-213">(Note that there is no `Role` property; setting the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> property emits the `Role` attribute if you are using SOAP 1.2).</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="11315-214">La deuxième méthode permettant de contrôler ces attributs s'appuie sur un mécanisme dynamique, via le code.</span><span class="sxs-lookup"><span data-stu-id="11315-214">The second way to control these attributes is dynamically, through code.</span></span> <span data-ttu-id="11315-215">Pour ce faire, encapsulez le type d'en-tête souhaité dans le type <xref:System.ServiceModel.MessageHeader%601> (assurez-vous de ne pas confondre ce type avec la version non générique), puis utilisez le type avec <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="11315-215">You can achieve this by wrapping the desired header type in the <xref:System.ServiceModel.MessageHeader%601> type (be sure not to confuse this type with the non-generic version) and by using the type together with the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="11315-216">Puis, utilisez des propriétés sur <xref:System.ServiceModel.MessageHeader%601> pour définir les attributs SOAP, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="11315-216">Then, you can use properties on the <xref:System.ServiceModel.MessageHeader%601> to set the SOAP attributes, as shown in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public MessageHeader<bool> IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
// application code:  
BankingTransaction bt = new BankingTransaction();  
bt.IsAudited = new MessageHeader<bool>();  
bt.IsAudited.Content = false; // Set IsAudited header value to "false"  
bt.IsAudited.Actor="http://auditingservice.contoso.com";  
bt.IsAudited.MustUnderstand=true;  
```  
  
 <span data-ttu-id="11315-217">Si vous utilisez à la fois les mécanismes de contrôle dynamique et statique, les paramètres statiques sont utilisés comme valeur par défaut mais peuvent être substitués ultérieurement en utilisant le mécanisme dynamique, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="11315-217">If you use both the dynamic and the static control mechanisms, the static settings are used as a default but can later be overridden by using the dynamic mechanism, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 <span data-ttu-id="11315-218">La création d'en-têtes répétés avec contrôle d'attribut dynamique est autorisée, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="11315-218">Creating repeated headers with dynamic attribute control is allowed, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 <span data-ttu-id="11315-219">Côté réception, la lecture de ces attributs SOAP peut être faite uniquement si la classe <xref:System.ServiceModel.MessageHeader%601> est utilisée pour l'en-tête dans le type.</span><span class="sxs-lookup"><span data-stu-id="11315-219">On the receiving side, reading these SOAP attributes can only be done if the <xref:System.ServiceModel.MessageHeader%601> class is used for the header in the type.</span></span> <span data-ttu-id="11315-220">Examinez les propriétés `Actor`, `Relay` ou `MustUnderstand` d'un en-tête du type <xref:System.ServiceModel.MessageHeader%601> pour découvrir les paramètres d'attribut sur le message reçu.</span><span class="sxs-lookup"><span data-stu-id="11315-220">Examine the `Actor`, `Relay`, or `MustUnderstand` properties of a header of the <xref:System.ServiceModel.MessageHeader%601> type to discover the attribute settings on the received message.</span></span>  
  
 <span data-ttu-id="11315-221">Lorsqu'un message est reçu puis renvoyé, les paramètres d'attribut SOAP font l'aller-retour uniquement pour les en-têtes du type <xref:System.ServiceModel.MessageHeader%601>.</span><span class="sxs-lookup"><span data-stu-id="11315-221">When a message is received and then sent back, the SOAP attribute settings only go round-trip for headers of the <xref:System.ServiceModel.MessageHeader%601> type.</span></span>  
  
## <a name="order-of-soap-body-parts"></a><span data-ttu-id="11315-222">Ordre des parties de corps SOAP</span><span class="sxs-lookup"><span data-stu-id="11315-222">Order of SOAP Body Parts</span></span>  
 <span data-ttu-id="11315-223">Dans certains cas, il peut s'avérer nécessaire de contrôler l'ordre des parties du corps.</span><span class="sxs-lookup"><span data-stu-id="11315-223">In some circumstances, you may need to control the order of the body parts.</span></span> <span data-ttu-id="11315-224">L'ordre des éléments du corps est alphabétique par défaut, mais peut être contrôlé par la propriété <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="11315-224">The order of the body elements is alphabetical by default, but can be controlled by the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="11315-225">Cette propriété a la même sémantique que la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType>, à l'exception du comportement dans les scénarios d'héritage (dans les contrats de message, les membres du corps du type de base ne sont pas triés avant les membres du corps du type dérivé).</span><span class="sxs-lookup"><span data-stu-id="11315-225">This property has the same semantics as the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> property, except for the behavior in inheritance scenarios (in message contracts, base type body members are not sorted before the derived type body members).</span></span> <span data-ttu-id="11315-226">Pour plus d’informations, consultez [commande des membres de données](data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="11315-226">For more information, see [Data Member Order](data-member-order.md).</span></span>  
  
 <span data-ttu-id="11315-227">Dans l'exemple suivant, `amount` viendrait normalement en premier car c'est le premier dans l'ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="11315-227">In the following example, `amount` would normally come first because it is first alphabetically.</span></span> <span data-ttu-id="11315-228">Cependant, la propriété <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> le met en troisième position.</span><span class="sxs-lookup"><span data-stu-id="11315-228">However, the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> property puts it into the third position.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember(Order=1)] public Account sourceAccount;  
  [MessageBodyMember(Order=2)] public Account targetAccount;  
  [MessageBodyMember(Order=3)] public int amount;  
}  
```  
  
## <a name="message-contract-versioning"></a><span data-ttu-id="11315-229">Contrôle de version des contrats de message</span><span class="sxs-lookup"><span data-stu-id="11315-229">Message Contract Versioning</span></span>  
 <span data-ttu-id="11315-230">Il peut parfois s'avérer nécessaire de modifier des contrats de message.</span><span class="sxs-lookup"><span data-stu-id="11315-230">Occasionally, you may need to change message contracts.</span></span> <span data-ttu-id="11315-231">Par exemple, une nouvelle version de votre application peut ajouter un en-tête supplémentaire à un message.</span><span class="sxs-lookup"><span data-stu-id="11315-231">For example, a new version of your application may add an extra header to a message.</span></span> <span data-ttu-id="11315-232">Ensuite, lors de l'envoi de la nouvelle version à l'ancienne, le système doit gérer en-tête supplémentaire, ainsi qu'un en-tête manquant lorsqu'il va dans l'autre direction.</span><span class="sxs-lookup"><span data-stu-id="11315-232">Then, when sending from the new version to the old, the system must deal with an extra header, as well as a missing header when going in the other direction.</span></span>  
  
 <span data-ttu-id="11315-233">Les règles suivantes s'appliquent pour le contrôle de version des en-têtes :</span><span class="sxs-lookup"><span data-stu-id="11315-233">The following rules apply for versioning headers:</span></span>  
  
- <span data-ttu-id="11315-234">WCF n’objet pas les en-têtes manquants : les membres correspondants sont conservés à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="11315-234">WCF does not object to the missing headers—the corresponding members are left at their default values.</span></span>  
  
- <span data-ttu-id="11315-235">WCF ignore également les en-têtes supplémentaires inattendus.</span><span class="sxs-lookup"><span data-stu-id="11315-235">WCF also ignores unexpected extra headers.</span></span> <span data-ttu-id="11315-236">La seule exception à cette règle est si l'en-tête supplémentaire a un attribut `MustUnderstand` défini à `true` dans le message SOAP entrant ; dans ce cas, une exception est levée car un en-tête qui doit être compris ne peut pas être traité.</span><span class="sxs-lookup"><span data-stu-id="11315-236">The one exception to this rule is if the extra header has a `MustUnderstand` attribute set to `true` in the incoming SOAP message—in this case, an exception is thrown because a header that must be understood cannot be processed.</span></span>  
  
 <span data-ttu-id="11315-237">Les corps de message ont des règles de contrôle de version similaires ; les parties de corps de message manquantes et supplémentaires sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="11315-237">Message bodies have similar versioning rules—both missing and additional message body parts are ignored.</span></span>  
  
## <a name="inheritance-considerations"></a><span data-ttu-id="11315-238">Considérations sur l'héritage</span><span class="sxs-lookup"><span data-stu-id="11315-238">Inheritance Considerations</span></span>  
 <span data-ttu-id="11315-239">Un type de contrat de message peut hériter d'un autre type, tant que le type de base a également un contrat de message.</span><span class="sxs-lookup"><span data-stu-id="11315-239">A message contract type can inherit from another type, as long as the base type also has a message contract.</span></span>  
  
 <span data-ttu-id="11315-240">Lors de la création ou de l'accès à un message à l'aide d'un type de contrat de message qui hérite d'autres types de contrats de message, les règles suivantes s'appliquent :</span><span class="sxs-lookup"><span data-stu-id="11315-240">When creating or accessing a message using a message contract type that inherits from other message contract types, the following rules apply:</span></span>  
  
- <span data-ttu-id="11315-241">Tous les en-têtes de message dans la hiérarchie d'héritage sont regroupés pour former le jeu complet d'en-têtes pour le message.</span><span class="sxs-lookup"><span data-stu-id="11315-241">All of the message headers in the inheritance hierarchy are collected together to form the full set of headers for the message.</span></span>  
  
- <span data-ttu-id="11315-242">Toutes les parties de corps du message dans la hiérarchie d'héritage sont regroupées pour former le corps du message complet.</span><span class="sxs-lookup"><span data-stu-id="11315-242">All of the message body parts in the inheritance hierarchy are collected together to form the full message body.</span></span> <span data-ttu-id="11315-243">Les parties du corps sont ordonnées conformément aux règles de classement habituelles (par la propriété <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType>, puis par ordre alphabétique), sans tenir compte de leur place dans la hiérarchie d'héritage.</span><span class="sxs-lookup"><span data-stu-id="11315-243">The body parts are ordered according to the usual ordering rules (by <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property and then alphabetical), with no relevance to their place in the inheritance hierarchy.</span></span> <span data-ttu-id="11315-244">L’utilisation d’un héritage de contrat de message dans lequel les parties de corps du message se produisent à plusieurs niveaux de l’arborescence d’héritage est fortement déconseillée.</span><span class="sxs-lookup"><span data-stu-id="11315-244">Using message contract inheritance where message body parts occur at multiple levels of the inheritance tree is strongly discouraged.</span></span> <span data-ttu-id="11315-245">Si une classe de base et une classe dérivée définissent un en-tête ou une partie du corps avec le même nom, le membre de la classe la plus de base est utilisé pour stocker la valeur de cet en-tête ou partie du corps.</span><span class="sxs-lookup"><span data-stu-id="11315-245">If a base class and a derived class define a header or a body part with the same name, the member from the base-most class is used to store the value of that header or body part.</span></span>  
  
 <span data-ttu-id="11315-246">Examinons les classes dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="11315-246">Consider the classes in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class PersonRecord  
{  
  [MessageHeader(Name="ID")] public int personID;  
  [MessageBodyMember] public string patientName;  
}  
  
[MessageContract]  
public class PatientRecord : PersonRecord  
{  
  [MessageHeader(Name="ID")] public int patientID;  
  [MessageBodyMember] public string diagnosis;  
}  
```  
  
 <span data-ttu-id="11315-247">La classe `PatientRecord` décrit un message avec un en-tête appelé `ID`.</span><span class="sxs-lookup"><span data-stu-id="11315-247">The `PatientRecord` class describes a message with one header called `ID`.</span></span> <span data-ttu-id="11315-248">L'en-tête correspond à `personID` et non pas au membre `patientID`, car le membre le plus de base est choisi.</span><span class="sxs-lookup"><span data-stu-id="11315-248">The header corresponds to the `personID` and not the `patientID` member, because the base-most member is chosen.</span></span> <span data-ttu-id="11315-249">Par conséquent, le champ `patientID` est inutile dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="11315-249">Thus, the `patientID` field is useless in this case.</span></span> <span data-ttu-id="11315-250">Le corps du message contient l'élément `diagnosis` suivi par l'élément `patientName`, car il s'agit de l'ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="11315-250">The body of the message contains the `diagnosis` element followed by the `patientName` element, because that is the alphabetical order.</span></span> <span data-ttu-id="11315-251">Notez que l'exemple présente un modèle qui est fortement déconseillé : les contrats de message de base et dérivés ont tous deux des parties de corps de message.</span><span class="sxs-lookup"><span data-stu-id="11315-251">Notice that the example shows a pattern that is strongly discouraged: both the base and the derived message contracts have message body parts.</span></span>  
  
## <a name="wsdl-considerations"></a><span data-ttu-id="11315-252">Considérations sur WSDL</span><span class="sxs-lookup"><span data-stu-id="11315-252">WSDL Considerations</span></span>  
 <span data-ttu-id="11315-253">Lors de la génération d’un contrat WSDL (Web Services Description Language) à partir d’un service qui utilise des contrats de message, il est important de se souvenir que les fonctionnalités de contrat de message ne sont pas toutes répercutées dans le WSDL résultant.</span><span class="sxs-lookup"><span data-stu-id="11315-253">When generating a Web Services Description Language (WSDL) contract from a service that uses message contracts, it is important to remember that not all message contract features are reflected in the resulting WSDL.</span></span> <span data-ttu-id="11315-254">Observez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="11315-254">Consider the following points:</span></span>  
  
- <span data-ttu-id="11315-255">WSDL ne peut pas exprimer le concept d'un tableau d'en-têtes.</span><span class="sxs-lookup"><span data-stu-id="11315-255">WSDL cannot express the concept of an array of headers.</span></span> <span data-ttu-id="11315-256">Lors de la création de messages avec un tableau d'en-têtes à l'aide de <xref:System.ServiceModel.MessageHeaderArrayAttribute>, le WSDL résultant ne reflète qu'un seul en-tête au lieu du tableau.</span><span class="sxs-lookup"><span data-stu-id="11315-256">When creating messages with an array of headers using the <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the resulting WSDL reflects only one header instead of the array.</span></span>  
  
- <span data-ttu-id="11315-257">Le document WSDL résultant ne reflète pas certaines informations de niveau de protection.</span><span class="sxs-lookup"><span data-stu-id="11315-257">The resulting WSDL document may not reflect some protection-level information.</span></span>  
  
- <span data-ttu-id="11315-258">Le type de message généré dans le WSDL a le même nom que le nom de la classe du type de contrat de message.</span><span class="sxs-lookup"><span data-stu-id="11315-258">The message type generated in the WSDL has the same name as the class name of the message contract type.</span></span>  
  
- <span data-ttu-id="11315-259">Lors de l'utilisation du même contrat de message dans plusieurs opérations, plusieurs types de message sont générés dans le document WSDL.</span><span class="sxs-lookup"><span data-stu-id="11315-259">When using the same message contract in multiple operations, multiple message types are generated in the WSDL document.</span></span> <span data-ttu-id="11315-260">Les noms sont rendus uniques en ajoutant les nombres « 2 », « 3 », et ainsi de suite, pour les utilisations suivantes.</span><span class="sxs-lookup"><span data-stu-id="11315-260">The names are made unique by adding the numbers "2", "3", and so on, for subsequent uses.</span></span> <span data-ttu-id="11315-261">Lors de la réimportation du WSDL, plusieurs types de contrats de message sont créés et sont identiques à l'exception de leurs noms.</span><span class="sxs-lookup"><span data-stu-id="11315-261">When importing back the WSDL, multiple message contract types are created and are identical except for their names.</span></span>  
  
## <a name="soap-encoding-considerations"></a><span data-ttu-id="11315-262">Considérations sur l'encodage SOAP</span><span class="sxs-lookup"><span data-stu-id="11315-262">SOAP Encoding Considerations</span></span>  
 <span data-ttu-id="11315-263">WCF vous permet d’utiliser le style d’encodage SOAP hérité de XML, mais son utilisation n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="11315-263">WCF allows you to use the legacy SOAP encoding style of XML, however, its use is not recommended.</span></span> <span data-ttu-id="11315-264">Lors de l'utilisation de ce style (en affectant à la propriété `Use` la valeur `Encoded` sur le <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> appliqué au contrat de service), les considérations supplémentaires suivantes s'appliquent :</span><span class="sxs-lookup"><span data-stu-id="11315-264">When using this style (by setting the `Use` property to `Encoded` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> applied to the service contract), the following additional considerations apply:</span></span>  
  
- <span data-ttu-id="11315-265">Les en-têtes de message ne sont pas pris en charge ; cela signifie que l'attribut <xref:System.ServiceModel.MessageHeaderAttribute> et l'attribut de tableau <xref:System.ServiceModel.MessageHeaderArrayAttribute> sont incompatibles avec l'encodage SOAP.</span><span class="sxs-lookup"><span data-stu-id="11315-265">The message headers are not supported; this means that the attribute <xref:System.ServiceModel.MessageHeaderAttribute> and the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute> are incompatible with SOAP encoding.</span></span>  
  
- <span data-ttu-id="11315-266">Si le contrat de message n'est pas encapsulé, c'est-à-dire, si la propriété <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> a la valeur `false`, le contrat de message ne peut avoir qu'une seule partie de corps.</span><span class="sxs-lookup"><span data-stu-id="11315-266">If the message contract is not wrapped, that is, if the property <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is set to `false`, the message contract can have only one body part.</span></span>  
  
- <span data-ttu-id="11315-267">Le nom de l'élément wrapper du contrat de message de demande doit correspondre au nom d'opération.</span><span class="sxs-lookup"><span data-stu-id="11315-267">The name of the wrapper element for the request message contract must match the operation name.</span></span> <span data-ttu-id="11315-268">Utilisez la propriété `WrapperName` du contrat de message à cette fin.</span><span class="sxs-lookup"><span data-stu-id="11315-268">Use the `WrapperName` property of the message contract for this.</span></span>  
  
- <span data-ttu-id="11315-269">Le nom de l'élément wrapper du contrat de message de réponse doit être le même que celui de l'opération suffixée par 'Response'.</span><span class="sxs-lookup"><span data-stu-id="11315-269">The name of the wrapper element for the response message contract must be the same as the name of the operation suffixed by 'Response'.</span></span> <span data-ttu-id="11315-270">Utilisez la propriété <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> du contrat de message à cette fin.</span><span class="sxs-lookup"><span data-stu-id="11315-270">Use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> property of the message contract for this.</span></span>  
  
- <span data-ttu-id="11315-271">L'encodage SOAP conserve les références d'objet.</span><span class="sxs-lookup"><span data-stu-id="11315-271">SOAP encoding preserves object references.</span></span> <span data-ttu-id="11315-272">Par exemple, prenons le code suivant.</span><span class="sxs-lookup"><span data-stu-id="11315-272">For example, consider the following code.</span></span>  
  
    ```csharp  
    [MessageContract(WrapperName="updateChangeRecord")]  
    public class ChangeRecordRequest  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    [MessageContract(WrapperName="updateChangeRecordResponse")]  
    public class ChangeRecordResponse  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    // application code:  
    ChangeRecordRequest cr = new ChangeRecordRequest();  
    Person p = new Person("John Doe");  
    cr.changedBy=p;  
    cr.changedFrom=p;  
    cr.changedTo=p;  
    ```  
  
 <span data-ttu-id="11315-273">Après avoir sérialisé le message à l'aide de l'encodage SOAP, `changedFrom` et `changedTo` ne contiennent pas leurs propres copies de `p`, mais pointent à la place sur la copie à l'intérieur de l'élément `changedBy`.</span><span class="sxs-lookup"><span data-stu-id="11315-273">After serializing the message using SOAP encoding, `changedFrom` and `changedTo` do not contain their own copies of `p`, but instead point to the copy inside the `changedBy` element.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="11315-274">Considérations relatives aux performances</span><span class="sxs-lookup"><span data-stu-id="11315-274">Performance Considerations</span></span>  
 <span data-ttu-id="11315-275">Chaque partie de corps du message et en-tête de message est sérialisé indépendamment des autres.</span><span class="sxs-lookup"><span data-stu-id="11315-275">Every message header and message body part is serialized independently of the others.</span></span> <span data-ttu-id="11315-276">Par conséquent, des espaces de noms identiques peuvent être à nouveau déclarés pour chaque en-tête et partie du corps.</span><span class="sxs-lookup"><span data-stu-id="11315-276">Therefore, the same namespaces can be declared again for each header and body part.</span></span> <span data-ttu-id="11315-277">Pour améliorer les performances, tout particulièrement en termes de taille du message sur le câble, consolidez plusieurs en-têtes et parties de corps dans un en-tête ou une partie de corps unique.</span><span class="sxs-lookup"><span data-stu-id="11315-277">To improve performance, especially in terms of the size of the message on the wire, consolidate multiple headers and body parts into a single header or body part.</span></span> <span data-ttu-id="11315-278">Par exemple, à la place du code suivant :</span><span class="sxs-lookup"><span data-stu-id="11315-278">For example, instead of the following code:</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public Account sourceAccount;  
  [MessageBodyMember] public Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 <span data-ttu-id="11315-279">Utilisez celui-ci.</span><span class="sxs-lookup"><span data-stu-id="11315-279">Use this code.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public OperationDetails details;  
}  
  
[DataContract]  
public class OperationDetails  
{  
  [DataMember] public Account sourceAccount;  
  [DataMember] public Account targetAccount;  
  [DataMember] public int amount;  
}  
```  
  
### <a name="event-based-asynchronous-and-message-contracts"></a><span data-ttu-id="11315-280">Contrats de message et modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="11315-280">Event-based Asynchronous and Message Contracts</span></span>  
 <span data-ttu-id="11315-281">Les règles de conception pour le modèle asynchrone basé sur les événements stipulent que si plusieurs valeurs sont retournées, une valeur est retournée comme la propriété `Result` et les autres sont retournées comme les propriétés sur l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="11315-281">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="11315-282">Il en découle que si un client importe des métadonnées à l'aide des options de commande asynchrone basées sur les événements et que l'opération retourne plusieurs valeurs, l'objet <xref:System.EventArgs> par défaut retourne une valeur comme la propriété `Result` et le reste sont des propriétés de l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="11315-282">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="11315-283">Pour recevoir l'objet message comme la propriété `Result` et que les valeurs retournées sur cet objet soient des propriétés, utilisez l'option de commande `/messageContract`.</span><span class="sxs-lookup"><span data-stu-id="11315-283">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="11315-284">Cette opération génère une signature qui retourne le message de réponse comme la propriété `Result` sur l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="11315-284">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="11315-285">Toutes les valeurs de retour internes sont ensuite des propriétés de l'objet de message de réponse.</span><span class="sxs-lookup"><span data-stu-id="11315-285">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11315-286">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11315-286">See also</span></span>

- [<span data-ttu-id="11315-287">Using Data Contracts</span><span class="sxs-lookup"><span data-stu-id="11315-287">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="11315-288">Conception et implémentation de services</span><span class="sxs-lookup"><span data-stu-id="11315-288">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
