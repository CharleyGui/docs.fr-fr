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
# <a name="using-message-contracts"></a>Utilisation de contrats de message
En général, lors de la création d’applications Windows Communication Foundation (WCF), les développeurs prêtent une attention particulière aux structures de données et aux problèmes de sérialisation, et n’ont pas besoin de se préoccuper de la structure des messages dans lesquels les données sont transportées. Pour ces applications, créer des contrats de données pour les paramètres ou les valeurs de retour est une procédure simple. (Pour plus d’informations, consultez [spécification d’transfert de données dans les contrats de service](specifying-data-transfer-in-service-contracts.md).)  
  
 Toutefois, le contrôle complet sur la structure d'un message SOAP est parfois aussi important que celui sur son contenu. Cela se vérifie tout particulièrement lorsque l'interopérabilité est importante ou pour contrôler spécifiquement des problèmes de sécurité au niveau du message ou de la partie de message. Dans ce cas, vous pouvez créer un *contrat de message* qui vous permet de spécifier la structure du message SOAP précis requis.  
  
 Cette rubrique explique comment utiliser les divers attributs de contrat de message afin de créer un contrat de message spécifique pour votre opération.  
  
## <a name="using-message-contracts-in-operations"></a>Utilisation de contrats de message dans les opérations  
 WCF prend en charge les opérations modélisées sur le *style d’appel de procédure distante (RPC)* ou le *style de messagerie*. Dans une opération de style RPC, vous pouvez utiliser n’importe quel type sérialisable, et vous avez accès aux fonctionnalités disponibles aux appels locaux, tels que plusieurs paramètres et les paramètres `ref` et `out`. Dans ce style, le formulaire de sérialisation choisi contrôle la structure des données dans les messages sous-jacents, et le runtime WCF crée les messages pour prendre en charge l’opération. Cela permet aux développeurs qui ne sont pas familiarisés avec SOAP et les messages SOAP de créer et d'utiliser rapidement et facilement des applications de service.  
  
 L'exemple de code suivant présente une opération de service modélisée sur le style RPC.  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 Habituellement, un contrat de données est suffisant pour définir le schéma des messages. Par exemple, cela est suffisant pour la plupart des applications dans l'exemple précédent si `BankingTransaction` et `BankingTransactionResponse` ont des contrats de données pour définir le contenu des messages SOAP sous-jacents. Pour plus d’informations sur les contrats de données, consultez [utilisation de contrats de données](using-data-contracts.md).  
  
 Toutefois, il peut parfois s'avérer nécessaire de contrôler de manière précise la façon dont la structure du message SOAP est transmise sur le réseau. Le scénario le plus courant dans ce cas consiste à insérer des en-têtes SOAP personnalisés. Un autre consiste à définir des propriétés de sécurité pour le corps et les en-têtes du message, c'est à-dire, à déterminer si ces éléments sont chiffrés et signés numériquement. Enfin, certaines piles SOAP tiers requièrent que les messages soient dans un format spécifique. Les opérations de style de messagerie fournissent ce contrôle.  
  
 Une opération de style de messagerie a au plus un paramètre et une valeur de retour où les deux types sont des types de messages ; autrement dit, ils sérialisent directement dans une structure de message SOAP spécifiée. Il peut s'agir de n'importe quel type marqué avec le type <xref:System.ServiceModel.MessageContractAttribute> ou <xref:System.ServiceModel.Channels.Message>. L'exemple de code suivant présente une opération similaire au style RCP précédent, mais qui utilise le style de messagerie.  
  
 Par exemple, si `BankingTransaction` et `BankingTransactionResponse` sont les deux types qui sont des contrats de message, alors le code dans les opérations suivantes est valide.  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 Toutefois, le code suivant n'est pas valide.  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 Une exception est levée pour toute opération qui implique un type de contrat de message et ne suit pas l’un des modèles valides. Bien évidemment, les opérations qui n'impliquent pas de types de contrats de message ne sont pas soumises à ces restrictions.  
  
 Si un type dispose à la fois d'un contrat de message et d'un contrat de données, seul son contrat de message est pris en compte lorsque le type est utilisé dans une opération.  
  
