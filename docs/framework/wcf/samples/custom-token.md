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
# <a name="custom-token"></a>Custom Token

Cet exemple montre comment ajouter une implémentation de jeton personnalisée dans une application Windows Communication Foundation (WCF). Cet exemple utilise un `CreditCardToken` pour transmettre de manière sécurisée les informations de carte de crédit du client au service. Le jeton est transmis dans l’en-tête de message WS-Security. Il est signé et chiffré à l’aide de l’élément de liaison de sécurité symétrique en même temps que le corps du message et que les autres en-têtes de message. Cette particularité est utile lorsque les jetons intégrés ne sont pas suffisants. Cet exemple illustre comment fournir un jeton de sécurité personnalisé à un service au lieu d'utiliser l'un des jetons intégrés. Le service implémente un contrat qui définit un modèle de communication demande-réponse.

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

 En résumé, cet exemple montre :

- Comment un client peut transmettre un jeton de sécurité personnalisé à un service.

- Comment le service peut consommer et valider un jeton de sécurité personnalisé.

- Comment le code de service WCF peut obtenir les informations sur les jetons de sécurité reçus, y compris le jeton de sécurité personnalisé.

- Comment le certificat X.509 du serveur permet de protéger la clé symétrique utilisée pour la signature et le chiffrement des messages.

## <a name="client-authentication-using-a-custom-security-token"></a>Authentification du client à l'aide d'un jeton de sécurité personnalisé

 Le service expose un point de terminaison unique qui est créé par programme à l'aide des classes `BindingHelper` et `EchoServiceHost`. Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat. La liaison est configurée avec une liaison personnalisé à l'aide de `SymmetricSecurityBindingElement` et `HttpTransportBindingElement`. Dans cet exemple, l'élément `SymmetricSecurityBindingElement` est configuré pour utiliser un certificat X.509 de service afin de protéger la clé symétrique pendant la transmission et de transmettre le `CreditCardToken` personnalisé dans un en-tête de message WS-Security sous forme de jeton de sécurité signé et chiffré. Le comportement spécifie les informations d'identification du service qui doivent être utilisées pour l'authentification du client ainsi que les informations sur le certificat X.509 du service.

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

 Pour consommer le jeton de carte de crédit figurant dans le message, l'exemple utilise les informations d'identification personnalisées du service. La classe d’informations d’identification du service se trouve dans la classe `CreditCardServiceCredentials`. Elle est ajoutée aux collections de comportements de l’hôte de service dans la méthode `EchoServiceHost.InitializeRuntime`.

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

 Le point de terminaison du client est configuré de la même manière que le point de terminaison du service. Le client utilise une classe `BindingHelper` identique pour créer sa liaison. La suite de la configuration s'effectue dans la classe `Client`. Le client définit également les informations qui figureront dans `CreditCardToken` ainsi que les informations relatives au certificat X.509 du service dans le code d’installation en ajoutant une instance `CreditCardClientCredentials` à l’aide des données appropriées à la collection des comportements du point de terminaison du client. Dans cet exemple, le nom du sujet du certificat X.509 utilisé correspond à `CN=localhost` pour le certificat de service.

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

