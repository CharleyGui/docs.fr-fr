---
title: Trusted Facade Service
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 80f139ace43d5f8d2136528681386711bea7a1e5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295052"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="48885-102">Trusted Facade Service</span><span class="sxs-lookup"><span data-stu-id="48885-102">Trusted Facade Service</span></span>

<span data-ttu-id="48885-103">Cet exemple de scénario montre comment transmettre les informations d’identité d’un appelant d’un service à un autre à l’aide de l’infrastructure de sécurité Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="48885-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="48885-104">Exposer les fonctionnalités fournies par un service au réseau public à l'aide d'un service de façade correspond à un modèle de conception standard.</span><span class="sxs-lookup"><span data-stu-id="48885-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="48885-105">Le service de façade, qui se trouve en principe dans le réseau de périmètre (également appelé sous-réseau filtré), communique avec le service principal, lequel implémente la logique métier et l'accès aux données internes.</span><span class="sxs-lookup"><span data-stu-id="48885-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="48885-106">Le canal de communication entre ces deux services traverse un pare-feu et est habituellement utilisé à une seule fin.</span><span class="sxs-lookup"><span data-stu-id="48885-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="48885-107">Cet exemple comporte les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="48885-107">This sample consists of the following components:</span></span>  
  
- <span data-ttu-id="48885-108">Client de calculatrice</span><span class="sxs-lookup"><span data-stu-id="48885-108">Calculator client</span></span>  
  
- <span data-ttu-id="48885-109">Service de façade de calculatrice</span><span class="sxs-lookup"><span data-stu-id="48885-109">Calculator façade service</span></span>  
  
