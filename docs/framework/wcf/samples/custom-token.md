---
title: Custom Token
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: 1a8c312248b0c15bb2e366a3d9925014556b6dd8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553159"
---
# <a name="custom-token"></a><span data-ttu-id="37084-102">Custom Token</span><span class="sxs-lookup"><span data-stu-id="37084-102">Custom Token</span></span>

<span data-ttu-id="37084-103">Cet exemple montre comment ajouter une implémentation de jeton personnalisée dans une application Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="37084-103">This sample demonstrates how to add a custom token implementation into a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="37084-104">Cet exemple utilise un `CreditCardToken` pour transmettre de manière sécurisée les informations de carte de crédit du client au service.</span><span class="sxs-lookup"><span data-stu-id="37084-104">The example uses a `CreditCardToken` to securely pass information about client credit cards to the service.</span></span> <span data-ttu-id="37084-105">Le jeton est transmis dans l’en-tête de message WS-Security. Il est signé et chiffré à l’aide de l’élément de liaison de sécurité symétrique en même temps que le corps du message et que les autres en-têtes de message.</span><span class="sxs-lookup"><span data-stu-id="37084-105">The token is passed in the WS-Security message header and is signed and encrypted using the symmetric security binding element along with message body and other message headers.</span></span> <span data-ttu-id="37084-106">Cette particularité est utile lorsque les jetons intégrés ne sont pas suffisants.</span><span class="sxs-lookup"><span data-stu-id="37084-106">This is useful in cases where the built-in tokens are not sufficient.</span></span> <span data-ttu-id="37084-107">Cet exemple illustre comment fournir un jeton de sécurité personnalisé à un service au lieu d'utiliser l'un des jetons intégrés.</span><span class="sxs-lookup"><span data-stu-id="37084-107">This sample demonstrates how to provide a custom security token to a service instead of using one of the built-in tokens.</span></span> <span data-ttu-id="37084-108">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="37084-108">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="37084-109">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="37084-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="37084-110">En résumé, cet exemple montre :</span><span class="sxs-lookup"><span data-stu-id="37084-110">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="37084-111">Comment un client peut transmettre un jeton de sécurité personnalisé à un service.</span><span class="sxs-lookup"><span data-stu-id="37084-111">How a client can pass a custom security token to a service.</span></span>

- <span data-ttu-id="37084-112">Comment le service peut consommer et valider un jeton de sécurité personnalisé.</span><span class="sxs-lookup"><span data-stu-id="37084-112">How the service can consume and validate a custom security token.</span></span>

- <span data-ttu-id="37084-113">Comment le code de service WCF peut obtenir les informations sur les jetons de sécurité reçus, y compris le jeton de sécurité personnalisé.</span><span class="sxs-lookup"><span data-stu-id="37084-113">How the WCF service code can obtain the information about received security tokens including the custom security token.</span></span>

- <span data-ttu-id="37084-114">Comment le certificat X.509 du serveur permet de protéger la clé symétrique utilisée pour la signature et le chiffrement des messages.</span><span class="sxs-lookup"><span data-stu-id="37084-114">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

## <a name="client-authentication-using-a-custom-security-token"></a><span data-ttu-id="37084-115">Authentification du client à l'aide d'un jeton de sécurité personnalisé</span><span class="sxs-lookup"><span data-stu-id="37084-115">Client Authentication Using a Custom Security Token</span></span>

 <span data-ttu-id="37084-116">Le service expose un point de terminaison unique qui est créé par programme à l'aide des classes `BindingHelper` et `EchoServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="37084-116">The service exposes a single endpoint that is programmatically created using `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="37084-117">Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat.</span><span class="sxs-lookup"><span data-stu-id="37084-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="37084-118">La liaison est configurée avec une liaison personnalisé à l'aide de `SymmetricSecurityBindingElement` et `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="37084-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="37084-119">Dans cet exemple, l'élément `SymmetricSecurityBindingElement` est configuré pour utiliser un certificat X.509 de service afin de protéger la clé symétrique pendant la transmission et de transmettre le `CreditCardToken` personnalisé dans un en-tête de message WS-Security sous forme de jeton de sécurité signé et chiffré.</span><span class="sxs-lookup"><span data-stu-id="37084-119">This sample sets the `SymmetricSecurityBindingElement` to use a service's X.509 certificate to protect the symmetric key during transmission and to pass a custom `CreditCardToken` in a WS-Security message header as a signed and encrypted security token.</span></span> <span data-ttu-id="37084-120">Le comportement spécifie les informations d'identification du service qui doivent être utilisées pour l'authentification du client ainsi que les informations sur le certificat X.509 du service.</span><span class="sxs-lookup"><span data-stu-id="37084-120">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span>

```csharp
public static class BindingHelper
{
    public static Binding CreateCreditCardBinding()
    {
        var httpTransport = new HttpTransportBindingElement();

        // The message security binding element will be configured to require a credit card.
        // The token that is encrypted with the service's certificate.
        var messageSecurity = new SymmetricSecurityBindingElement();
        messageSecurity.EndpointSupportingTokenParameters.SignedEncrypted.Add(new CreditCardTokenParameters());
        X509SecurityTokenParameters x509ProtectionParameters = new X509SecurityTokenParameters();
        x509ProtectionParameters.InclusionMode = SecurityTokenInclusionMode.Never;
        messageSecurity.ProtectionTokenParameters = x509ProtectionParameters;
        return new CustomBinding(messageSecurity, httpTransport);
    }
}
```

 <span data-ttu-id="37084-121">Pour consommer le jeton de carte de crédit figurant dans le message, l'exemple utilise les informations d'identification personnalisées du service.</span><span class="sxs-lookup"><span data-stu-id="37084-121">To consume a credit card token in the message, the sample uses custom service credentials to provide this functionality.</span></span> <span data-ttu-id="37084-122">La classe d’informations d’identification du service se trouve dans la classe `CreditCardServiceCredentials`. Elle est ajoutée aux collections de comportements de l’hôte de service dans la méthode `EchoServiceHost.InitializeRuntime`.</span><span class="sxs-lookup"><span data-stu-id="37084-122">The service credentials class is located in the `CreditCardServiceCredentials` class and is added to the behaviors collections of the service host in the `EchoServiceHost.InitializeRuntime` method.</span></span>

```csharp
class EchoServiceHost : ServiceHost
{
    string creditCardFile;