## <a name="defining-message-contracts"></a>Définition de contrats de message  
 Pour définir un contrat de message pour un type (autrement dit, définir le mappage entre le type et une enveloppe SOAP), appliquez <xref:System.ServiceModel.MessageContractAttribute> au type. Puis appliquez <xref:System.ServiceModel.MessageHeaderAttribute> aux membres du type que vous souhaitez créer dans les en-têtes SOAP et appliquez <xref:System.ServiceModel.MessageBodyMemberAttribute> aux membres que vous souhaitez créer dans les parties du corps SOAP du message.  
  
 Le code suivant fournit un exemple d'utilisation d'un contrat de message.  
  
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
  
 En utilisant ce type comme paramètre d'opération, l'enveloppe SOAP suivante est générée :  
  
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
  
 Notez que `operation` et `transactionDate` apparaissent comme des en-têtes SOAP et le corps SOAP se compose d'un élément wrapper `BankingTransaction` contenant `sourceAccount`,`targetAccount` et `amount`.  
  
 Vous pouvez appliquer <xref:System.ServiceModel.MessageHeaderAttribute> et <xref:System.ServiceModel.MessageBodyMemberAttribute> à l'ensemble des champs, propriétés et événements, indépendamment du fait qu'ils soient publics, privés, protégés ou internes.  
  
 <xref:System.ServiceModel.MessageContractAttribute> vous permet de spécifier les attributs WrapperName et WrapperNamespace qui contrôlent le nom de l'élément wrapper dans le corps du message SOAP. Par défaut le nom du type de contrat de message est utilisé pour le wrapper et l'espace de noms dans lequel le contrat de message est défini `http://tempuri.org/` est utilisé comme espace de noms par défaut.  
  
> [!NOTE]
> Les attributs <xref:System.Runtime.Serialization.KnownTypeAttribute> sont ignorés dans les contrats de message. Si un <xref:System.Runtime.Serialization.KnownTypeAttribute> est requis, placez-le sur l'opération qui utilise le contrat de message en question.  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a>Contrôle des espaces de noms et noms des en-têtes et parties du corps  
 Dans la représentation SOAP d'un contrat de message, chaque en-tête et le partie du corps mappe à un élément XML ayant un nom et un espace de noms.  
  
 Par défaut, l'espace de noms est le même que celui du contrat de service auquel le message participe, et le nom est déterminé par le nom de membre auquel les attributs <xref:System.ServiceModel.MessageHeaderAttribute> ou <xref:System.ServiceModel.MessageBodyMemberAttribute> sont appliqués.  
  
 Vous pouvez modifier ces valeurs par défaut en manipulant <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> et <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (sur la classe parente des attributs <xref:System.ServiceModel.MessageHeaderAttribute> et <xref:System.ServiceModel.MessageBodyMemberAttribute>).  
  
 Examinons la classe dans l'exemple de code suivant :  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 Dans cet exemple, l'en-tête `IsAudited` est dans l'espace de noms spécifié dans le code, et le corps qui représente le membre `theData` est représenté par un élément XML avec le nom `transactionData`. Le code suivant montre le XML généré pour ce contrat de message.  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a>Contrôle de l'encapsulation des parties de corps SOAP  
 Par défaut, les parties de corps SOAP sont sérialisées à l'intérieur d'un élément encapsulé. Par exemple, le code suivant affiche l'élément wrapper `HelloGreetingMessage` généré à partir du nom du type <xref:System.ServiceModel.MessageContractAttribute> dans le contrat de message du message `HelloGreetingMessage`.  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 Pour supprimer l'élément wrapper, affectez <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> à la propriété `false`. Pour contrôler le nom et l'espace de noms de l'élément wrapper, utilisez les propriétés <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> et <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A>.  
  
> [!NOTE]
> La présence de plusieurs parties de corps de messages non encapsulées n'est pas conforme à WS-I Basic Profile 1.1 et n'est pas recommandée lors de la conception de nouveaux contrats de message. Toutefois, il peut s'avérer nécessaire d'avoir plusieurs parties de corps du message non encapsulées dans certains scénarios d'interopérabilité spécifiques. Si vous prévoyez de transmettre plusieurs éléments de données dans un corps de message, il est recommandé d'utiliser le mode (encapsulé) par défaut. La présence de plusieurs en-têtes de message dans des messages non encapsulés est complètement acceptable.  
  
