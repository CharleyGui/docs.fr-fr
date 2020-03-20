---
title: 'Comment : configurer un port avec un certificat SSL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 90d5424e12bb770dc3da85e1b2738206f4777c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185106"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="8bb15-102">Comment : configurer un port avec un certificat SSL</span><span class="sxs-lookup"><span data-stu-id="8bb15-102">How to: Configure a Port with an SSL Certificate</span></span>

<span data-ttu-id="8bb15-103">Lors de la création d’un service auto-hébergé <xref:System.ServiceModel.WSHttpBinding> Windows Communication Foundation (WCF) avec la classe qui utilise la sécurité des transports, vous devez également configurer un port avec un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="8bb15-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="8bb15-104">Si vous ne créez pas de service auto-hébergé, vous pouvez héberger votre service sur les services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="8bb15-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="8bb15-105">Pour plus d’informations, voir [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="8bb15-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="8bb15-106">Pour configurer un port, l'outil que vous utilisez dépend du système d'exploitation qui s'exécute sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8bb15-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="8bb15-107">Si vous exécutez Windows Server 2003, utilisez l’outil HttpCfg.exe.</span><span class="sxs-lookup"><span data-stu-id="8bb15-107">If you are running Windows Server 2003, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="8bb15-108">Sur Windows Server 2003, cet outil est installé.</span><span class="sxs-lookup"><span data-stu-id="8bb15-108">On Windows Server 2003, this tool is installed.</span></span> <span data-ttu-id="8bb15-109">Pour plus d’informations, voir [Httpcfg Aperçu](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="8bb15-109">For more information, see [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="8bb15-110">La [documentation Windows Support Tools](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explique la syntaxe de l’outil Httpcfg.exe.</span><span class="sxs-lookup"><span data-stu-id="8bb15-110">The [Windows Support Tools documentation](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="8bb15-111">Si vous exécutez Windows Vista, utilisez l’outil Netsh.exe qui est déjà installé.</span><span class="sxs-lookup"><span data-stu-id="8bb15-111">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8bb15-112">La modification des certificats stockés sur l’ordinateur nécessite des privilèges administratifs.</span><span class="sxs-lookup"><span data-stu-id="8bb15-112">Modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
## <a name="determine-how-ports-are-configured"></a><span data-ttu-id="8bb15-113">Déterminer comment les ports sont configurés</span><span class="sxs-lookup"><span data-stu-id="8bb15-113">Determine how ports are configured</span></span>  
  
1. <span data-ttu-id="8bb15-114">Dans Windows Server 2003 ou Windows XP, utilisez l’outil HttpCfg.exe pour afficher la configuration portuaire actuelle, en utilisant les commutateurs de **requête** et **de ssl,** comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8bb15-114">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="8bb15-115">Dans Windows Vista, utilisez l’outil Netsh.exe pour afficher la configuration portuaire actuelle, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8bb15-115">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a><span data-ttu-id="8bb15-116">Obtenir l’empreinte du pouce d’un certificat</span><span class="sxs-lookup"><span data-stu-id="8bb15-116">Get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="8bb15-117">Utilisez le composant logiciel enfichable MMC Certificats pour rechercher un certificat X.509 ayant pour objectif l'authentification du client.</span><span class="sxs-lookup"><span data-stu-id="8bb15-117">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="8bb15-118">Pour plus d’informations, consultez la page [Affichage de certificats à l’aide du composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="8bb15-118">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="8bb15-119">Accédez à l'empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="8bb15-119">Access the certificate's thumbprint.</span></span> <span data-ttu-id="8bb15-120">Pour plus d’informations, consultez l’article [Comment : récupérer l’empreinte numérique d’un certificat](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="8bb15-120">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="8bb15-121">Copiez l'empreinte numérique du certificat dans un éditeur de texte, tel que le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="8bb15-121">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="8bb15-122">Supprimez tous les espaces entre les caractères hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="8bb15-122">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="8bb15-123">Pour ce faire, vous pouvez utiliser la fonctionnalité rechercher et remplacer de l’éditeur de texte pour remplacer chaque espace par un caractère Null.</span><span class="sxs-lookup"><span data-stu-id="8bb15-123">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="8bb15-124">Lier un certificat SSL à un numéro de port</span><span class="sxs-lookup"><span data-stu-id="8bb15-124">Bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="8bb15-125">Dans Windows Server 2003 ou Windows XP, utilisez l’outil HttpCfg.exe en mode «set» sur le magasin Secure Sockets Layer (SSL) pour lier le certificat à un numéro de port.</span><span class="sxs-lookup"><span data-stu-id="8bb15-125">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="8bb15-126">L'outil utilise l'empreinte numérique pour identifier le certificat, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8bb15-126">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="8bb15-127">Le **commutateur -i** a `IP`la`port` syntaxe de : et instruit l’outil pour définir le certificat au port 8012 de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8bb15-127">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="8bb15-128">Le cas échéant, les quatre zéros qui précédent le nombre peuvent aussi être remplacés par l'adresse IP réelle de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8bb15-128">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="8bb15-129">L’interrupteur **-h** spécifie l’empreinte du certificat.</span><span class="sxs-lookup"><span data-stu-id="8bb15-129">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="8bb15-130">Dans Windows Vista, utilisez l’outil Netsh.exe, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8bb15-130">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - <span data-ttu-id="8bb15-131">Le **paramètre certhash** spécifie l’empreinte du certificat.</span><span class="sxs-lookup"><span data-stu-id="8bb15-131">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="8bb15-132">Le **paramètre ipport** spécifie l’adresse IP et le port, et fonctionne tout comme le commutateur **-i** de l’outil Httpcfg.exe décrit.</span><span class="sxs-lookup"><span data-stu-id="8bb15-132">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="8bb15-133">Le **paramètre appid** est un GUID qui peut être utilisé pour identifier l’application propriétaire.</span><span class="sxs-lookup"><span data-stu-id="8bb15-133">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="8bb15-134">Lier un certificat SSL à un numéro de port et prendre en charge les certificats de clients</span><span class="sxs-lookup"><span data-stu-id="8bb15-134">Bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="8bb15-135">Dans Windows Server 2003 ou Windows XP, pour prendre en charge les clients qui s’authentifient avec des certificats X.509 à la couche de transport, suivez la procédure précédente, mais passez un paramètre de ligne de commande supplémentaire à HttpCfg.exe, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8bb15-135">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="8bb15-136">Le **commutateur -f** a `n` la syntaxe de l’endroit où n est un nombre entre 1 et 7.</span><span class="sxs-lookup"><span data-stu-id="8bb15-136">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="8bb15-137">Une valeur de 2, comme indiqué dans l'exemple précédent, active des certificats clients au niveau de la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="8bb15-137">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="8bb15-138">La valeur 3 active les certificats clients et mappe ces certificats à un compte Windows.</span><span class="sxs-lookup"><span data-stu-id="8bb15-138">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="8bb15-139">Consultez l'aide de HttpCfg.exe pour connaître le comportement des autres valeurs.</span><span class="sxs-lookup"><span data-stu-id="8bb15-139">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="8bb15-140">Dans Windows Vista, pour prendre en charge les clients qui s’authentifient avec des certificats X.509 à la couche de transport, suivez la procédure précédente, mais avec un paramètre supplémentaire, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8bb15-140">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="8bb15-141">Supprimer un certificat SSL à partir d’un numéro de port</span><span class="sxs-lookup"><span data-stu-id="8bb15-141">Delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="8bb15-142">Utilisez l’outil HttpCfg.exe ou Netsh.exe pour consulter les ports et les empreintes numériques de toutes les liaisons sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8bb15-142">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="8bb15-143">Pour imprimer l’information sur disque, utilisez le caractère de redirection «>», comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8bb15-143">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="8bb15-144">Dans Windows Server 2003 ou Windows XP, utilisez l’outil HttpCfg.exe avec les mots clés **supprimer** et **ssl.**</span><span class="sxs-lookup"><span data-stu-id="8bb15-144">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="8bb15-145">Utilisez le **commutateur -i** pour spécifier le `IP``port` : numéro, et le commutateur **-h** pour spécifier l’empreinte du pouce.</span><span class="sxs-lookup"><span data-stu-id="8bb15-145">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="8bb15-146">Dans Windows Vista, utilisez l’outil Netsh.exe, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8bb15-146">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="8bb15-147"> Exemple</span><span class="sxs-lookup"><span data-stu-id="8bb15-147">Example</span></span>  

 <span data-ttu-id="8bb15-148">Le code suivant montre comment créer un service auto-hébergé à l'aide de la classe <xref:System.ServiceModel.WSHttpBinding> à laquelle est attribuée la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="8bb15-148">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="8bb15-149">Lorsque vous créez une application, spécifiez le numéro de port dans l'adresse.</span><span class="sxs-lookup"><span data-stu-id="8bb15-149">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8bb15-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8bb15-150">See also</span></span>

- [<span data-ttu-id="8bb15-151">Sécurité de transport HTTP</span><span class="sxs-lookup"><span data-stu-id="8bb15-151">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