    public EchoServiceHost(parameters Uri[] addresses)
        : base(typeof(EchoService), addresses)
    {
        creditCardFile = ConfigurationManager.AppSettings["creditCardFile"];
        if (string.IsNullOrEmpty(creditCardFile))
        {
            throw new ConfigurationErrorsException("creditCardFile not specified in service config");
        }

        creditCardFile = String.Format("{0}\\{1}", System.Web.Hosting.HostingEnvironment.ApplicationPhysicalPath, creditCardFile);
    }

    override protected void InitializeRuntime()
    {
        // Create a credit card service credentials and add it to the behaviors.
        CreditCardServiceCredentials serviceCredentials = new CreditCardServiceCredentials(this.creditCardFile);
        serviceCredentials.ServiceCertificate.SetCertificate("CN=localhost", StoreLocation.LocalMachine, StoreName.My);
        this.Description.Behaviors.Remove((typeof(ServiceCredentials)));
        this.Description.Behaviors.Add(serviceCredentials);

        // Register a credit card binding for the endpoint.
        Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
        this.AddServiceEndpoint(typeof(IEchoService), creditCardBinding, string.Empty);

        base.InitializeRuntime();
    }
}
```

 <span data-ttu-id="37084-123">Le point de terminaison du client est configuré de la même manière que le point de terminaison du service.</span><span class="sxs-lookup"><span data-stu-id="37084-123">The client endpoint is configured in a similar manner as the service endpoint.</span></span> <span data-ttu-id="37084-124">Le client utilise une classe `BindingHelper` identique pour créer sa liaison.</span><span class="sxs-lookup"><span data-stu-id="37084-124">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="37084-125">La suite de la configuration s'effectue dans la classe `Client`.</span><span class="sxs-lookup"><span data-stu-id="37084-125">The rest of the setup is located in the `Client` class.</span></span> <span data-ttu-id="37084-126">Le client définit également les informations qui figureront dans `CreditCardToken` ainsi que les informations relatives au certificat X.509 du service dans le code d’installation en ajoutant une instance `CreditCardClientCredentials` à l’aide des données appropriées à la collection des comportements du point de terminaison du client.</span><span class="sxs-lookup"><span data-stu-id="37084-126">The client also sets information to be contained in the `CreditCardToken` and information about the service X.509 certificate in the setup code by adding a `CreditCardClientCredentials` instance with the proper data to the client endpoint behaviors collection.</span></span> <span data-ttu-id="37084-127">Dans cet exemple, le nom du sujet du certificat X.509 utilisé correspond à `CN=localhost` pour le certificat de service.</span><span class="sxs-lookup"><span data-stu-id="37084-127">The sample uses X.509 certificate with subject name set to `CN=localhost` as the service certificate.</span></span>

```csharp
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
var serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");

// Create a client with given client endpoint configuration.
channelFactory = new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);

// Configure the credit card credentials on the channel factory.
var credentials =
      new CreditCardClientCredentials(
      new CreditCardInfo(creditCardNumber, issuer, expirationTime));
// Configure the service certificate on the credentials.
credentials.ServiceCertificate.SetDefaultCertificate(
      "CN=localhost", StoreLocation.LocalMachine, StoreName.My);

// Replace ClientCredentials with CreditCardClientCredentials.
channelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
channelFactory.Endpoint.Behaviors.Add(credentials);

client = channelFactory.CreateChannel();

Console.WriteLine($"Echo service returned: {client.Echo()}");