## <a name="using-custom-types-inside-message-contracts"></a>Utilisation de types personnalisés dans des contrats de message  
 Chaque partie de corps de message et en-tête de message individuel est sérialisé (converti en XML) à l'aide du moteur de sérialisation choisi du contrat de service dans lequel le message est utilisé. Le moteur de sérialisation par défaut, `XmlFormatter`, peut gérer n'importe quel type ayant un contrat de données, soit explicitement (en ayant <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) ou implicitement (en étant un type primitif, en ayant <xref:System.SerializableAttribute?displayProperty=nameWithType>, etc.). Pour plus d’informations, consultez [utilisation de contrats de données](using-data-contracts.md).  
  
 Dans l'exemple précédent, les types `Operation` et `BankingTransactionData` doivent avoir un contrat de données, et `transactionDate` est sérialisable car <xref:System.DateTime> est un type primitif (et a ainsi un contrat de données implicite).  
  
 Cependant, il est possible de basculer sur un autre moteur de sérialisation, `XmlSerializer`. Dans ce cas, vous devez vous assurer que tous les types utilisés pour les en-têtes de message et les parties du corps sont sérialisables à l'aide de `XmlSerializer`.  
  
## <a name="using-arrays-inside-message-contracts"></a>Utilisation de tableaux dans des contrats de message  
 Vous pouvez utiliser des tableaux d'éléments répétitifs dans des contrats de message de deux manières différentes.  
  
 La première méthode consiste à utiliser <xref:System.ServiceModel.MessageHeaderAttribute> ou <xref:System.ServiceModel.MessageBodyMemberAttribute> directement sur le tableau. Dans ce cas, l'ensemble du tableau est sérialisé comme un seul élément (c'est-à-dire, un seul en-tête ou un seul corps) avec plusieurs éléments enfants. Examinons la classe dans l'exemple suivant :  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 Les en-têtes SOAP sont similaires aux éléments suivants.  
  
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
  
 L'autre méthode consiste à utiliser <xref:System.ServiceModel.MessageHeaderArrayAttribute>. Dans ce cas, chaque élément de tableau est sérialisé indépendamment et de manière à n'avoir qu'un seul en-tête comme suit.  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 Le nom par défaut des entrées de tableau correspond à celui du membre auquel l'attribut <xref:System.ServiceModel.MessageHeaderArrayAttribute> est appliqué.  
  
 L'attribut <xref:System.ServiceModel.MessageHeaderArrayAttribute> hérite de <xref:System.ServiceModel.MessageHeaderAttribute>. Il a le même jeu de fonctionnalités que les attributs non-tableau ; il est possible, par exemple, de définir l’ordre, le nom et l’espace de noms d’un tableau d’en-têtes de la même façon que pour un en-tête unique. Lorsque vous utilisez la propriété `Order` sur un tableau, elle s'applique à l'ensemble de celui-ci.  
  
 Vous ne pouvez appliquer <xref:System.ServiceModel.MessageHeaderArrayAttribute> qu’aux tableaux, et non pas aux collections.  
  
## <a name="using-byte-arrays-in-message-contracts"></a>Utilisation de tableaux d'octets dans des contrats de message  
 Les tableaux d'octets, lorsqu'ils sont utilisés avec des attributs non-tableau (<xref:System.ServiceModel.MessageBodyMemberAttribute> et <xref:System.ServiceModel.MessageHeaderAttribute>), ne sont pas traités comme des tableaux mais comme un type primitif spécial représenté sous forme de données encodées en base 64 dans le XML résultant.  
  
 Lorsque vous utilisez des tableaux d'octets avec l'attribut de tableau <xref:System.ServiceModel.MessageHeaderArrayAttribute>, les résultats varient en fonction du sérialiseur utilisé. Avec le sérialiseur par défaut, le tableau est représenté sous forme d'une entrée individuelle pour chaque octet. Toutefois, lorsque `XmlSerializer` est sélectionné, (à l'aide de <xref:System.ServiceModel.XmlSerializerFormatAttribute> sur le contrat de service), les tableaux d'octets sont traités comme des données Base64, indépendamment de l'utilisation d'attributs de tableau ou non-tableau.  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a>Signature et chiffrement des parties du message  
 Un contrat de message peut indiquer si les en-têtes et/ou le corps du message doivent être signés numériquement et chiffrés.  
  
 Pour ce faire, définissez la propriété <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> sur les attributs <xref:System.ServiceModel.MessageHeaderAttribute> et <xref:System.ServiceModel.MessageBodyMemberAttribute>. La propriété est une énumération du type <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> et peut être définie à <xref:System.Net.Security.ProtectionLevel.None> (pas de chiffrement ni de signature), <xref:System.Net.Security.ProtectionLevel.Sign> (signature numérique uniquement) ou <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (chiffrement et signature numérique). Par défaut, il s’agit de <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Pour que ces fonctionnalités de sécurité fonctionnent, vous devez configurer la liaison et les comportements correctement. Si vous utilisez ces fonctionnalités de sécurité sans configuration correcte (par exemple, essayer de signer un message sans fournir vos informations d’identification), une exception est levée lors de la validation.  
  
 Pour les en-têtes de message, le niveau de protection est déterminé individuellement pour chaque en-tête.  
  
 Pour les parties de corps de message, le niveau de protection peut être considéré comme le « niveau de protection minimal ». Le corps a un seul niveau de protection, quel que soit le nombre de parties du corps. Le niveau de protection du corps est déterminé par le paramètre de propriété <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> le plus élevé de toutes les parties du corps. Toutefois, vous devez définir le niveau de protection de chaque partie du corps au niveau de protection minimal réel requis.  
  
 Examinons la classe dans l'exemple de code suivant :  
  
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
  
 Dans cet exemple, l'en-tête `recordID` n'est pas protégé, `patientName` est `signed`, et `SSN` est chiffré et signé. `medicalHistory` étant appliqué sur au moins une partie du corps (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>), l'ensemble du message est donc chiffré et signé, même si les commentaires et les parties de corps de diagnostic spécifient des niveaux de protection inférieurs.  
  
