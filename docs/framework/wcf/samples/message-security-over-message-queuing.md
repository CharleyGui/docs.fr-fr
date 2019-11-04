---
title: Message Security over Message Queuing
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: d27ee01636e37ac8f09c4f7dc497f14bfac1b0f1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424122"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="eaaf5-102">Message Security over Message Queuing</span><span class="sxs-lookup"><span data-stu-id="eaaf5-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="eaaf5-103">Cet exemple montre comment implémenter une application qui utilise WS-Security avec l'authentification de certificat X.509v3 pour le client et requiert l'authentification de serveur à l'aide du certificat X.509v3 du serveur via MSMQ.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="eaaf5-104">La sécurité de message est parfois plus souhaitable pour garantir que les messages du magasin MSMQ demeurent chiffrés et que l'application peut effectuer sa propre authentification du message.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="eaaf5-105">Cet exemple est basé sur l’exemple de [liaison MSMQ transactionnelle](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) .</span><span class="sxs-lookup"><span data-stu-id="eaaf5-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="eaaf5-106">Les messages sont chiffrés et signés.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-106">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eaaf5-107">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="eaaf5-107">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="eaaf5-108">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eaaf5-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="eaaf5-109">Si le service est exécuté en premier, il vérifie que la file d'attente existe.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="eaaf5-110">Si la file d'attente n'existe pas, le service en crée une.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="eaaf5-111">Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="eaaf5-112">Procédez comme suit pour créer une file d'attente dans Windows 2008 :</span><span class="sxs-lookup"><span data-stu-id="eaaf5-112">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="eaaf5-113">Ouvrez Gestionnaire de serveur dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-113">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="eaaf5-114">Développez l’onglet **fonctionnalités** .</span><span class="sxs-lookup"><span data-stu-id="eaaf5-114">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="eaaf5-115">Cliquez avec le bouton droit sur **files d’attente de messages privées**, puis sélectionnez **nouveau**, **file d’attente privée**.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="eaaf5-116">Activez la case à cocher **transactionnelle** .</span><span class="sxs-lookup"><span data-stu-id="eaaf5-116">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="eaaf5-117">Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="eaaf5-118">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eaaf5-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="eaaf5-119">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="eaaf5-119">To run the sample on the same computer</span></span>

1. <span data-ttu-id="eaaf5-120">Vérifiez que le chemin d’accès inclut le dossier qui contient Makecert.exe et FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2. <span data-ttu-id="eaaf5-121">Exécutez Setup.bat à partir du dossier d'installation de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="eaaf5-122">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-122">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="eaaf5-123">Assurez-vous d'effacer les certificats en exécutant Cleanup.bat une fois l'exemple terminé.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="eaaf5-124">D'autres exemples de sécurité utilisent ces mêmes certificats.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-124">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="eaaf5-125">Lancez Service.exe à partir de \service\bin.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-125">Launch Service.exe from \service\bin.</span></span>  
  