((IChannel)client).Close();
channelFactory.Close();
```

## <a name="custom-security-token-implementation"></a><span data-ttu-id="37084-128">Implémentation du jeton de sécurité personnalisé</span><span class="sxs-lookup"><span data-stu-id="37084-128">Custom Security Token Implementation</span></span>

 <span data-ttu-id="37084-129">Pour activer un jeton de sécurité personnalisé dans WCF, créez une représentation d’objet du jeton de sécurité personnalisé.</span><span class="sxs-lookup"><span data-stu-id="37084-129">To enable a custom security token in WCF, create an object representation of the custom security token.</span></span> <span data-ttu-id="37084-130">Dans l'exemple, cette représentation figure dans la classe `CreditCardToken`.</span><span class="sxs-lookup"><span data-stu-id="37084-130">The sample has this representation in the `CreditCardToken` class.</span></span> <span data-ttu-id="37084-131">La représentation d'objet est chargée de conserver toutes les informations de jeton de sécurité pertinentes et de fournir la liste des clés de sécurité contenues dans le jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="37084-131">The object representation is responsible for holding all relevant security token information and to provide a list of security keys contained in the security token.</span></span> <span data-ttu-id="37084-132">Dans ce cas de figure, le jeton de sécurité de carte de crédit ne contient pas de clé de sécurité.</span><span class="sxs-lookup"><span data-stu-id="37084-132">In this case, the credit card security token does not contain any security key.</span></span>

 <span data-ttu-id="37084-133">La section suivante décrit ce qui doit être fait pour permettre à un jeton personnalisé d’être transmis sur le réseau et consommé par un point de terminaison WCF.</span><span class="sxs-lookup"><span data-stu-id="37084-133">The next section describes what must be done to enable a custom token to be transmitted over the wire and consumed by a WCF endpoint.</span></span>

```csharp
class CreditCardToken : SecurityToken
{
    CreditCardInfo cardInfo;
    DateTime effectiveTime = DateTime.UtcNow;
    string id;
    ReadOnlyCollection<SecurityKey> securityKeys;

    public CreditCardToken(CreditCardInfo cardInfo) : this(cardInfo, Guid.NewGuid().ToString()) { }

    public CreditCardToken(CreditCardInfo cardInfo, string id)
    {
        if (cardInfo == null)
            throw new ArgumentNullException(nameof(cardInfo));

        if (id == null)
            throw new ArgumentNullException(nameof(id));

        this.cardInfo = cardInfo;
        this.id = id;

        // The credit card token is not capable of any cryptography.
        this.securityKeys = new ReadOnlyCollection<SecurityKey>(new List<SecurityKey>());
    }

    public CreditCardInfo CardInfo { get { return this.cardInfo; } }

    public override ReadOnlyCollection<SecurityKey> SecurityKeys { get { return this.securityKeys; } }

    public override DateTime ValidFrom { get { return this.effectiveTime; } }
    public override DateTime ValidTo { get { return this.cardInfo.ExpirationDate; } }
    public override string Id { get { return this.id; } }
}
```

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a><span data-ttu-id="37084-134">Obtention du jeton de carte de crédit personnalisé au niveau du message</span><span class="sxs-lookup"><span data-stu-id="37084-134">Getting the Custom Credit Card Token to and from the Message</span></span>

 <span data-ttu-id="37084-135">Dans WCF, les sérialiseurs de jeton de sécurité sont responsables de la création d’une représentation d’objet de jetons de sécurité à partir du code XML du message et de la création d’un formulaire XML des jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="37084-135">Security token serializers in WCF are responsible for creating an object representation of security tokens from the XML in the message and creating a XML form of the security tokens.</span></span> <span data-ttu-id="37084-136">D'autres tâches telles que la lecture et l'écriture des identificateurs de clé renvoyant aux jetons de sécurité leur incombent également, mais dans cet exemple, seule la fonctionnalité concernant les jetons de sécurité est utilisée.</span><span class="sxs-lookup"><span data-stu-id="37084-136">They are also responsible for other functionality such as reading and writing key identifiers pointing to security tokens, but this example uses only security token-related functionality.</span></span> <span data-ttu-id="37084-137">Pour activer un jeton personnalisé, vous devez implémenter votre propre sérialiseur de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="37084-137">To enable a custom token you must implement your own security token serializer.</span></span> <span data-ttu-id="37084-138">Cette exemple utilise la classe `CreditCardSecurityTokenSerializer` à cette fin.</span><span class="sxs-lookup"><span data-stu-id="37084-138">This sample uses the `CreditCardSecurityTokenSerializer` class for this purpose.</span></span>

 <span data-ttu-id="37084-139">Côté service, le sérialiseur personnalisé lit le formulaire XML du jeton personnalisé et crée sa représentation d'objet à partir de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="37084-139">On the service, the custom serializer reads the XML form of the custom token and creates the custom token object representation from it.</span></span>

 <span data-ttu-id="37084-140">Côté client, la classe `CreditCardSecurityTokenSerializer` inscrit les informations contenues dans la représentation d'objet du jeton de sécurité dans l'enregistreur XML.</span><span class="sxs-lookup"><span data-stu-id="37084-140">On the client, the `CreditCardSecurityTokenSerializer` class writes the information contained in the security token object representation into the XML writer.</span></span>

```csharp
public class CreditCardSecurityTokenSerializer : WSSecurityTokenSerializer
{
    public CreditCardSecurityTokenSerializer(SecurityTokenVersion version) : base() { }

