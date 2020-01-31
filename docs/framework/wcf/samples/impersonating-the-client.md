---
title: Emprunt de l'identité du client
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: e9e85729b10d1c992a22f6c0bea65dfd1e21e7e4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742555"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="c9dcd-102">Emprunt de l'identité du client</span><span class="sxs-lookup"><span data-stu-id="c9dcd-102">Impersonating the Client</span></span>
<span data-ttu-id="c9dcd-103">Cet exemple montre comment emprunter l'identité de l'application de l'appelant au niveau du service afin que ce dernier puisse accéder aux ressources système pour le compte de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="c9dcd-104">Cet exemple est basé sur l’exemple d' [auto-hébergement](../../../../docs/framework/wcf/samples/self-host.md) .</span><span class="sxs-lookup"><span data-stu-id="c9dcd-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="c9dcd-105">Les fichiers de configuration du service et du client sont les mêmes que ceux de l’exemple [auto-hôte](../../../../docs/framework/wcf/samples/self-host.md) .</span><span class="sxs-lookup"><span data-stu-id="c9dcd-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9dcd-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c9dcd-107">Le code de service a été modifié afin que la méthode `Add` sur le service emprunte l'identité de l'appelant à l'aide de <xref:System.ServiceModel.OperationBehaviorAttribute>, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    Console.WriteLine("Received Add({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="c9dcd-108">En conséquence, le contexte de sécurité du thread en cours d'exécution est basculé pour emprunter l'identité de l'appelant avant d'entrer dans la méthode `Add` et est rétabli lorsqu'il quitte la méthode.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="c9dcd-109">La méthode `DisplayIdentityInformation` indiquée dans l'exemple de code suivant est une fonction utilitaire qui affiche l'identité de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
```csharp
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tThread Identity            :{0}",  
         WindowsIdentity.GetCurrent().Name);  
    Console.WriteLine("\t\tThread Identity level  :{0}",   
         WindowsIdentity.GetCurrent().ImpersonationLevel);  
    Console.WriteLine("\t\thToken                     :{0}",  
         WindowsIdentity.GetCurrent().Token.ToString());  
    return;  
}  
```  
  
 <span data-ttu-id="c9dcd-110">La méthode `Subtract` sur le service emprunte l'identité de l'appelant à l'aide d'appels impératifs, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
```csharp
public double Subtract(double n1, double n2)  
{  
    double result = n1 - n2;  
    Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    Console.WriteLine("Before impersonating");  
    DisplayIdentityInformation();  
  
    if (ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Impersonation ||  
        ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Delegation)  
    {  
        // Impersonate.  
        using (ServiceSecurityContext.Current.WindowsIdentity.Impersonate())  
        {  
            // Make a system call in the caller's context and ACLs   
            // on the system resource are enforced in the caller's context.   
            Console.WriteLine("Impersonating the caller imperatively");  
            DisplayIdentityInformation();  
        }  
    }  
    else  
    {  
        Console.WriteLine("ImpersonationLevel is not high enough to perform this operation.");  
    }  
  
    Console.WriteLine("After reverting");  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="c9dcd-111">Notez que dans ce cas, l'identité de l'appelant n'est pas empruntée pour l'ensemble de l'appel, mais uniquement pour une partie de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="c9dcd-112">En général, l'emprunt d'identité pour la plus petite étendue est préférable à l'emprunt d'identité pour l'ensemble de l'opération.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="c9dcd-113">Les autres méthodes n'empruntent pas l'identité de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="c9dcd-114">Le code client a été modifié pour affecter <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> au niveau d'emprunt d'identité.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="c9dcd-115">Le client spécifie le niveau d'emprunt d'identité à utiliser par le service, en utilisant l'énumération <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="c9dcd-116">L'énumération prend en charge les valeurs suivantes : <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> et <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="c9dcd-117">Pour effectuer un contrôle lors de l'accès à une ressource système sur l'ordinateur local protégé à l'aide des listes de contrôle d'accès Windows, le niveau d'emprunt d'identité doit avoir la valeur <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="c9dcd-118">Lorsque vous exécutez l'exemple, les requêtes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="c9dcd-119">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9dcd-120">Le service doit s’exécuter sous un compte d’administration ou le compte sous lequel il s’exécute doit disposer des droits d’inscription de l’URI de la `http://localhost:8000/ServiceModelSamples` auprès de la couche HTTP.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="c9dcd-121">Ces droits peuvent être accordés en configurant une [réservation d’espace de noms](/windows/win32/http/namespace-reservations-registrations-and-routing) à l’aide de l' [outil HttpCfg. exe](/windows/win32/http/httpcfg-exe).</span><span class="sxs-lookup"><span data-stu-id="c9dcd-121">Such rights can be granted by setting up a [Namespace Reservation](/windows/win32/http/namespace-reservations-registrations-and-routing) using the [Httpcfg.exe tool](/windows/win32/http/httpcfg-exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9dcd-122">Sur les ordinateurs exécutant Windows Server 2003, l’emprunt d’identité est pris en charge uniquement si l’application Host. exe dispose du privilège d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-122">On computers running Windows Server 2003, impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="c9dcd-123">(Par défaut, seuls les administrateurs ont cette autorisation.) Pour ajouter ce privilège à un compte sous lequel le service s’exécute, accédez à **Outils d’administration**, ouvrez **stratégie de sécurité locale**, ouvrez **stratégies locales**, cliquez sur **attribution des droits utilisateur**, puis sélectionnez **emprunter l’identité d’un client après l’authentification** et double-cliquez sur **Propriétés** pour ajouter un utilisateur ou un groupe.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c9dcd-124">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="c9dcd-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c9dcd-125">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c9dcd-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c9dcd-126">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c9dcd-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c9dcd-127">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c9dcd-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="c9dcd-128">Pour montrer que le service emprunte l'identité de l'appelant, exécutez le client sous un autre compte que celui sous lequel le service s'exécute.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="c9dcd-129">Pour ce faire, à l'invite de commandes tapez :</span><span class="sxs-lookup"><span data-stu-id="c9dcd-129">To do so, at the command prompt, type:</span></span>  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="c9dcd-130">Vous êtes ensuite invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-130">You are then prompted for a password.</span></span> <span data-ttu-id="c9dcd-131">Entrez le mot de passe du compte précédemment spécifié.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-131">Enter the password for the account you previously specified.</span></span>  
  
5. <span data-ttu-id="c9dcd-132">Lorsque vous exécutez le client, notez l'identité avant et après l'avoir exécuté avec des informations d'identification différentes.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
