---
title: WS 2007 Federation HTTP Binding
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: bf61e64733859d96adf42fbacf08266eca1f5b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183185"
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="32c16-102">WS 2007 Federation HTTP Binding</span><span class="sxs-lookup"><span data-stu-id="32c16-102">WS 2007 Federation HTTP Binding</span></span>

<span data-ttu-id="32c16-103">Cet exemple montre l’utilisation de <xref:System.ServiceModel.WS2007FederationHttpBinding>, une liaison standard vous permettant de générer des scénarios fédérés qui prennent en charge la version 1.3 de la spécification WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="32c16-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>

> [!NOTE]
> <span data-ttu-id="32c16-104">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="32c16-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="32c16-105">L’échantillon se compose d’un programme client basé sur console (*Client.exe*), d’un programme de service de jetons de sécurité basé sur console *(Securitytokenservice.exe*), et d’un programme de service basé sur console *(Service.exe*).</span><span class="sxs-lookup"><span data-stu-id="32c16-105">The sample consists of a console-based client program (*Client.exe*), a console-based security token service program (*Securitytokenservice.exe*), and a console-based service program (*Service.exe*).</span></span> <span data-ttu-id="32c16-106">Le service implémente un contrat qui définit un modèle de communication demande/réponse.</span><span class="sxs-lookup"><span data-stu-id="32c16-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="32c16-107">Le contrat est défini par l'interface `ICalculator`, qui expose des opérations mathématiques (`Add`, `Subtract`, `Multiply` et `Divide`).</span><span class="sxs-lookup"><span data-stu-id="32c16-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="32c16-108">Le client obtient un jeton de sécurité du service d’émission de jeton de sécurité (STS, Security Token Service) et adresse des demandes synchrones au service pour une opération mathématique donnée.</span><span class="sxs-lookup"><span data-stu-id="32c16-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="32c16-109">Le service répond ensuite avec le résultat.</span><span class="sxs-lookup"><span data-stu-id="32c16-109">The service then replies with the result.</span></span> <span data-ttu-id="32c16-110">L'activité du client est affichée dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="32c16-110">Client activity is visible in the console window.</span></span>

<span data-ttu-id="32c16-111">L'exemple rend le contrat `ICalculator` disponible à l'aide de l'élément `ws2007FederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="32c16-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="32c16-112">La configuration de cette liaison sur le client est indiquée dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="32c16-112">The configuration of this binding on the client is shown in the following code:</span></span>

```xml
<bindings>
  <ws2007FederationHttpBinding>
    <binding name="ServiceFed" >
      <security mode ="Message">
        <message issuedKeyType ="SymmetricKey"
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >
          <!-- Endpoint address and binding for Security Token Service -->
          <issuer address ="http://localhost:8000/sts/windows"
                  binding ="ws2007HttpBinding" />
        </message>
      </security>
    </binding>
  </ws2007FederationHttpBinding>
</bindings>
```

