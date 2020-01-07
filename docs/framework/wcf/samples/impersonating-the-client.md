---
title: Emprunt de l'identité du client
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 0c262d8b5460f236ef0429154ae337c7adf96714
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338715"
---
# <a name="impersonating-the-client"></a>Emprunt de l'identité du client
Cet exemple montre comment emprunter l'identité de l'application de l'appelant au niveau du service afin que ce dernier puisse accéder aux ressources système pour le compte de l'appelant.  
  
 Cet exemple est basé sur l’exemple d' [auto-hébergement](../../../../docs/framework/wcf/samples/self-host.md) . Les fichiers de configuration du service et du client sont les mêmes que ceux de l’exemple [auto-hôte](../../../../docs/framework/wcf/samples/self-host.md) .  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le code de service a été modifié afin que la méthode `Add` sur le service emprunte l'identité de l'appelant à l'aide de <xref:System.ServiceModel.OperationBehaviorAttribute>, tel qu'indiqué dans l'exemple de code suivant.  
  
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
  
 En conséquence, le contexte de sécurité du thread en cours d'exécution est basculé pour emprunter l'identité de l'appelant avant d'entrer dans la méthode `Add` et est rétabli lorsqu'il quitte la méthode.  
  
 La méthode `DisplayIdentityInformation` indiquée dans l'exemple de code suivant est une fonction utilitaire qui affiche l'identité de l'appelant.  
  
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
  
 La méthode `Subtract` sur le service emprunte l'identité de l'appelant à l'aide d'appels impératifs, tel qu'indiqué dans l'exemple de code suivant.  
  
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
  
 Notez que dans ce cas, l'identité de l'appelant n'est pas empruntée pour l'ensemble de l'appel, mais uniquement pour une partie de celui-ci. En général, l'emprunt d'identité pour la plus petite étendue est préférable à l'emprunt d'identité pour l'ensemble de l'opération.  
  
 Les autres méthodes n'empruntent pas l'identité de l'appelant.  
  
 Le code client a été modifié pour affecter <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> au niveau d'emprunt d'identité. Le client spécifie le niveau d'emprunt d'identité à utiliser par le service, en utilisant l'énumération <xref:System.Security.Principal.TokenImpersonationLevel>. L'énumération prend en charge les valeurs suivantes : <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> et <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Pour effectuer un contrôle lors de l'accès à une ressource système sur l'ordinateur local protégé à l'aide des listes de contrôle d'accès Windows, le niveau d'emprunt d'identité doit avoir la valeur <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, tel qu'indiqué dans l'exemple de code suivant.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Lorsque vous exécutez l'exemple, les requêtes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.  
  
> [!NOTE]
> Le service doit s’exécuter sous un compte d’administration ou le compte sous lequel il s’exécute doit disposer des droits d’inscription de l’URI de la `http://localhost:8000/ServiceModelSamples` auprès de la couche HTTP. Ces droits peuvent être accordés en configurant une [réservation d’espace de noms](https://go.microsoft.com/fwlink/?LinkId=95012) à l’aide de l' [outil HttpCfg. exe](https://go.microsoft.com/fwlink/?LinkId=95010).  
  
> [!NOTE]
> Sur les ordinateurs exécutant Windows Server 2003, l’emprunt d’identité est pris en charge uniquement si l’application Host. exe dispose du privilège d’emprunt d’identité. (Par défaut, seuls les administrateurs ont cette autorisation.) Pour ajouter ce privilège à un compte sous lequel le service s’exécute, accédez à **Outils d’administration**, ouvrez **stratégie de sécurité locale**, ouvrez **stratégies locales**, cliquez sur **attribution des droits utilisateur**, puis sélectionnez **emprunter l’identité d’un client après l’authentification** et double-cliquez sur **Propriétés** pour ajouter un utilisateur ou un groupe.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4. Pour montrer que le service emprunte l'identité de l'appelant, exécutez le client sous un autre compte que celui sous lequel le service s'exécute. Pour ce faire, à l'invite de commandes tapez :  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Vous êtes ensuite invité à entrer un mot de passe. Entrez le mot de passe du compte précédemment spécifié.  
  
5. Lorsque vous exécutez le client, notez l'identité avant et après l'avoir exécuté avec des informations d'identification différentes.  