    protected override bool CanReadTokenCore(XmlReader reader)
    {
        XmlDictionaryReader localReader = XmlDictionaryReader.CreateDictionaryReader(reader);

        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
            return true;

        return base.CanReadTokenCore(reader);
    }

    protected override SecurityToken ReadTokenCore(XmlReader reader, SecurityTokenResolver tokenResolver)
    {
        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
        {
            string id = reader.GetAttribute(Constants.Id, Constants.WsUtilityNamespace);

            reader.ReadStartElement();

            // Read the credit card number.
            string creditCardNumber = reader.ReadElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace);

            // Read the expiration date.
            string expirationTimeString = reader.ReadElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace);
            DateTime expirationTime = XmlConvert.ToDateTime(expirationTimeString, XmlDateTimeSerializationMode.Utc);

            // Read the issuer of the credit card.
            string creditCardIssuer = reader.ReadElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace);
            reader.ReadEndElement();

            var cardInfo = new CreditCardInfo(creditCardNumber, creditCardIssuer, expirationTime);

            return new CreditCardToken(cardInfo, id);
        }
        else
        {
            return WSSecurityTokenSerializer.DefaultInstance.ReadToken(reader, tokenResolver);
        }
    }

    protected override bool CanWriteTokenCore(SecurityToken token)
    {
        if (token is CreditCardToken)
            return true;
        return base.CanWriteTokenCore(token);
    }

    protected override void WriteTokenCore(XmlWriter writer, SecurityToken token)
    {
        if (writer == null)
            throw new ArgumentNullException(nameof(writer));
        if (token == null)
            throw new ArgumentNullException(nameof(token));

        CreditCardToken c = token as CreditCardToken;
        if (c != null)
        {
            writer.WriteStartElement(Constants.CreditCardTokenPrefix, Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace);
            writer.WriteAttributeString(Constants.WsUtilityPrefix, Constants.Id, Constants.WsUtilityNamespace, token.Id);
            writer.WriteElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardNumber);
            writer.WriteElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace, XmlConvert.ToString(c.CardInfo.ExpirationDate, XmlDateTimeSerializationMode.Utc));
            writer.WriteElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardIssuer);
            writer.WriteEndElement();
            writer.Flush();
        }
        else
        {
            base.WriteTokenCore(writer, token);
        }
    }
}
```

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a><span data-ttu-id="37084-141">Modalités de création des classes de fournisseur et d'authentificateur de jetons</span><span class="sxs-lookup"><span data-stu-id="37084-141">How Token Provider and Token Authenticator Classes are Created</span></span>

 <span data-ttu-id="37084-142">Les informations d'identification du client et du service sont chargées de fournir l'instance de gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="37084-142">Client and service credentials are responsible for providing the security token manager instance.</span></span> <span data-ttu-id="37084-143">Cette instance est utilisée pour obtenir les fournisseurs, authentificateurs et sérialiseurs de jetons.</span><span class="sxs-lookup"><span data-stu-id="37084-143">The security token manager instance is used to get token providers, token authenticators and token serializers.</span></span>

 <span data-ttu-id="37084-144">Le fournisseur de jetons crée une représentation d'objet du jeton en fonction des données contenues dans les informations d'identification du client ou du service.</span><span class="sxs-lookup"><span data-stu-id="37084-144">The token provider creates an object representation of the token based on the information contained in the client or service credentials.</span></span> <span data-ttu-id="37084-145">Cette représentation est ensuite inscrite dans le message à l'aide du sérialiseur de jetons (thème abordé à la section précédente).</span><span class="sxs-lookup"><span data-stu-id="37084-145">The token object representation is then written to the message using the token serializer (discussed in the previous section).</span></span>

 <span data-ttu-id="37084-146">L'authentificateur de jetons valide les jetons qui arrivent dans les messages.</span><span class="sxs-lookup"><span data-stu-id="37084-146">The token authenticator validates tokens that arrive in the message.</span></span> <span data-ttu-id="37084-147">La représentation entrante d'objet du jeton est créée par le sérialiseur de jetons.</span><span class="sxs-lookup"><span data-stu-id="37084-147">The incoming token object representation is created by the token serializer.</span></span> <span data-ttu-id="37084-148">Cette représentation est ensuite transmise à l’authentificateur de jetons pour validation.</span><span class="sxs-lookup"><span data-stu-id="37084-148">This object representation is then passed to the token authenticator for validation.</span></span> <span data-ttu-id="37084-149">Le jeton validé, l’authentificateur de jetons retourne une collection d’objets `IAuthorizationPolicy` qui représentent les informations contenues dans ce jeton.</span><span class="sxs-lookup"><span data-stu-id="37084-149">After the token is successfully validated, the token authenticator returns a collection of `IAuthorizationPolicy` objects that represent the information contained in the token.</span></span> <span data-ttu-id="37084-150">Ces informations sont utilisées ultérieurement pendant le traitement des messages pour prendre les décisions d'autorisation et définir des revendications pour les applications concernées.</span><span class="sxs-lookup"><span data-stu-id="37084-150">This information is used later during the message processing to perform authorization decisions and to provide claims for the application.</span></span> <span data-ttu-id="37084-151">Dans cet exemple, l'authentificateur du jeton de carte de crédit utilise `CreditCardTokenAuthorizationPolicy` à cette fin.</span><span class="sxs-lookup"><span data-stu-id="37084-151">In this example, the credit card token authenticator uses `CreditCardTokenAuthorizationPolicy` for this purpose.</span></span>

 <span data-ttu-id="37084-152">Le sérialiseur de jetons est chargé d'obtenir la représentation d'objet du jeton depuis le câble et de la générer à ce même niveau.</span><span class="sxs-lookup"><span data-stu-id="37084-152">The token serializer is responsible for getting the object representation of the token to and from the wire.</span></span> <span data-ttu-id="37084-153">Ce thème est abordé à la section précédente.</span><span class="sxs-lookup"><span data-stu-id="37084-153">This is discussed in the previous section.</span></span>

 <span data-ttu-id="37084-154">Dans cet exemple, nous utilisons uniquement un fournisseur de jetons sur le client et un authentificateur de jetons sur le service, le jeton de carte de crédit étant transmis uniquement dans le sens client-service.</span><span class="sxs-lookup"><span data-stu-id="37084-154">In this sample, we use a token provider only on the client and a token authenticator only on the service, because we want to transmit a credit card token only in the client-to-service direction.</span></span>

 <span data-ttu-id="37084-155">Côté client, cette fonctionnalité figure dans les classes `CreditCardClientCredentials`, `CreditCardClientCredentialsSecurityTokenManager` et `CreditCardTokenProvider`.</span><span class="sxs-lookup"><span data-stu-id="37084-155">The functionality on the client is located in the `CreditCardClientCredentials`, `CreditCardClientCredentialsSecurityTokenManager` and `CreditCardTokenProvider` classes.</span></span>

 <span data-ttu-id="37084-156">Côté service, cette fonctionnalité figure dans les classes `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` et `CreditCardTokenAuthorizationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="37084-156">On the service, the functionality resides in the `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` and `CreditCardTokenAuthorizationPolicy` classes.</span></span>