<span data-ttu-id="32c16-113">Sur le [ \<>de sécurité, ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)la `security` valeur précise quel mode de sécurité doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="32c16-113">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="32c16-114">Dans cet `message` échantillon, la sécurité est [ \<](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) utilisée, c’est pourquoi [ \< ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)le message>est spécifié à l’intérieur du>de sécurité .</span><span class="sxs-lookup"><span data-stu-id="32c16-114">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="32c16-115">[ \<L’émetteur>](../../configure-apps/file-schema/wcf/issuer.md) élément à l’intérieur du [ \<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) spécifie l’adresse et la liaison pour la STS qui émet un jeton de sécurité au client afin que le client puisse s’authentifier au `ICalculator` service.</span><span class="sxs-lookup"><span data-stu-id="32c16-115">The [\<issuer>](../../configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>
  
<span data-ttu-id="32c16-116">La configuration de cette liaison sur le service est indiquée dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="32c16-116">The configuration of this binding on the service is shown in the following code:</span></span>

```xml
<bindings>
  <ws2007FederationHttpBinding>
    <binding name="ServiceFed" >
      <security mode ="Message">
        <message issuedKeyType ="SymmetricKey"
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >
          <!-- Metadata address for Security Token Service -->
          <issuerMetadata address ="http://localhost:8000/sts/mex" >
            <identity>
              <certificateReference storeLocation ="CurrentUser"
                                    storeName="TrustedPeople"
                                    x509FindType ="FindBySubjectDistinguishedName"
                                    findValue ="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </ws2007FederationHttpBinding>
</bindings>
```

<span data-ttu-id="32c16-117">Sur le [ \<>de sécurité, ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)la `security` valeur précise quel mode de sécurité doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="32c16-117">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="32c16-118">Dans cet `message` échantillon, la sécurité est [ \<](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) utilisée, c’est pourquoi [ \< ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)le message>est spécifié à l’intérieur du>de sécurité .</span><span class="sxs-lookup"><span data-stu-id="32c16-118">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="32c16-119">[ \<L’émetteurMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) élément de `ws2007FederationHttpBinding` l’intérieur du [ \<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) spécifie l’adresse et l’identité d’un point de terminaison qui peut être utilisé pour récupérer les métadonnées pour la STS.</span><span class="sxs-lookup"><span data-stu-id="32c16-119">The [\<issuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>

<span data-ttu-id="32c16-120">Le comportement du service est affiché dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="32c16-120">The behavior for the service is shown in the following code:</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name ="ServiceBehaviour" >
      <serviceDebug includeExceptionDetailInFaults ="true"/>
      <serviceMetadata httpGetEnabled ="true"/>
      <serviceCredentials>
        <issuedTokenAuthentication>
          <knownCertificates>
            <add storeLocation ="LocalMachine"
                 storeName="TrustedPeople"
                 x509FindType="FindBySubjectDistinguishedName"
                 findValue="CN=STS" />
          </knownCertificates>
        </issuedTokenAuthentication>
        <serviceCertificate storeLocation ="LocalMachine"
                            storeName ="My"
                            x509FindType ="FindBySubjectDistinguishedName"
                            findValue ="CN=localhost"/>
      </serviceCredentials>
    </behavior>
  </serviceBehaviors>
</behaviors>
```
  
<span data-ttu-id="32c16-121">[ \<L'>d'> d’auteur de l’Auteur de l’Autriche délivrée](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) permet au service de spécifier les contraintes sur les jetons qu’il permet aux clients de présenter lors de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="32c16-121">The [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="32c16-122">Cette configuration spécifie que les jetons signés par un certificat dont le nom du sujet est CN=STS sont acceptés par le service.</span><span class="sxs-lookup"><span data-stu-id="32c16-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>

<span data-ttu-id="32c16-123">STS rend un point de terminaison unique disponible à l'aide du <xref:System.ServiceModel.WS2007HttpBinding> standard.</span><span class="sxs-lookup"><span data-stu-id="32c16-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="32c16-124">Le service répond aux demandes de jeton des clients.</span><span class="sxs-lookup"><span data-stu-id="32c16-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="32c16-125">Si le client est authentifié à l'aide d'un compte Windows, le service émet un jeton qui contient le nom d'utilisateur du client sous forme d'une revendication.</span><span class="sxs-lookup"><span data-stu-id="32c16-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="32c16-126">Dans le cadre de la création du jeton, le STS le signe à l'aide de la clé privée associée au certificat CN=STS.</span><span class="sxs-lookup"><span data-stu-id="32c16-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="32c16-127">Par ailleurs, il crée une clé symétrique et la chiffre à l'aide de la clé publique associée au certificat CN=localhost.</span><span class="sxs-lookup"><span data-stu-id="32c16-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="32c16-128">Lorsqu'il retourne le jeton au client, le STS retourne également la clé symétrique.</span><span class="sxs-lookup"><span data-stu-id="32c16-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="32c16-129">Le client présente le jeton émis au service `ICalculator` et prouve qu'il connaît la clé symétrique en signant le message à l'aide de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="32c16-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>

<span data-ttu-id="32c16-130">Lorsque vous exécutez l'exemple, la demande de jeton de sécurité s'affiche dans la fenêtre de console du STS.</span><span class="sxs-lookup"><span data-stu-id="32c16-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="32c16-131">Les demandes et réponses de l'opération s'affichent dans les fenêtres de console du client et du service.</span><span class="sxs-lookup"><span data-stu-id="32c16-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="32c16-132">Appuyez sur ENTER dans l'une ou l'autre de ces fenêtres pour arrêter l'application leur correspondant.</span><span class="sxs-lookup"><span data-stu-id="32c16-132">Press ENTER in any of the console windows to shut down the application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

<span data-ttu-id="32c16-133">Le fichier *Setup.bat* inclus dans cet échantillon vous permet de configurer le serveur et STS avec les certificats pertinents pour exécuter une application auto-hébergée.</span><span class="sxs-lookup"><span data-stu-id="32c16-133">The *Setup.bat* file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="32c16-134">Il crée deux certificats dans le magasin de certificats LocalMachine/TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="32c16-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="32c16-135">Le nom du sujet du premier certificat est CN=STS. Ce certificat est utilisé par le STS pour signer les jetons de sécurité qu'il émet au client.</span><span class="sxs-lookup"><span data-stu-id="32c16-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="32c16-136">Le nom du sujet du deuxième certificat est CN=localhost. Ce certificat est utilisé par le STS pour chiffrer une clé de sorte que le service puisse la déchiffrer.</span><span class="sxs-lookup"><span data-stu-id="32c16-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="32c16-137">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="32c16-137">To set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="32c16-138">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](one-time-setup-procedure-for-the-wcf-samples.md)</span><span class="sxs-lookup"><span data-stu-id="32c16-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="32c16-139">Ouvrez une invite de commande de développeur pour Visual Studio avec des privilèges d’administrateur et exécutez le fichier Setup.bat pour créer les certificats requis.</span><span class="sxs-lookup"><span data-stu-id="32c16-139">Open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>

 <span data-ttu-id="32c16-140">Ce fichier de lot utilise *Certmgr.exe* et Makecert.exe, qui sont distribués avec le Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="32c16-140">This batch file uses *Certmgr.exe* and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="32c16-141">Cependant, vous devez exécuter *Setup.bat* à partir d’une invite de commande Visual Studio pour permettre au script de trouver ces outils.</span><span class="sxs-lookup"><span data-stu-id="32c16-141">However, you must run *Setup.bat* from within a Visual Studio command prompt to enable the script to find these tools.</span></span>

1. <span data-ttu-id="32c16-142">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="32c16-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="32c16-143">Pour exécuter l’échantillon dans une configuration mono-ou cross-computer, suivez les instructions dans [Running the Windows Communication Foundation Samples](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="32c16-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="32c16-144">Si vous utilisez Windows Vista, vous devez exécuter *Service.exe*, *Client.exe*, et *SecurityTokenService.exe* avec des privilèges élevés (clic droit les fichiers, puis cliquez sur **Run en tant qu’administrateur**).</span><span class="sxs-lookup"><span data-stu-id="32c16-144">If you are using Windows Vista, you must run *Service.exe*, *Client.exe*, and *SecurityTokenService.exe* with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="32c16-145">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="32c16-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="32c16-146">Recherchez le répertoire (par défaut) suivant avant de continuer :</span><span class="sxs-lookup"><span data-stu-id="32c16-146">Check for the following (default) directory before continuing:</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="32c16-147">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="32c16-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="32c16-148">Cet exemple se trouve dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="32c16-148">This sample is located in the following directory:</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