## <a name="soap-action"></a>Action SOAP  
 SOAP et les standards de services Web associés définissent une propriété appelée `Action` qui peut être présente pour chaque message SOAP envoyé. Les propriétés <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> et <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> de l'opération contrôlent la valeur de cette propriété.  
  
## <a name="soap-header-attributes"></a>Attributs d'en-tête SOAP  
 Le standard SOAP définit les attributs suivants qui peuvent exister dans un en-tête :  
  
- `Actor/Role` (`Actor` dans SOAP 1.1, `Role` dans SOAP 1.2)  
  
- `MustUnderstand`  
  
- `Relay`  
  
 L'attribut `Actor` ou `Role` spécifie l'URI (Uniform Resource Identifier) du nœud auquel un en-tête donné est destiné. L'attribut `MustUnderstand` spécifie si le nœud qui traite cet en-tête doit le comprendre. L'attribut `Relay` spécifie si l'en-tête sera relayé aux nœuds en aval. WCF n’effectue aucun traitement de ces attributs sur les messages entrants, à l’exception de l' `MustUnderstand` attribut, tel que spécifié dans la section « contrôle de version des contrats de message » plus loin dans cette rubrique. Toutefois, il vous permet de lire et d'écrire ces attributs si nécessaire, comme dans la description suivante.  
  
 Lors de l'envoi d'un message, ces attributs ne sont pas émis par défaut. Vous pouvez modifier ce paramètre de deux façons : La première méthode consiste à affecter statiquement aux attributs les valeurs souhaitées en modifiant les propriétés <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType> et <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType>, tel qu'indiqué dans l'exemple de code suivant. (Notez qu'il n'y a pas de propriété `Role` ; la définition de la propriété <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> entraîne l'émission de l'attribut `Role` si vous utilisez SOAP 1.2).  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 La deuxième méthode permettant de contrôler ces attributs s'appuie sur un mécanisme dynamique, via le code. Pour ce faire, encapsulez le type d'en-tête souhaité dans le type <xref:System.ServiceModel.MessageHeader%601> (assurez-vous de ne pas confondre ce type avec la version non générique), puis utilisez le type avec <xref:System.ServiceModel.MessageHeaderAttribute>. Puis, utilisez des propriétés sur <xref:System.ServiceModel.MessageHeader%601> pour définir les attributs SOAP, tel qu'indiqué dans l'exemple de code suivant.  
  
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
  
 Si vous utilisez à la fois les mécanismes de contrôle dynamique et statique, les paramètres statiques sont utilisés comme valeur par défaut mais peuvent être substitués ultérieurement en utilisant le mécanisme dynamique, tel qu'indiqué dans le code suivant.  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 La création d'en-têtes répétés avec contrôle d'attribut dynamique est autorisée, tel qu'indiqué dans le code suivant.  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 Côté réception, la lecture de ces attributs SOAP peut être faite uniquement si la classe <xref:System.ServiceModel.MessageHeader%601> est utilisée pour l'en-tête dans le type. Examinez les propriétés `Actor`, `Relay` ou `MustUnderstand` d'un en-tête du type <xref:System.ServiceModel.MessageHeader%601> pour découvrir les paramètres d'attribut sur le message reçu.  
  
 Lorsqu'un message est reçu puis renvoyé, les paramètres d'attribut SOAP font l'aller-retour uniquement pour les en-têtes du type <xref:System.ServiceModel.MessageHeader%601>.  
  