```csharp
    public class CreditCardClientCredentials : ClientCredentials
    {
        CreditCardInfo creditCardInfo;

        public CreditCardClientCredentials(CreditCardInfo creditCardInfo)
            : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException(nameof(creditCardInfo));

            this.creditCardInfo = creditCardInfo;
        }

        public CreditCardInfo CreditCardInfo
        {
            get { return this.creditCardInfo; }
        }

        protected override ClientCredentials CloneCore()
        {
            return new CreditCardClientCredentials(this.creditCardInfo);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardClientCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardClientCredentialsSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        CreditCardClientCredentials creditCardClientCredentials;

        public CreditCardClientCredentialsSecurityTokenManager(CreditCardClientCredentials creditCardClientCredentials)
            : base (creditCardClientCredentials)
        {
            this.creditCardClientCredentials = creditCardClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // Handle this token for Custom.
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
                return new CreditCardTokenProvider(this.creditCardClientCredentials.CreditCardInfo);
            // Return server cert.
            else if (tokenRequirement is InitiatorServiceModelSecurityTokenRequirement)
            {
                if (tokenRequirement.TokenType == SecurityTokenTypes.X509Certificate)
                {
                    return new X509SecurityTokenProvider(creditCardClientCredentials.ServiceCertificate.DefaultCertificate);
                }
            }

            return base.CreateSecurityTokenProvider(tokenRequirement);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {

            return new CreditCardSecurityTokenSerializer(version);
        }

    }

    class CreditCardTokenProvider : SecurityTokenProvider
    {
        CreditCardInfo creditCardInfo;

        public CreditCardTokenProvider(CreditCardInfo creditCardInfo) : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException(nameof(creditCardInfo));

            this.creditCardInfo = creditCardInfo;
        }

        protected override SecurityToken GetTokenCore(TimeSpan timeout)
        {
            SecurityToken result = new CreditCardToken(this.creditCardInfo);
            return result;
        }
    }

    public class CreditCardServiceCredentials : ServiceCredentials
    {
        string creditCardFile;

        public CreditCardServiceCredentials(string creditCardFile)
            : base()
        {
            if (creditCardFile == null)
                throw new ArgumentNullException(nameof(creditCardFile));

            this.creditCardFile = creditCardFile;
        }

        public string CreditCardDataFile
        {
            get { return this.creditCardFile; }
        }

        protected override ServiceCredentials CloneCore()
        {
            return new CreditCardServiceCredentials(this.creditCardFile);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardServiceCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardServiceCredentialsSecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        CreditCardServiceCredentials creditCardServiceCredentials;

        public CreditCardServiceCredentialsSecurityTokenManager(CreditCardServiceCredentials creditCardServiceCredentials)
            : base(creditCardServiceCredentials)
        {
            this.creditCardServiceCredentials = creditCardServiceCredentials;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
            {
                outOfBandTokenResolver = null;
                return new CreditCardTokenAuthenticator(creditCardServiceCredentials.CreditCardDataFile);
            }

            return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {
            return new CreditCardSecurityTokenSerializer(version);
        }
    }

    class CreditCardTokenAuthenticator : SecurityTokenAuthenticator
    {
        string creditCardsFile;
        public CreditCardTokenAuthenticator(string creditCardsFile)
        {
            this.creditCardsFile = creditCardsFile;
        }

        protected override bool CanValidateTokenCore(SecurityToken token)
        {
            return (token is CreditCardToken);
        }

        protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateTokenCore(SecurityToken token)
        {
            CreditCardToken creditCardToken = token as CreditCardToken;

            if (creditCardToken.CardInfo.ExpirationDate < DateTime.UtcNow)
                throw new SecurityTokenValidationException("The credit card has expired.");
            if (!IsCardNumberAndExpirationValid(creditCardToken.CardInfo))
                throw new SecurityTokenValidationException("Unknown or invalid credit card.");

            // the credit card token has only 1 claim - the card number. The issuer for the claim is the
            // credit card issuer

            var cardIssuerClaimSet = new DefaultClaimSet(new Claim(ClaimTypes.Name, creditCardToken.CardInfo.CardIssuer, Rights.PossessProperty));
            var cardClaimSet = new DefaultClaimSet(cardIssuerClaimSet, new Claim(Constants.CreditCardNumberClaim, creditCardToken.CardInfo.CardNumber, Rights.PossessProperty));
            var policies = new List<IAuthorizationPolicy>(1);
            policies.Add(new CreditCardTokenAuthorizationPolicy(cardClaimSet));
            return policies.AsReadOnly();
        }

        /// <summary>
        /// Helper method to check if a given credit card entry is present in the User DB
        /// </summary>
        private bool IsCardNumberAndExpirationValid(CreditCardInfo cardInfo)
        {
            try
            {
                using (var myStreamReader = new StreamReader(this.creditCardsFile))
                {
                    string line = "";
                    while ((line = myStreamReader.ReadLine()) != null)
                    {
                        string[] splitEntry = line.Split('#');
                        if (splitEntry[0] == cardInfo.CardNumber)
                        {
                            string expirationDateString = splitEntry[1].Trim();
                            DateTime expirationDateOnFile = DateTime.Parse(expirationDateString, System.Globalization.DateTimeFormatInfo.InvariantInfo, System.Globalization.DateTimeStyles.AdjustToUniversal);
                            if (cardInfo.ExpirationDate == expirationDateOnFile)
                            {
                                string issuer = splitEntry[2];
                                return issuer.Equals(cardInfo.CardIssuer, StringComparison.InvariantCultureIgnoreCase);
                            }
                            else
                            {
                                return false;
                            }
                        }
                    }
                    return false;
                }
            }
            catch (Exception e)
            {
                throw new Exception("BookStoreService: Error while retrieving credit card information from User DB " + e.ToString());
            }
        }
    }

    public class CreditCardTokenAuthorizationPolicy : IAuthorizationPolicy
    {
        string id;
        ClaimSet issuer;
        IEnumerable<ClaimSet> issuedClaimSets;

        public CreditCardTokenAuthorizationPolicy(ClaimSet issuedClaims)
        {
            if (issuedClaims == null)
                throw new ArgumentNullException(nameof(issuedClaims));
            this.issuer = issuedClaims.Issuer;
            this.issuedClaimSets = new ClaimSet[] { issuedClaims };
            this.id = Guid.NewGuid().ToString();
        }

        public ClaimSet Issuer { get { return this.issuer; } }

        public string Id { get { return this.id; } }

        public bool Evaluate(EvaluationContext context, ref object state)
        {
            foreach (ClaimSet issuance in this.issuedClaimSets)
            {
                context.AddClaimSet(this, issuance);
            }

            return true;
        }
    }
```

