---
title: "Comment : spécifier des informations d'identification pour la sécurité des canaux"
ms.date: 03/30/2017
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
ms.openlocfilehash: 45a13460ce94cbacae0465fede4b455a2833ce81
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596940"
---
# <a name="how-to-specify-channel-security-credentials"></a><span data-ttu-id="72e42-102">Comment : spécifier des informations d'identification pour la sécurité des canaux</span><span class="sxs-lookup"><span data-stu-id="72e42-102">How to: Specify Channel Security Credentials</span></span>
<span data-ttu-id="72e42-103">Le moniker de service Windows Communication Foundation (WCF) permet aux applications COM d’appeler des services WCF.</span><span class="sxs-lookup"><span data-stu-id="72e42-103">The Windows Communication Foundation (WCF) Service Moniker allows COM applications to call WCF services.</span></span> <span data-ttu-id="72e42-104">La plupart des services WCF requièrent que le client spécifie des informations d’identification pour l’authentification et l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="72e42-104">Most WCF services require the client to specify credentials for authentication and authorization.</span></span> <span data-ttu-id="72e42-105">Lors de l’appel d’un service WCF à partir d’un client WCF, vous pouvez spécifier ces informations d’identification en code managé ou dans un fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="72e42-105">When calling a WCF service from a WCF client, you can specify these credentials in managed code or in an application configuration file.</span></span> <span data-ttu-id="72e42-106">Lors de l’appel d’un service WCF à partir d’une application COM, vous pouvez utiliser l' <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface pour spécifier les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="72e42-106">When calling a WCF service from a COM application, you can use the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface to specify credentials.</span></span> <span data-ttu-id="72e42-107">Cette rubrique illustre diverses méthodes pour spécifier des informations d'identification à l'aide de l'interface <xref:System.ServiceModel.ComIntegration.IChannelCredentials>.</span><span class="sxs-lookup"><span data-stu-id="72e42-107">This topic will illustrate various ways to specify credentials using the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72e42-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> est une interface basée sur IDispatch et vous ne rencontrerez pas de fonctionnalités IntelliSense dans l'environnement Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="72e42-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> is an IDispatch-based interface and you will not get IntelliSense functionality in the Visual Studio environment.</span></span>  
  
 <span data-ttu-id="72e42-109">Cet article utilise le service WCF défini dans l' [exemple de sécurité de message](../samples/message-security-sample.md).</span><span class="sxs-lookup"><span data-stu-id="72e42-109">This article will use the WCF service defined in the [Message Security Sample](../samples/message-security-sample.md).</span></span>  
  
### <a name="to-specify-a-client-certificate"></a><span data-ttu-id="72e42-110">Pour spécifier un certificat client</span><span class="sxs-lookup"><span data-stu-id="72e42-110">To specify a client certificate</span></span>  
  
1. <span data-ttu-id="72e42-111">Exécutez le fichier Setup.bat dans le répertoire de la sécurité de message pour créer et installer les certificats de test requis.</span><span class="sxs-lookup"><span data-stu-id="72e42-111">Run the Setup.bat file in the Message Security directory to create and install the required test certificates.</span></span>  
  
2. <span data-ttu-id="72e42-112">Ouvrez le projet de la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="72e42-112">Open the Message Security project.</span></span>  
  
3. <span data-ttu-id="72e42-113">Ajoutez `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` à la `ICalculator` définition de l’interface.</span><span class="sxs-lookup"><span data-stu-id="72e42-113">Add `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` to the `ICalculator` interface definition.</span></span>  
  
4. <span data-ttu-id="72e42-114">Ajoutez `bindingNamespace="http://Microsoft.ServiceModel.Samples"` à la balise de point de terminaison dans le fichier app. config du service.</span><span class="sxs-lookup"><span data-stu-id="72e42-114">Add `bindingNamespace="http://Microsoft.ServiceModel.Samples"` to the endpoint tag in the App.config for the service.</span></span>  
  
5. <span data-ttu-id="72e42-115">Générez l'exemple de la sécurité de message et exécutez Service.exe.</span><span class="sxs-lookup"><span data-stu-id="72e42-115">Build the Message Security Sample and run Service.exe.</span></span> <span data-ttu-id="72e42-116">Utilisez Internet Explorer et accédez à l’URI du service ( `http://localhost:8000/ServiceModelSamples/Service` ) pour vous assurer que le service fonctionne.</span><span class="sxs-lookup"><span data-stu-id="72e42-116">Use Internet Explorer and browse to the service's URI (`http://localhost:8000/ServiceModelSamples/Service`) to ensure that the service is working.</span></span>  
  