- <span data-ttu-id="48885-110">Service principal de calculatrice</span><span class="sxs-lookup"><span data-stu-id="48885-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="48885-111">Le service de façade est chargé de valider la demande et d'authentifier l'appelant.</span><span class="sxs-lookup"><span data-stu-id="48885-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="48885-112">Après authentification de l'appelant et validation de la demande, il transfert celle-ci au service principal à l'aide du canal de communication contrôlé depuis le réseau de périmètre vers le réseau interne.</span><span class="sxs-lookup"><span data-stu-id="48885-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="48885-113">Le service de façade ajoute à la demande transférée des informations relatives à l'identité de l'appelant que le service principal pourra utiliser à des fins de traitement.</span><span class="sxs-lookup"><span data-stu-id="48885-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="48885-114">L'identité de l'appelant est transmise à l'aide d'un jeton de sécurité `Username` figurant dans l'en-tête `Security` du message.</span><span class="sxs-lookup"><span data-stu-id="48885-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="48885-115">L’exemple utilise l’infrastructure de sécurité WCF pour transmettre et extraire ces informations à partir de l' `Security` en-tête.</span><span class="sxs-lookup"><span data-stu-id="48885-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="48885-116">Le service principal approuve le service de façade pour authentifier l'appelant.</span><span class="sxs-lookup"><span data-stu-id="48885-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="48885-117">C'est pourquoi le service principal n'authentifie pas à nouveau l'appelant. Il utilise, en revanche, les informations d'identité fournies par le service de façade dans la demande transférée.</span><span class="sxs-lookup"><span data-stu-id="48885-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="48885-118">Dans le cadre de cette relation de confiance, il est essentiel que le service principal authentifie le service de façade afin de garantir la provenance depuis une source fiable (dans ce cas, le service de façade) du message transféré.</span><span class="sxs-lookup"><span data-stu-id="48885-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="48885-119">Implémentation</span><span class="sxs-lookup"><span data-stu-id="48885-119">Implementation</span></span>  

 <span data-ttu-id="48885-120">Dans cet exemple, deux voies de communication sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="48885-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="48885-121">La première entre le client et le service de façade, la seconde entre le service de façade et le service principal.</span><span class="sxs-lookup"><span data-stu-id="48885-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="48885-122">Voie de communication entre le client et le service de façade</span><span class="sxs-lookup"><span data-stu-id="48885-122">Communication Path between Client and Façade Service</span></span>  

 <span data-ttu-id="48885-123">La voie de communication entre le client et le service de façade utilise `wsHttpBinding` avec un type d'informations d'identification de client `UserName` .</span><span class="sxs-lookup"><span data-stu-id="48885-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="48885-124">Cela signifie que le client s'authentifie auprès du service de façade à l'aide d'un nom d'utilisateur et d'un mot de passe et que le service de façade s'authentifie auprès du client à l'aide d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="48885-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="48885-125">La configuration de la liaison ressemble à l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="48885-125">The binding configuration looks like the following example.</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="48885-126">Le service de façade authentifie l'appelant à l'aide de l'implémentation `UserNamePasswordValidator` personnalisée.</span><span class="sxs-lookup"><span data-stu-id="48885-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="48885-127">Dans le cadre de cet exemple, le processus d'authentification se contente seulement de vérifier que le nom d'utilisateur de l'appelant correspond au mot de passe présenté.</span><span class="sxs-lookup"><span data-stu-id="48885-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="48885-128">Dans la réalité, il y a de grandes chances que l'utilisateur soit authentifié à l'aide d'Active Directory ou d'un fournisseur d'appartenances ASP.NET personnalisé.</span><span class="sxs-lookup"><span data-stu-id="48885-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="48885-129">L'implémentation du validateur réside dans le fichier `FacadeService.cs` .</span><span class="sxs-lookup"><span data-stu-id="48885-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="48885-130">Le validateur personnalisé est configuré pour être utilisé à l'intérieur du comportement `serviceCredentials` , dans le fichier de configuration du service de façade.</span><span class="sxs-lookup"><span data-stu-id="48885-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="48885-131">Ce comportement est également utilisé pour configurer le certificat X.509 du service.</span><span class="sxs-lookup"><span data-stu-id="48885-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate
               findValue="localhost"
               storeLocation="LocalMachine"
               storeName="My"
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="48885-132">Voie de communication entre le service de façade et le service principal</span><span class="sxs-lookup"><span data-stu-id="48885-132">Communication Path between Façade Service and Backend Service</span></span>  

 <span data-ttu-id="48885-133">La voie de communication entre le service de façade et le service principal utilise une liaison `customBinding` qui se compose de plusieurs éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="48885-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="48885-134">Cette liaison remplit deux fonctions.</span><span class="sxs-lookup"><span data-stu-id="48885-134">This binding accomplishes two things.</span></span> <span data-ttu-id="48885-135">Elle authentifie le service de façade et le service principal afin de garantir que la communication est sécurisée et qu'elle provient d'une source fiable.</span><span class="sxs-lookup"><span data-stu-id="48885-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="48885-136">En outre, elle transmet l'identité de l'appelant initial à l'intérieur du jeton de sécurité `Username` .</span><span class="sxs-lookup"><span data-stu-id="48885-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="48885-137">Dans ce cas, seul le nom d'utilisateur de l'appelant initial est transmis au service principal, son mot de passe ne figure pas dans le message.</span><span class="sxs-lookup"><span data-stu-id="48885-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="48885-138">La raison en est que le service principal approuve le service de façade pour authentifier l'appelant avant que la demande de ce dernier de ne lui soit transféré.</span><span class="sxs-lookup"><span data-stu-id="48885-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="48885-139">Le service de façade s'authentifiant auprès du service principal, ce dernier peut se fier aux informations contenues dans la demande transférée.</span><span class="sxs-lookup"><span data-stu-id="48885-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="48885-140">Le code suivant contient la configuration de liaison utilisée par cette voie de communication.</span><span class="sxs-lookup"><span data-stu-id="48885-140">The following is the binding configuration for this communication path.</span></span>  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="48885-141">L' [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément de liaison s’occupe de la transmission et de l’extraction du nom d’utilisateur de l’appelant initial.</span><span class="sxs-lookup"><span data-stu-id="48885-141">The [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="48885-142">[\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md)Et [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) prennent en charge l’authentification de la façade et des services principaux et la protection des messages.</span><span class="sxs-lookup"><span data-stu-id="48885-142">The [\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="48885-143">Pour transférer la demande, l’implémentation du service de façade doit fournir le nom d’utilisateur de l’appelant initial afin que l’infrastructure de sécurité WCF puisse la placer dans le message transféré.</span><span class="sxs-lookup"><span data-stu-id="48885-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="48885-144">Pour que l'implémentation du service de façade puisse fournir ce nom d'utilisateur, ce dernier doit être défini dans la propriété `ClientCredentials` de l'instance de proxy de client utilisée par ce service pour communiquer avec le service principal.</span><span class="sxs-lookup"><span data-stu-id="48885-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="48885-145">Le code suivant illustre la manière dont la méthode `GetCallerIdentity` est implémentée sur le service de façade.</span><span class="sxs-lookup"><span data-stu-id="48885-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="48885-146">Ce même modèle est utilisé par d'autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="48885-146">Other methods use the same pattern.</span></span>  
  