## <a name="order-of-soap-body-parts"></a>Ordre des parties de corps SOAP  
 Dans certains cas, il peut s'avérer nécessaire de contrôler l'ordre des parties du corps. L'ordre des éléments du corps est alphabétique par défaut, mais peut être contrôlé par la propriété <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType>. Cette propriété a la même sémantique que la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType>, à l'exception du comportement dans les scénarios d'héritage (dans les contrats de message, les membres du corps du type de base ne sont pas triés avant les membres du corps du type dérivé). Pour plus d’informations, consultez [commande des membres de données](data-member-order.md).  
  
 Dans l'exemple suivant, `amount` viendrait normalement en premier car c'est le premier dans l'ordre alphabétique. Cependant, la propriété <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> le met en troisième position.  
  
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
  
## <a name="message-contract-versioning"></a>Contrôle de version des contrats de message  
 Il peut parfois s'avérer nécessaire de modifier des contrats de message. Par exemple, une nouvelle version de votre application peut ajouter un en-tête supplémentaire à un message. Ensuite, lors de l'envoi de la nouvelle version à l'ancienne, le système doit gérer en-tête supplémentaire, ainsi qu'un en-tête manquant lorsqu'il va dans l'autre direction.  
  
 Les règles suivantes s'appliquent pour le contrôle de version des en-têtes :  
  
- WCF n’objet pas les en-têtes manquants : les membres correspondants sont conservés à leurs valeurs par défaut.  
  
- WCF ignore également les en-têtes supplémentaires inattendus. La seule exception à cette règle est si l'en-tête supplémentaire a un attribut `MustUnderstand` défini à `true` dans le message SOAP entrant ; dans ce cas, une exception est levée car un en-tête qui doit être compris ne peut pas être traité.  
  
 Les corps de message ont des règles de contrôle de version similaires ; les parties de corps de message manquantes et supplémentaires sont ignorées.  
  
## <a name="inheritance-considerations"></a>Considérations sur l'héritage  
 Un type de contrat de message peut hériter d'un autre type, tant que le type de base a également un contrat de message.  
  
 Lors de la création ou de l'accès à un message à l'aide d'un type de contrat de message qui hérite d'autres types de contrats de message, les règles suivantes s'appliquent :  
  
- Tous les en-têtes de message dans la hiérarchie d'héritage sont regroupés pour former le jeu complet d'en-têtes pour le message.  
  
- Toutes les parties de corps du message dans la hiérarchie d'héritage sont regroupées pour former le corps du message complet. Les parties du corps sont ordonnées conformément aux règles de classement habituelles (par la propriété <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType>, puis par ordre alphabétique), sans tenir compte de leur place dans la hiérarchie d'héritage. L’utilisation d’un héritage de contrat de message dans lequel les parties de corps du message se produisent à plusieurs niveaux de l’arborescence d’héritage est fortement déconseillée. Si une classe de base et une classe dérivée définissent un en-tête ou une partie du corps avec le même nom, le membre de la classe la plus de base est utilisé pour stocker la valeur de cet en-tête ou partie du corps.  
  
 Examinons les classes dans l'exemple de code suivant.  
  
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
  
 La classe `PatientRecord` décrit un message avec un en-tête appelé `ID`. L'en-tête correspond à `personID` et non pas au membre `patientID`, car le membre le plus de base est choisi. Par conséquent, le champ `patientID` est inutile dans ce cas. Le corps du message contient l'élément `diagnosis` suivi par l'élément `patientName`, car il s'agit de l'ordre alphabétique. Notez que l'exemple présente un modèle qui est fortement déconseillé : les contrats de message de base et dérivés ont tous deux des parties de corps de message.  
  
## <a name="wsdl-considerations"></a>Considérations sur WSDL  
 Lors de la génération d’un contrat WSDL (Web Services Description Language) à partir d’un service qui utilise des contrats de message, il est important de se souvenir que les fonctionnalités de contrat de message ne sont pas toutes répercutées dans le WSDL résultant. Observez les points suivants :  
  