## <a name="displaying-the-callers-information"></a><span data-ttu-id="37084-157">Affichage des informations relatives aux appelants</span><span class="sxs-lookup"><span data-stu-id="37084-157">Displaying the Callers' Information</span></span>

 <span data-ttu-id="37084-158">Pour afficher les informations de l'appelant, utilisez `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="37084-158">To display the caller's information, use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following sample code.</span></span> <span data-ttu-id="37084-159">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contient les revendications d'autorisation associées à l'appelant actuel.</span><span class="sxs-lookup"><span data-stu-id="37084-159">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="37084-160">Ces revendications sont fournies par la classe `CreditCardToken`, depuis sa collection `AuthorizationPolicies`.</span><span class="sxs-lookup"><span data-stu-id="37084-160">The claims are supplied by the `CreditCardToken` class in its `AuthorizationPolicies` collection.</span></span>

```csharp
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)
{
    claimValue = null;
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
        return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    enumerator.MoveNext();
    claimValue = (enumerator.Current.Resource == null) ? null :
        enumerator.Current.Resource.ToString();
    return true;
}

string GetCallerCreditCardNumber()
{
     foreach (ClaimSet claimSet in
         ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)
     {
         string creditCardNumber = null;
         if (TryGetStringClaimValue(claimSet,
             Constants.CreditCardNumberClaim, out creditCardNumber))
             {
                 string issuer;
                 if (!TryGetStringClaimValue(claimSet.Issuer,
                        ClaimTypes.Name, out issuer))
                 {
                     issuer = "Unknown";
                 }
                 return $"Credit card '{creditCardNumber}' issued by '{issuer}'";
        }
    }
    return "Credit card is not known";
}
```

 <span data-ttu-id="37084-161">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="37084-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="37084-162">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="37084-162">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="37084-163">Fichier de commandes d'installation</span><span class="sxs-lookup"><span data-stu-id="37084-163">Setup Batch File</span></span>

 <span data-ttu-id="37084-164">Le fichier de commandes Setup.bat inclus dans cet exemple permet de configurer le serveur avec les certificats nécessaires à l'exécution des applications hébergées dans IIS qui nécessitent une sécurité basée sur les certificats de serveur.</span><span class="sxs-lookup"><span data-stu-id="37084-164">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run the IIS-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="37084-165">Ce fichier de commandes doit être modifié pour fonctionner sur plusieurs ordinateurs ou sans hébergement.</span><span class="sxs-lookup"><span data-stu-id="37084-165">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="37084-166">Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée.</span><span class="sxs-lookup"><span data-stu-id="37084-166">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="37084-167">Création du certificat de serveur :</span><span class="sxs-lookup"><span data-stu-id="37084-167">Creating the server certificate:</span></span>

     <span data-ttu-id="37084-168">Les lignes suivantes du fichier de commandes `Setup.bat` créent le certificat de serveur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="37084-168">The following lines from the `Setup.bat` batch file create the server certificate to be used.</span></span> <span data-ttu-id="37084-169">La variable `%SERVER_NAME%` spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="37084-169">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="37084-170">Modifiez cette variable pour spécifier votre propre nom de serveur.</span><span class="sxs-lookup"><span data-stu-id="37084-170">Change this variable to specify your own server name.</span></span> <span data-ttu-id="37084-171">La valeur par défaut dans ce fichier de commandes est localhost.</span><span class="sxs-lookup"><span data-stu-id="37084-171">The default in this batch file is localhost.</span></span> <span data-ttu-id="37084-172">Si vous modifiez la variable `%SERVER_NAME%`, vous devez parcourir tous les fichiers Client.cs et Service.cs afin de remplacer toutes les occurrences de localhost par le nom du serveur utilisé dans le script Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="37084-172">If you change the `%SERVER_NAME%` variable, you must go through the Client.cs and Service.cs files and replace all instances of localhost with the server name that you use in the Setup.bat script.</span></span>

     <span data-ttu-id="37084-173">Le certificat est stocké dans le magasin My (personnel) sous l'emplacement de magasin `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="37084-173">The certificate is stored in My (Personal) store under the `LocalMachine` store location.</span></span> <span data-ttu-id="37084-174">Le certificat est stocké dans le magasin LocalMachine pour les services hébergés par IIS.</span><span class="sxs-lookup"><span data-stu-id="37084-174">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="37084-175">Pour les services auto-hébergés, vous devez modifier le fichier de commandes en remplaçant la chaîne LocalMachine par CurrentUser afin de stocker le certificat de client dans l'emplacement de magasin CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="37084-175">For self-hosted services, you should modify the batch file to store the client certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="37084-176">Installation du certificat de serveur dans le magasin de certificats approuvés du client :</span><span class="sxs-lookup"><span data-stu-id="37084-176">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="37084-177">Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="37084-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="37084-178">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="37084-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="37084-179">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats client avec le certificat de serveur n'est pas requise.</span><span class="sxs-lookup"><span data-stu-id="37084-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```bat
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="37084-180">Pour activer l'accès à la clé privée du certificat à partir du service hébergé par IIS, le compte d'utilisateur sous lequel le processus hébergé par IIS s'exécute doit disposer des autorisations permettant d'y accéder.</span><span class="sxs-lookup"><span data-stu-id="37084-180">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="37084-181">Cette opération est effectuée par les dernières étapes du script Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="37084-181">This is accomplished by last steps in the Setup.bat script.</span></span>

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
> <span data-ttu-id="37084-182">Le fichier de commandes Setup.bat est conçu pour être exécuté à partir d’une invite de commandes de Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="37084-182">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="37084-183">La variable d’environnement PATH définie dans l’invite de commandes de Visual Studio 2012 pointe vers le répertoire qui contient les exécutables requis par le script Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="37084-183">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="37084-184">Pour configurer et générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="37084-184">To set up and build the sample</span></span>