```csharp  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 <span data-ttu-id="48885-147">Comme illustré dans le code précédent, le mot de passe n'est pas défini dans la propriété' `ClientCredentials` , seul le nom d'utilisateur est défini.</span><span class="sxs-lookup"><span data-stu-id="48885-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="48885-148">L’infrastructure de sécurité WCF crée un jeton de sécurité de nom d’utilisateur sans mot de passe dans ce cas, ce qui est exactement ce qui est nécessaire dans ce scénario.</span><span class="sxs-lookup"><span data-stu-id="48885-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="48885-149">Sur le service principal, les informations contenues dans le jeton de sécurité de nom d'utilisateur doivent être authentifiées.</span><span class="sxs-lookup"><span data-stu-id="48885-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="48885-150">Par défaut, la sécurité WCF tente de mapper l’utilisateur à un compte Windows à l’aide du mot de passe fourni.</span><span class="sxs-lookup"><span data-stu-id="48885-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="48885-151">Dans ce cas, aucun mot de passe n'est communiqué et le service principal n'est pas obligé d'authentifier le nom d'utilisateur, le service de façade ayant déjà procédé à cette authentification.</span><span class="sxs-lookup"><span data-stu-id="48885-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="48885-152">Pour implémenter cette fonctionnalité dans WCF, un personnalisé `UserNamePasswordValidator` est fourni, qui impose uniquement qu’un nom d’utilisateur est spécifié dans le jeton et n’exécute pas d’authentification supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="48885-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="48885-153">Le validateur personnalisé est configuré pour être utilisé à l'intérieur du comportement `serviceCredentials` , dans le fichier de configuration du service de façade.</span><span class="sxs-lookup"><span data-stu-id="48885-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="48885-154">Pour extraire les informations de nom d'utilisateur et les informations concernant le compte du service de façade approuvé, l'implémentation de service principal utilise la classe `ServiceSecurityContext` .</span><span class="sxs-lookup"><span data-stu-id="48885-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="48885-155">L'exemple de code suivant illustre la manière dont la méthode `GetCallerIdentity` est implémentée.</span><span class="sxs-lookup"><span data-stu-id="48885-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
```csharp  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 <span data-ttu-id="48885-156">Les informations relatives au compte du service de façade sont extraites à l'aide de la propriété `ServiceSecurityContext.Current.WindowsIdentity` .</span><span class="sxs-lookup"><span data-stu-id="48885-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="48885-157">Pour accéder aux informations de l'appelant initial, le service principal utilise la propriété `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` .</span><span class="sxs-lookup"><span data-stu-id="48885-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="48885-158">Le service recherche une revendication `Identity` ayant le type `Name`.</span><span class="sxs-lookup"><span data-stu-id="48885-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="48885-159">Cette revendication est générée automatiquement par l’infrastructure de sécurité WCF à partir des informations contenues dans le `Username` jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="48885-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="48885-160">Exécution de l’exemple</span><span class="sxs-lookup"><span data-stu-id="48885-160">Running the sample</span></span>  

 <span data-ttu-id="48885-161">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="48885-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="48885-162">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="48885-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="48885-163">Vous pouvez appuyer sur le bouton ENTER de la fenêtre du service de façade ou de la fenêtre du service principal pour arrêter ces derniers.</span><span class="sxs-lookup"><span data-stu-id="48885-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
```console  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="48885-164">Le fichier de commandes Setup.bat contenu dans cet exemple de scénario vous permet de configurer le serveur en utilisant le certificat requis pour permettre au service de façade exigeant la sécurité basée sur les certificats de s'authentifier auprès du client.</span><span class="sxs-lookup"><span data-stu-id="48885-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="48885-165">Pour plus d'informations, consultez la procédure d'installation figurant en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="48885-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="48885-166">Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes.</span><span class="sxs-lookup"><span data-stu-id="48885-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="48885-167">Création du certificat de serveur</span><span class="sxs-lookup"><span data-stu-id="48885-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="48885-168">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="48885-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="48885-169">La variable `%SERVER_NAME%` spécifie le nom du serveur, sa valeur par défaut est localhost.</span><span class="sxs-lookup"><span data-stu-id="48885-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="48885-170">Le certificat est stocké dans le magasin LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="48885-170">The certificate is stored in the LocalMachine store.</span></span>  
  
- <span data-ttu-id="48885-171">Installation du certificat du service de façade dans le magasin de certificats approuvés du client.</span><span class="sxs-lookup"><span data-stu-id="48885-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="48885-172">La ligne suivante copie le certificat du service de façade dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="48885-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="48885-173">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="48885-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="48885-174">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple d'un certificat émis par Microsoft, il n'est pas nécessaire d'ajouter le certificat du serveur au magasin de certificats du client.</span><span class="sxs-lookup"><span data-stu-id="48885-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="48885-175">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="48885-175">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="48885-176">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="48885-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="48885-177">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="48885-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="48885-178">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="48885-178">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="48885-179">Assurez-vous que le chemin d'accès pointe vers le dossier dans lequel Makecert.exe se trouve.</span><span class="sxs-lookup"><span data-stu-id="48885-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="48885-180">Exécutez Setup.bat à partir du dossier d'installation de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="48885-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="48885-181">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="48885-181">This installs all the certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="48885-182">Lancez le fichier BackendService.exe figurant dans le répertoire \BackendService\bin dans une fenêtre de console distincte.</span><span class="sxs-lookup"><span data-stu-id="48885-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4. <span data-ttu-id="48885-183">Lancez le fichier FacadeService.exe figurant dans le répertoire \FacadeService\bin dans une fenêtre de console distincte.</span><span class="sxs-lookup"><span data-stu-id="48885-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5. <span data-ttu-id="48885-184">Lancez Client.exe à partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="48885-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="48885-185">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="48885-185">Client activity is displayed on the client console application.</span></span>  
  
6. <span data-ttu-id="48885-186">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="48885-186">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="48885-187">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="48885-187">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="48885-188">Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.</span><span class="sxs-lookup"><span data-stu-id="48885-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="48885-189">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="48885-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="48885-190">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="48885-190">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="48885-191">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="48885-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="48885-192">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="48885-192">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`