4. <span data-ttu-id="eaaf5-126">Lancez Client.exe à partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="eaaf5-127">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-127">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="eaaf5-128">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="eaaf5-128">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="eaaf5-129">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="eaaf5-129">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="eaaf5-130">Copiez les fichiers Setup.bat, Cleanup.bat et ImportClientCert.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2. <span data-ttu-id="eaaf5-131">Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3. <span data-ttu-id="eaaf5-132">Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="eaaf5-133">Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4. <span data-ttu-id="eaaf5-134">Sur le serveur, exécutez `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="eaaf5-135">L’exécution de `setup.bat` avec l’argument `service` crée un certificat de service avec le nom de domaine complet de l’ordinateur et exporte le certificat de service vers un fichier nommé service. cer.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5. <span data-ttu-id="eaaf5-136">Modifiez Service. exe. config du service pour refléter le nouveau nom de certificat (dans l’attribut `findValue` de la [\<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) qui est le même que le nom de domaine complet de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6. <span data-ttu-id="eaaf5-137">Copiez le fichier Service.cer du répertoire de service vers le répertoire client sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7. <span data-ttu-id="eaaf5-138">Sur le client, exécutez `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="eaaf5-139">L'exécution de `setup.bat` à l'aide de l'argument `client` crée un certificat client appelé client.com, puis exporte ce certificat vers un fichier nommé Client.cer.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8. <span data-ttu-id="eaaf5-140">Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="eaaf5-141">Pour ce faire, remplacez localhost par le nom de domaine complet du serveur.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="eaaf5-142">Vous devez également modifier le nom de certificat du service pour qu'il soit identique au nom de domaine complet de l'ordinateur de service (dans l'attribut `findValue` de l'élément `defaultCertificate` de `serviceCertificate` sous `clientCredentials`).</span><span class="sxs-lookup"><span data-stu-id="eaaf5-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="eaaf5-143">Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="eaaf5-144">Sur le client, exécutez `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="eaaf5-145">Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="eaaf5-146">Sur le serveur, exécutez `ImportClientCert.bat`. Cette opération importe le certificat client du fichier Client.cer dans le magasin LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="eaaf5-147">Sur l'ordinateur de service, lancez Service.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="eaaf5-148">Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="eaaf5-149">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="eaaf5-149">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="eaaf5-150">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="eaaf5-150">To clean up after the sample</span></span>  
  
- <span data-ttu-id="eaaf5-151">Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="eaaf5-152">Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="eaaf5-153">Si vous avez exécuté des exemples de Windows Communication Foundation (WCF) qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-153">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="eaaf5-154">Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="eaaf5-155">spécifications</span><span class="sxs-lookup"><span data-stu-id="eaaf5-155">Requirements</span></span>
 <span data-ttu-id="eaaf5-156">Cet exemple requiert l'installation et l'exécution de MSMQ.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-156">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="eaaf5-157">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="eaaf5-157">Demonstrates</span></span>
 <span data-ttu-id="eaaf5-158">Le client chiffre le message à l'aide de la clé publique du service et signe le message qui utilise son propre certificat.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="eaaf5-159">Le service qui lit le message depuis la file d'attente authentifie le certificat client avec le certificat de son magasin de personnes de confiance.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="eaaf5-160">Il déchiffre alors le message et distribue le message à l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-160">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="eaaf5-161">Étant donné que le message Windows Communication Foundation (WCF) est transporté comme une charge dans le corps du message MSMQ, le corps reste chiffré dans le magasin MSMQ.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-161">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="eaaf5-162">Cela protège le message contre toute divulgation non désirée du message.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="eaaf5-163">Notez que MSMQ lui-même ne sait pas si le message qu'il transporte est chiffré.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="eaaf5-164">L'exemple montre comment l'authentification mutuelle au niveau du message peut être utilisée avec MSMQ.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="eaaf5-165">Les certificats sont échangés hors bande.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="eaaf5-166">C'est toujours le cas avec les applications mises en file d'attente parce que le service et le client n'ont pas à être en marche en même temps.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="eaaf5-167">Description</span><span class="sxs-lookup"><span data-stu-id="eaaf5-167">Description</span></span>
 <span data-ttu-id="eaaf5-168">L’exemple de code de client et de service est identique à l’exemple de [liaison MSMQ transactionnelle](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) , avec une différence.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="eaaf5-169">Le contrat d’opération est annoté avec le niveau de protection, ce qui suggère que le message doit être signé et chiffré.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="eaaf5-170">Pour garantir que le message est sécurisé à l'aide du jeton requis pour identifier le service et le client, App.config contient des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="eaaf5-171">La configuration client spécifie le certificat de service pour authentifier le service.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="eaaf5-172">Elle utilise son magasin LocalMachine comme magasin de confiance pour s'appuyer sur la validation du service.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="eaaf5-173">Elle spécifie également le certificat client joint avec le message pour l'authentification du service du client.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <system.serviceModel>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                binding="netMsmqBinding"
                bindingConfiguration="messageSecurityBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"
                behaviorConfiguration="ClientCertificateBehavior" />
    </client>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate"/>
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <!--
        The clientCredentials behavior allows one to define a certificate to present to a service.
        A certificate is used by a client to authenticate itself to the service and provide message integrity.
        This configuration references the "client.com" certificate installed during the setup instructions.
        -->
          <clientCredentials>
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />
            <serviceCertificate>
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="eaaf5-174">Notez que le mode de sécurité est Message et que le ClientCredentialType a pour valeur Certificat.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="eaaf5-175">La configuration du service inclut un comportement de service qui spécifie les informations d'identification du service utilisées lorsque le client authentifie le service.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="eaaf5-176">Le nom du sujet du certificat de serveur est spécifié dans l’attribut `findValue` de la [\<ServiceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="eaaf5-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />
  </appSettings>

  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"
          behaviorConfiguration="PurchaseOrderServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
          </baseAddresses>
        </host>
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                  binding="netMsmqBinding"
                  bindingConfiguration="messageSecurityBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="PurchaseOrderServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <!--
               The serviceCredentials behavior allows one to define a service certificate.
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.
               This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
            <clientCertificate>
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </clientCertificate>
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

 <span data-ttu-id="eaaf5-177">L'exemple montre comment contrôler l'authentification à l'aide de la configuration, et comment obtenir l'identité de l'appelant à partir du contexte de sécurité, tel qu'indiqué dans l'exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="eaaf5-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

```csharp
// Service class which implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    private string GetCallerIdentity()
    {
        // The client certificate is not mapped to a Windows identity by default.
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information
        // in the certificate that the client used to authenticate itself to the service.
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }
  //…
}
```

 <span data-ttu-id="eaaf5-178">Lorsqu'il est exécuté, le code de service affiche l'identification du client.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="eaaf5-179">L'exemple suivant illustre une sortie du code de service :</span><span class="sxs-lookup"><span data-stu-id="eaaf5-179">The following is a sample output from the service code:</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

## <a name="comments"></a><span data-ttu-id="eaaf5-180">Comments</span><span class="sxs-lookup"><span data-stu-id="eaaf5-180">Comments</span></span>

- <span data-ttu-id="eaaf5-181">Création du certificat client</span><span class="sxs-lookup"><span data-stu-id="eaaf5-181">Creating the client certificate.</span></span>

     <span data-ttu-id="eaaf5-182">La ligne suivante du fichier de commandes crée le certificat client.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="eaaf5-183">Le nom client spécifié est utilisé dans le nom du sujet du certificat créé.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="eaaf5-184">Le certificat est stocké dans le magasin `My` situé au niveau de l'emplacement de magasin `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="eaaf5-185">Installation du certificat client dans le magasin de certificats approuvés du serveur.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-185">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="eaaf5-186">La ligne suivante du fichier de commandes copie le certificat client dans le magasin TrustedPeople du serveur afin que le serveur puisse prendre les décisions d'approbation ou de non-approbation appropriées.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="eaaf5-187">Pour qu’un certificat installé dans le magasin TrustedPeople soit approuvé par un service Windows Communication Foundation (WCF), le mode de validation du certificat client doit être défini sur `PeerOrChainTrust` ou sur `PeerTrust` valeur.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-187">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="eaaf5-188">Pour connaître la procédure à suivre à l'aide d'un fichier de configuration, consultez l'exemple de configuration de service précédent.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="eaaf5-189">Création du certificat de serveur</span><span class="sxs-lookup"><span data-stu-id="eaaf5-189">Creating the server certificate.</span></span>

     <span data-ttu-id="eaaf5-190">Les lignes suivantes du fichier de commandes Setup.bat génèrent le certificat de serveur à utiliser :</span><span class="sxs-lookup"><span data-stu-id="eaaf5-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="eaaf5-191">La variable %SERVER_NAME% spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="eaaf5-192">Le certificat est stocké dans le magasin LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="eaaf5-193">Si le fichier de commandes d’installation est exécuté avec un argument service (par exemple, `setup.bat service`),% SERVER_NAME% contient le nom de domaine complet de l’ordinateur. Dans le cas contraire, la valeur par défaut est localhost</span><span class="sxs-lookup"><span data-stu-id="eaaf5-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

- <span data-ttu-id="eaaf5-194">Installation du certificat de serveur dans le magasin de certificats approuvés du client.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-194">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="eaaf5-195">La ligne suivante copie le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="eaaf5-196">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="eaaf5-197">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple d'un certificat émis par Microsoft, il n'est pas nécessaire d'ajouter le certificat du serveur au magasin de certificats du client.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="eaaf5-198">Si vous utilisez une édition non-américaine de Microsoft Windows, vous devez modifier le fichier Setup. bat et remplacer le nom de compte « NT AUTHORITY\NETWORK SERVICE » par votre équivalent régional.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eaaf5-199">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="eaaf5-200">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-200">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="eaaf5-201">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eaaf5-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eaaf5-202">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="eaaf5-202">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