- WSDL ne peut pas exprimer le concept d'un tableau d'en-têtes. Lors de la création de messages avec un tableau d'en-têtes à l'aide de <xref:System.ServiceModel.MessageHeaderArrayAttribute>, le WSDL résultant ne reflète qu'un seul en-tête au lieu du tableau.  
  
- Le document WSDL résultant ne reflète pas certaines informations de niveau de protection.  
  
- Le type de message généré dans le WSDL a le même nom que le nom de la classe du type de contrat de message.  
  
- Lors de l'utilisation du même contrat de message dans plusieurs opérations, plusieurs types de message sont générés dans le document WSDL. Les noms sont rendus uniques en ajoutant les nombres « 2 », « 3 », et ainsi de suite, pour les utilisations suivantes. Lors de la réimportation du WSDL, plusieurs types de contrats de message sont créés et sont identiques à l'exception de leurs noms.  
  
## <a name="soap-encoding-considerations"></a>Considérations sur l'encodage SOAP  
 WCF vous permet d’utiliser le style d’encodage SOAP hérité de XML, mais son utilisation n’est pas recommandée. Lors de l'utilisation de ce style (en affectant à la propriété `Use` la valeur `Encoded` sur le <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> appliqué au contrat de service), les considérations supplémentaires suivantes s'appliquent :  
  
- Les en-têtes de message ne sont pas pris en charge ; cela signifie que l'attribut <xref:System.ServiceModel.MessageHeaderAttribute> et l'attribut de tableau <xref:System.ServiceModel.MessageHeaderArrayAttribute> sont incompatibles avec l'encodage SOAP.  
  
- Si le contrat de message n'est pas encapsulé, c'est-à-dire, si la propriété <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> a la valeur `false`, le contrat de message ne peut avoir qu'une seule partie de corps.  
  
- Le nom de l'élément wrapper du contrat de message de demande doit correspondre au nom d'opération. Utilisez la propriété `WrapperName` du contrat de message à cette fin.  
  
- Le nom de l'élément wrapper du contrat de message de réponse doit être le même que celui de l'opération suffixée par 'Response'. Utilisez la propriété <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> du contrat de message à cette fin.  
  
- L'encodage SOAP conserve les références d'objet. Par exemple, prenons le code suivant.  
  
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
  
 Après avoir sérialisé le message à l'aide de l'encodage SOAP, `changedFrom` et `changedTo` ne contiennent pas leurs propres copies de `p`, mais pointent à la place sur la copie à l'intérieur de l'élément `changedBy`.  
  
## <a name="performance-considerations"></a>Considérations relatives aux performances  
 Chaque partie de corps du message et en-tête de message est sérialisé indépendamment des autres. Par conséquent, des espaces de noms identiques peuvent être à nouveau déclarés pour chaque en-tête et partie du corps. Pour améliorer les performances, tout particulièrement en termes de taille du message sur le câble, consolidez plusieurs en-têtes et parties de corps dans un en-tête ou une partie de corps unique. Par exemple, à la place du code suivant :  
  
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
  
 Utilisez celui-ci.  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a>Contrats de message et modèle asynchrone basé sur les événements  
 Les règles de conception pour le modèle asynchrone basé sur les événements stipulent que si plusieurs valeurs sont retournées, une valeur est retournée comme la propriété `Result` et les autres sont retournées comme les propriétés sur l'objet <xref:System.EventArgs>. Il en découle que si un client importe des métadonnées à l'aide des options de commande asynchrone basées sur les événements et que l'opération retourne plusieurs valeurs, l'objet <xref:System.EventArgs> par défaut retourne une valeur comme la propriété `Result` et le reste sont des propriétés de l'objet <xref:System.EventArgs>.  
  
 Pour recevoir l'objet message comme la propriété `Result` et que les valeurs retournées sur cet objet soient des propriétés, utilisez l'option de commande `/messageContract`. Cette opération génère une signature qui retourne le message de réponse comme la propriété `Result` sur l'objet <xref:System.EventArgs>. Toutes les valeurs de retour internes sont ensuite des propriétés de l'objet de message de réponse.  
  
## <a name="see-also"></a>Voir aussi

- [Using Data Contracts](using-data-contracts.md)
- [Conception et implémentation de services](../designing-and-implementing-services.md)