6. <span data-ttu-id="72e42-117">Ouvrez Visual Basic 6.0 et créez un nouveau fichier .exe standard.</span><span class="sxs-lookup"><span data-stu-id="72e42-117">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="72e42-118">Ajoutez un bouton au formulaire et double-cliquez dessus pour ajouter le code suivant au gestionnaire Click :</span><span class="sxs-lookup"><span data-stu-id="72e42-118">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
        monString = monString + ", binding=BasicHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
        Set monikerProxy = GetObject(monString)  
  
        'Set the Service Certificate.  
     monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetDefaultServiceCertificateFromStore "CurrentUser", "TrustedPeople", "FindBySubjectName", "localhost"  
  
        'Set the Client Certificate.  
        monikerProxy.ChannelCredentials.SetClientCertificateFromStoreByName "CN=client.com", "CurrentUser", "My"  
        MsgBox monikerProxy.Add(3, 4)  
    ```  
  
7. <span data-ttu-id="72e42-119">Exécutez l'application Visual Basic et vérifiez les résultats.</span><span class="sxs-lookup"><span data-stu-id="72e42-119">Run the Visual Basic application and verify the results.</span></span>  
  
     <span data-ttu-id="72e42-120">L'application Visual Basic affiche un message contenant le résultat de l'appel Add(3, 4).</span><span class="sxs-lookup"><span data-stu-id="72e42-120">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span> <span data-ttu-id="72e42-121">l'<xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> ou <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> peut également être utilisé à la place de <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> pour définir le certificat client :</span><span class="sxs-lookup"><span data-stu-id="72e42-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> or <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> can also be used in place of <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> to set the Client Certificate:</span></span>  
  
    ```vb  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
> <span data-ttu-id="72e42-122">Pour que fonctionne cet appel, le certificat client doit être approuvé sur l'ordinateur qui exécute le client.</span><span class="sxs-lookup"><span data-stu-id="72e42-122">For this call to work, the client certificate needs to be trusted on the machine the client is running on.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72e42-123">Si le moniker est mal formé ou si le service n'est pas disponible, l'appel à `GetObject` retourne une erreur indiquant que la syntaxe n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="72e42-123">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span> <span data-ttu-id="72e42-124">Si vous recevez cette erreur, assurez-vous que le moniker que vous utilisez est correct et que le service est disponible.</span><span class="sxs-lookup"><span data-stu-id="72e42-124">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
### <a name="to-specify-user-name-and-password"></a><span data-ttu-id="72e42-125">Pour spécifier un nom d'utilisateur et un mot de passe</span><span class="sxs-lookup"><span data-stu-id="72e42-125">To specify user name and password</span></span>  
  