1. <span data-ttu-id="37084-185">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37084-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="37084-186">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37084-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="37084-187">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="37084-187">To run the sample on the same computer</span></span>

1. <span data-ttu-id="37084-188">Ouvrez une fenêtre d’invite de commandes Visual Studio 2012 avec des privilèges d’administrateur et exécutez Setup.bat à partir du dossier d’installation de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="37084-188">Open a Visual Studio 2012 Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="37084-189">Tous les certificats requis pour l'exécution de l'exemple sont ainsi installés. Assurez-vous que le chemin d'accès inclut le dossier dans lequel Makecert.exe se trouve.</span><span class="sxs-lookup"><span data-stu-id="37084-189">This installs all the certificates required for running the sample.Make sure that the path includes the folder where Makecert.exe is located.</span></span>

> [!NOTE]
> <span data-ttu-id="37084-190">Assurez-vous de supprimer les certificats en exécutant Cleanup.bat une fois l'exemple terminé.</span><span class="sxs-lookup"><span data-stu-id="37084-190">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="37084-191">D'autres exemples de sécurité utilisent ces mêmes certificats.</span><span class="sxs-lookup"><span data-stu-id="37084-191">Other security samples use the same certificates.</span></span>  
  
1. <span data-ttu-id="37084-192">Lancez Client.exe à partir du répertoire \client\bin.</span><span class="sxs-lookup"><span data-stu-id="37084-192">Launch Client.exe from client\bin directory.</span></span> <span data-ttu-id="37084-193">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="37084-193">Client activity is displayed on the client console application.</span></span>  
  