## <a name="custom-security-token-implementation"></a>Implémentation du jeton de sécurité personnalisé

 Pour activer un jeton de sécurité personnalisé dans WCF, créez une représentation d’objet du jeton de sécurité personnalisé. Dans l'exemple, cette représentation figure dans la classe `CreditCardToken`. La représentation d'objet est chargée de conserver toutes les informations de jeton de sécurité pertinentes et de fournir la liste des clés de sécurité contenues dans le jeton de sécurité. Dans ce cas de figure, le jeton de sécurité de carte de crédit ne contient pas de clé de sécurité.

 La section suivante décrit ce qui doit être fait pour permettre à un jeton personnalisé d’être transmis sur le réseau et consommé par un point de terminaison WCF.

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

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a>Obtention du jeton de carte de crédit personnalisé au niveau du message

 Dans WCF, les sérialiseurs de jeton de sécurité sont responsables de la création d’une représentation d’objet de jetons de sécurité à partir du code XML du message et de la création d’un formulaire XML des jetons de sécurité. D'autres tâches telles que la lecture et l'écriture des identificateurs de clé renvoyant aux jetons de sécurité leur incombent également, mais dans cet exemple, seule la fonctionnalité concernant les jetons de sécurité est utilisée. Pour activer un jeton personnalisé, vous devez implémenter votre propre sérialiseur de jeton de sécurité. Cette exemple utilise la classe `CreditCardSecurityTokenSerializer` à cette fin.

 Côté service, le sérialiseur personnalisé lit le formulaire XML du jeton personnalisé et crée sa représentation d'objet à partir de ce dernier.

 Côté client, la classe `CreditCardSecurityTokenSerializer` inscrit les informations contenues dans la représentation d'objet du jeton de sécurité dans l'enregistreur XML.

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

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a>Modalités de création des classes de fournisseur et d'authentificateur de jetons

 Les informations d'identification du client et du service sont chargées de fournir l'instance de gestionnaire de jetons de sécurité. Cette instance est utilisée pour obtenir les fournisseurs, authentificateurs et sérialiseurs de jetons.

 Le fournisseur de jetons crée une représentation d'objet du jeton en fonction des données contenues dans les informations d'identification du client ou du service. Cette représentation est ensuite inscrite dans le message à l'aide du sérialiseur de jetons (thème abordé à la section précédente).

 L'authentificateur de jetons valide les jetons qui arrivent dans les messages. La représentation entrante d'objet du jeton est créée par le sérialiseur de jetons. Cette représentation est ensuite transmise à l’authentificateur de jetons pour validation. Le jeton validé, l’authentificateur de jetons retourne une collection d’objets `IAuthorizationPolicy` qui représentent les informations contenues dans ce jeton. Ces informations sont utilisées ultérieurement pendant le traitement des messages pour prendre les décisions d'autorisation et définir des revendications pour les applications concernées. Dans cet exemple, l'authentificateur du jeton de carte de crédit utilise `CreditCardTokenAuthorizationPolicy` à cette fin.

 Le sérialiseur de jetons est chargé d'obtenir la représentation d'objet du jeton depuis le câble et de la générer à ce même niveau. Ce thème est abordé à la section précédente.

 Dans cet exemple, nous utilisons uniquement un fournisseur de jetons sur le client et un authentificateur de jetons sur le service, le jeton de carte de crédit étant transmis uniquement dans le sens client-service.

 Côté client, cette fonctionnalité figure dans les classes `CreditCardClientCredentials`, `CreditCardClientCredentialsSecurityTokenManager` et `CreditCardTokenProvider`.

 Côté service, cette fonctionnalité figure dans les classes `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` et `CreditCardTokenAuthorizationPolicy`.

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

## <a name="displaying-the-callers-information"></a>Affichage des informations relatives aux appelants

 Pour afficher les informations de l'appelant, utilisez `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`, tel qu'indiqué dans l'exemple de code suivant. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contient les revendications d'autorisation associées à l'appelant actuel. Ces revendications sont fournies par la classe `CreditCardToken`, depuis sa collection `AuthorizationPolicies`.

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

 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.

## <a name="setup-batch-file"></a>Fichier de commandes d'installation

 Le fichier de commandes Setup.bat inclus dans cet exemple permet de configurer le serveur avec les certificats nécessaires à l'exécution des applications hébergées dans IIS qui nécessitent une sécurité basée sur les certificats de serveur. Ce fichier de commandes doit être modifié pour fonctionner sur plusieurs ordinateurs ou sans hébergement.

 Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée.