1. <span data-ttu-id="72e42-126">Modifiez le fichier App.config du service pour utiliser `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="72e42-126">Modify the Service App.config file to use the `wsHttpBinding`.</span></span> <span data-ttu-id="72e42-127">Il est requis pour la validation du nom d’utilisateur et du mot de passe :</span><span class="sxs-lookup"><span data-stu-id="72e42-127">This is required for user name and password validation:</span></span>  

2. <span data-ttu-id="72e42-128">Affectez `clientCredentialType` à UserName :</span><span class="sxs-lookup"><span data-stu-id="72e42-128">Set the `clientCredentialType` to UserName:</span></span>  

3. <span data-ttu-id="72e42-129">Ouvrez Visual Basic 6.0 et créez un nouveau fichier .exe standard.</span><span class="sxs-lookup"><span data-stu-id="72e42-129">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="72e42-130">Ajoutez un bouton au formulaire et double-cliquez dessus pour ajouter le code suivant au gestionnaire Click :</span><span class="sxs-lookup"><span data-stu-id="72e42-130">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4. <span data-ttu-id="72e42-131">Exécutez l'application Visual Basic et vérifiez les résultats.</span><span class="sxs-lookup"><span data-stu-id="72e42-131">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="72e42-132">L'application Visual Basic affiche un message contenant le résultat de l'appel Add(3, 4).</span><span class="sxs-lookup"><span data-stu-id="72e42-132">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="72e42-133">La liaison spécifiée dans le moniker de service dans cet exemple a été remplacée par WSHttpBinding_ICalculator.</span><span class="sxs-lookup"><span data-stu-id="72e42-133">The binding specified in the service moniker in this sample has been changed to WSHttpBinding_ICalculator.</span></span> <span data-ttu-id="72e42-134">Notez aussi que vous devez fournir un nom d'utilisateur et un mot de passe valides dans l'appel à <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="72e42-134">Also note that you must supply a valid user name and password in the call to <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span></span>  
  
### <a name="to-specify-windows-credentials"></a><span data-ttu-id="72e42-135">Pour spécifier des informations d'identification Windows</span><span class="sxs-lookup"><span data-stu-id="72e42-135">To specify Windows Credentials</span></span>  
  
1. <span data-ttu-id="72e42-136">Affectez `clientCredentialType` à Windows dans le fichier App.config de service :</span><span class="sxs-lookup"><span data-stu-id="72e42-136">Set `clientCredentialType` to Windows in the Service App.config file:</span></span>  

2. <span data-ttu-id="72e42-137">Ouvrez Visual Basic 6.0 et créez un nouveau fichier .exe standard.</span><span class="sxs-lookup"><span data-stu-id="72e42-137">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="72e42-138">Ajoutez un bouton au formulaire et double-cliquez dessus pour ajouter le code suivant au gestionnaire Click :</span><span class="sxs-lookup"><span data-stu-id="72e42-138">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="72e42-139">Exécutez l'application Visual Basic et vérifiez les résultats.</span><span class="sxs-lookup"><span data-stu-id="72e42-139">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="72e42-140">L'application Visual Basic affiche un message contenant le résultat de l'appel Add(3, 4).</span><span class="sxs-lookup"><span data-stu-id="72e42-140">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="72e42-141">Vous devez remplacer "domain", "userID" et "password" par des valeurs valides.</span><span class="sxs-lookup"><span data-stu-id="72e42-141">You must replace "domain", "userID", and "password" with valid values.</span></span>  
  
### <a name="to-specify-an-issue-token"></a><span data-ttu-id="72e42-142">Pour spécifier un jeton d'émission</span><span class="sxs-lookup"><span data-stu-id="72e42-142">To specify an issue token</span></span>  
  
1. <span data-ttu-id="72e42-143">Ces jetons sont utilisés uniquement pour les applications qui utilisent la sécurité fédérée.</span><span class="sxs-lookup"><span data-stu-id="72e42-143">Issue tokens are used only for applications using federated security.</span></span> <span data-ttu-id="72e42-144">Pour plus d’informations sur la sécurité fédérée, consultez l’exemple de [Fédération et de jetons émis](federation-and-issued-tokens.md) et de [Fédération](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="72e42-144">For more information about federated security, see [Federation and Issued Tokens](federation-and-issued-tokens.md) and [Federation Sample](../samples/federation-sample.md).</span></span>  
  
     <span data-ttu-id="72e42-145">L'exemple de code Visual Basic suivant montre comment appeler la méthode <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> :</span><span class="sxs-lookup"><span data-stu-id="72e42-145">The following Visual Basic code example illustrates how to call the <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> method:</span></span>  
  
    ```vb
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     <span data-ttu-id="72e42-146">Pour plus d'informations sur les paramètres de cette méthode, consultez <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="72e42-146">For more information about the parameters for this method, see <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72e42-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72e42-147">See also</span></span>

- [<span data-ttu-id="72e42-148">Fédération</span><span class="sxs-lookup"><span data-stu-id="72e42-148">Federation</span></span>](federation.md)
- [<span data-ttu-id="72e42-149">Comment : configurer des informations d'identification sur un service FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="72e42-149">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="72e42-150">Comment : créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="72e42-150">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="72e42-151">Sécurité des messages</span><span class="sxs-lookup"><span data-stu-id="72e42-151">Message Security</span></span>](message-security-in-wcf.md)
- [<span data-ttu-id="72e42-152">Liaisons et sécurité</span><span class="sxs-lookup"><span data-stu-id="72e42-152">Bindings and Security</span></span>](bindings-and-security.md)