2. <span data-ttu-id="37084-194">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="37084-194">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computer"></a><span data-ttu-id="37084-195">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="37084-195">To run the sample across computer</span></span>  
  
1. <span data-ttu-id="37084-196">Créez un répertoire sur l'ordinateur de service pour les fichiers binaires du service.</span><span class="sxs-lookup"><span data-stu-id="37084-196">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="37084-197">Copiez les fichiers programme du service dans le répertoire de service sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="37084-197">Copy the service program files into the service directory on the service computer.</span></span> <span data-ttu-id="37084-198">N'oubliez pas de copier le fichier CreditCardFile.txt, sinon l'authentificateur de carte de crédit ne pourra pas valider les informations de carte de crédit envoyées depuis le client.</span><span class="sxs-lookup"><span data-stu-id="37084-198">Do not forget to copy CreditCardFile.txt; otherwise the credit card authenticator cannot validate credit card information sent from the client.</span></span> <span data-ttu-id="37084-199">Copiez également les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="37084-199">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="37084-200">Le nom de sujet de votre certificat de serveur doit contenir le nom de domaine complet de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="37084-200">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="37084-201">Pour en créer un à l'aide de Setup.bat, il vous suffit de remplacer la variable `%SERVER_NAME%` par le nom complet de l'ordinateur où le service est hébergé.</span><span class="sxs-lookup"><span data-stu-id="37084-201">You can create one using the Setup.bat if you change the `%SERVER_NAME%` variable to fully-qualified name of the computer where the service is hosted.</span></span> <span data-ttu-id="37084-202">Notez que le fichier Setup.bat doit être exécuté dans un Invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="37084-202">Note that the Setup.bat file must be run in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="37084-203">Copiez le certificat du serveur dans le magasin CurrentUser-TrustedPeople du client.</span><span class="sxs-lookup"><span data-stu-id="37084-203">Copy the server certificate into the CurrentUser-TrustedPeople store on the client.</span></span> <span data-ttu-id="37084-204">Cette tâche est requise uniquement si le certificat du serveur n'est pas publié par un émetteur approuvé.</span><span class="sxs-lookup"><span data-stu-id="37084-204">You must do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="37084-205">Dans le fichier EchoServiceHost.cs, remplacez la valeur localhost du nom du sujet du certificat par le nom complet de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="37084-205">In the EchoServiceHost.cs file, change the value of the certificate subject name to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="37084-206">Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="37084-206">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
7. <span data-ttu-id="37084-207">Dans le fichier Client.cs, modifiez l'adresse du point de terminaison en fonction de la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="37084-207">In the Client.cs file, change the address value of the endpoint to match the new address of your service.</span></span>  
  
8. <span data-ttu-id="37084-208">Dans le fichier Client.cs, modifiez le nom du sujet du certificat X.509 de service en remplaçant la valeur localhost par le nom complet de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="37084-208">In the Client.cs file change the subject name of the service X.509 certificate to match the fully-qualified computer name of the remote host instead of localhost.</span></span>  
  
9. <span data-ttu-id="37084-209">Sur l'ordinateur client, lancez Client.exe à partir d'une fenêtre d'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="37084-209">On the client computer, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="37084-210">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="37084-210">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="37084-211">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="37084-211">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="37084-212">Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.</span><span class="sxs-lookup"><span data-stu-id="37084-212">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>