- Création du certificat de serveur :

     Les lignes suivantes du fichier de commandes `Setup.bat` créent le certificat de serveur à utiliser. La variable `%SERVER_NAME%` spécifie le nom du serveur. Modifiez cette variable pour spécifier votre propre nom de serveur. La valeur par défaut dans ce fichier de commandes est localhost. Si vous modifiez la variable `%SERVER_NAME%`, vous devez parcourir tous les fichiers Client.cs et Service.cs afin de remplacer toutes les occurrences de localhost par le nom du serveur utilisé dans le script Setup.bat.

     Le certificat est stocké dans le magasin My (personnel) sous l'emplacement de magasin `LocalMachine`. Le certificat est stocké dans le magasin LocalMachine pour les services hébergés par IIS. Pour les services auto-hébergés, vous devez modifier le fichier de commandes en remplaçant la chaîne LocalMachine par CurrentUser afin de stocker le certificat de client dans l'emplacement de magasin CurrentUser.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Installation du certificat de serveur dans le magasin de certificats approuvés du client :

     Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client. Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client. Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats client avec le certificat de serveur n'est pas requise.

    ```bat
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Pour activer l'accès à la clé privée du certificat à partir du service hébergé par IIS, le compte d'utilisateur sous lequel le processus hébergé par IIS s'exécute doit disposer des autorisations permettant d'y accéder. Cette opération est effectuée par les dernières étapes du script Setup.bat.

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
> Le fichier de commandes Setup.bat est conçu pour être exécuté à partir d’une invite de commandes de Visual Studio 2012. La variable d’environnement PATH définie dans l’invite de commandes de Visual Studio 2012 pointe vers le répertoire qui contient les exécutables requis par le script Setup.bat.

#### <a name="to-set-up-and-build-the-sample"></a>Pour configurer et générer l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).

#### <a name="to-run-the-sample-on-the-same-computer"></a>Pour exécuter l'exemple sur le même ordinateur

1. Ouvrez une fenêtre d’invite de commandes Visual Studio 2012 avec des privilèges d’administrateur et exécutez Setup.bat à partir du dossier d’installation de l’exemple. Tous les certificats requis pour l'exécution de l'exemple sont ainsi installés. Assurez-vous que le chemin d'accès inclut le dossier dans lequel Makecert.exe se trouve.

> [!NOTE]
> Assurez-vous de supprimer les certificats en exécutant Cleanup.bat une fois l'exemple terminé. D'autres exemples de sécurité utilisent ces mêmes certificats.  
  
1. Lancez Client.exe à partir du répertoire \client\bin. L'activité du client s'affiche sur son application de console.  
  
2. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computer"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1. Créez un répertoire sur l'ordinateur de service pour les fichiers binaires du service.  
  
2. Copiez les fichiers programme du service dans le répertoire de service sur l'ordinateur de service. N'oubliez pas de copier le fichier CreditCardFile.txt, sinon l'authentificateur de carte de crédit ne pourra pas valider les informations de carte de crédit envoyées depuis le client. Copiez également les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.  
  
3. Le nom de sujet de votre certificat de serveur doit contenir le nom de domaine complet de l'ordinateur. Pour en créer un à l'aide de Setup.bat, il vous suffit de remplacer la variable `%SERVER_NAME%` par le nom complet de l'ordinateur où le service est hébergé. Notez que le fichier Setup.bat doit être exécuté dans un Invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.  
  
4. Copiez le certificat du serveur dans le magasin CurrentUser-TrustedPeople du client. Cette tâche est requise uniquement si le certificat du serveur n'est pas publié par un émetteur approuvé.  
  
5. Dans le fichier EchoServiceHost.cs, remplacez la valeur localhost du nom du sujet du certificat par le nom complet de l'ordinateur.  
  
6. Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur client.  
  
7. Dans le fichier Client.cs, modifiez l'adresse du point de terminaison en fonction de la nouvelle adresse de votre service.  
  
8. Dans le fichier Client.cs, modifiez le nom du sujet du certificat X.509 de service en remplaçant la valeur localhost par le nom complet de l'ordinateur.  
  
9. Sur l'ordinateur client, lancez Client.exe à partir d'une fenêtre d'invite de commandes.  
  
10. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
1. Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.
