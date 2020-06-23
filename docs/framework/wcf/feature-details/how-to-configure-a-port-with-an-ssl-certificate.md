---
title: 'Comment : configurer un port avec un certificat SSL'
description: Découvrez comment configurer un port avec un certificat X. 509, requis pour un service WCF auto-hébergé avec la classe WSHttpBinding à l’aide de la sécurité de transport.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 0eccdf916dae7b886cbc4e6563e6dfe17039c321
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247180"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="340c5-103">Comment : configurer un port avec un certificat SSL</span><span class="sxs-lookup"><span data-stu-id="340c5-103">How to: Configure a Port with an SSL Certificate</span></span>

<span data-ttu-id="340c5-104">Lorsque vous créez un service de Windows Communication Foundation (WCF) auto-hébergé avec la <xref:System.ServiceModel.WSHttpBinding> classe qui utilise la sécurité de transport, vous devez également configurer un port avec un certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="340c5-104">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="340c5-105">Si vous ne créez pas de service auto-hébergé, vous pouvez héberger votre service sur les services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="340c5-105">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="340c5-106">Pour plus d’informations, consultez [sécurité du transport http](http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="340c5-106">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
 <span data-ttu-id="340c5-107">Pour configurer un port, l'outil que vous utilisez dépend du système d'exploitation qui s'exécute sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="340c5-107">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="340c5-108">Si vous exécutez Windows Server 2003, utilisez l’outil HttpCfg.exe.</span><span class="sxs-lookup"><span data-stu-id="340c5-108">If you are running Windows Server 2003, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="340c5-109">Sur Windows Server 2003, cet outil est installé.</span><span class="sxs-lookup"><span data-stu-id="340c5-109">On Windows Server 2003, this tool is installed.</span></span> <span data-ttu-id="340c5-110">Pour plus d’informations, consultez [vue d’ensemble de Httpcfg](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="340c5-110">For more information, see [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="340c5-111">La [documentation](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) sur les outils de support de Windows explique la syntaxe de l’outil Httpcfg.exe.</span><span class="sxs-lookup"><span data-stu-id="340c5-111">The [Windows Support Tools documentation](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="340c5-112">Si vous exécutez Windows Vista, utilisez l’outil Netsh.exe qui est déjà installé.</span><span class="sxs-lookup"><span data-stu-id="340c5-112">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="340c5-113">La modification des certificats stockés sur l’ordinateur requiert des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="340c5-113">Modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
## <a name="determine-how-ports-are-configured"></a><span data-ttu-id="340c5-114">Déterminer le mode de configuration des ports</span><span class="sxs-lookup"><span data-stu-id="340c5-114">Determine how ports are configured</span></span>  
  
1. <span data-ttu-id="340c5-115">Dans Windows Server 2003 ou Windows XP, utilisez l’outil HttpCfg.exe pour afficher la configuration de port actuelle, à l’aide des commutateurs de **requête** et **SSL** , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="340c5-115">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="340c5-116">Dans Windows Vista, utilisez l’outil Netsh.exe pour afficher la configuration de port actuelle, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="340c5-116">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a><span data-ttu-id="340c5-117">Obtenir l’empreinte numérique d’un certificat</span><span class="sxs-lookup"><span data-stu-id="340c5-117">Get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="340c5-118">Utilisez le composant logiciel enfichable MMC Certificats pour rechercher un certificat X.509 ayant pour objectif l'authentification du client.</span><span class="sxs-lookup"><span data-stu-id="340c5-118">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="340c5-119">Pour plus d’informations, consultez la page [Affichage de certificats à l’aide du composant logiciel enfichable MMC](how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="340c5-119">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="340c5-120">Accédez à l'empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="340c5-120">Access the certificate's thumbprint.</span></span> <span data-ttu-id="340c5-121">Pour plus d’informations, consultez l’article [Comment : récupérer l’empreinte numérique d’un certificat](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="340c5-121">For more information, see [How to: Retrieve the Thumbprint of a Certificate](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="340c5-122">Copiez l'empreinte numérique du certificat dans un éditeur de texte, tel que le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="340c5-122">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="340c5-123">Supprimez tous les espaces entre les caractères hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="340c5-123">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="340c5-124">Pour ce faire, vous pouvez utiliser la fonctionnalité rechercher et remplacer de l’éditeur de texte pour remplacer chaque espace par un caractère Null.</span><span class="sxs-lookup"><span data-stu-id="340c5-124">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="340c5-125">Lier un certificat SSL à un numéro de port</span><span class="sxs-lookup"><span data-stu-id="340c5-125">Bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="340c5-126">Dans Windows Server 2003 ou Windows XP, utilisez l’outil HttpCfg.exe en mode « set » sur le magasin protocole SSL (SSL) pour lier le certificat à un numéro de port.</span><span class="sxs-lookup"><span data-stu-id="340c5-126">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="340c5-127">L'outil utilise l'empreinte numérique pour identifier le certificat, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="340c5-127">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="340c5-128">Le commutateur **-i** a la syntaxe `IP` suivante : `port` et indique à l’outil de définir le certificat sur le port 8012 de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="340c5-128">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="340c5-129">Le cas échéant, les quatre zéros qui précédent le nombre peuvent aussi être remplacés par l'adresse IP réelle de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="340c5-129">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="340c5-130">Le commutateur **-h** spécifie l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="340c5-130">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="340c5-131">Dans Windows Vista, utilisez l’outil Netsh.exe, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="340c5-131">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - <span data-ttu-id="340c5-132">Le paramètre **certhash** spécifie l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="340c5-132">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="340c5-133">Le paramètre **ipport** spécifie l’adresse IP et le port, et fonctionne de la même façon que le commutateur **-i** de l’outil Httpcfg.exe décrit.</span><span class="sxs-lookup"><span data-stu-id="340c5-133">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="340c5-134">Le paramètre **AppID** est un GUID qui peut être utilisé pour identifier l’application propriétaire.</span><span class="sxs-lookup"><span data-stu-id="340c5-134">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="340c5-135">Lier un certificat SSL à un numéro de port et prendre en charge les certificats clients</span><span class="sxs-lookup"><span data-stu-id="340c5-135">Bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="340c5-136">Dans Windows Server 2003 ou Windows XP, pour prendre en charge les clients qui s’authentifient avec des certificats X. 509 au niveau de la couche de transport, suivez la procédure précédente, mais transmettez un paramètre de ligne de commande supplémentaire à HttpCfg.exe, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="340c5-136">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="340c5-137">Le commutateur **-f** a la syntaxe, `n` où n est un nombre compris entre 1 et 7.</span><span class="sxs-lookup"><span data-stu-id="340c5-137">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="340c5-138">Une valeur de 2, comme indiqué dans l'exemple précédent, active des certificats clients au niveau de la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="340c5-138">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="340c5-139">La valeur 3 active les certificats clients et mappe ces certificats à un compte Windows.</span><span class="sxs-lookup"><span data-stu-id="340c5-139">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="340c5-140">Consultez l'aide de HttpCfg.exe pour connaître le comportement des autres valeurs.</span><span class="sxs-lookup"><span data-stu-id="340c5-140">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="340c5-141">Dans Windows Vista, pour prendre en charge les clients qui s’authentifient avec des certificats X. 509 au niveau de la couche de transport, suivez la procédure précédente, mais avec un paramètre supplémentaire, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="340c5-141">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="340c5-142">Supprimer un certificat SSL d’un numéro de port</span><span class="sxs-lookup"><span data-stu-id="340c5-142">Delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="340c5-143">Utilisez l’outil HttpCfg.exe ou Netsh.exe pour consulter les ports et les empreintes numériques de toutes les liaisons sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="340c5-143">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="340c5-144">Pour imprimer les informations sur le disque, utilisez le caractère de redirection « > », comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="340c5-144">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="340c5-145">Dans Windows Server 2003 ou Windows XP, utilisez l’outil HttpCfg.exe avec les mots clés **Delete** et **SSL** .</span><span class="sxs-lookup"><span data-stu-id="340c5-145">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="340c5-146">Utilisez le commutateur **-i** pour spécifier le `IP` `port` nombre : et le commutateur **-h** pour spécifier l’empreinte numérique.</span><span class="sxs-lookup"><span data-stu-id="340c5-146">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="340c5-147">Dans Windows Vista, utilisez l’outil Netsh.exe, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="340c5-147">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="340c5-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="340c5-148">Example</span></span>  

 <span data-ttu-id="340c5-149">Le code suivant montre comment créer un service auto-hébergé à l'aide de la classe <xref:System.ServiceModel.WSHttpBinding> à laquelle est attribuée la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="340c5-149">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="340c5-150">Lorsque vous créez une application, spécifiez le numéro de port dans l'adresse.</span><span class="sxs-lookup"><span data-stu-id="340c5-150">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="340c5-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="340c5-151">See also</span></span>

- [<span data-ttu-id="340c5-152">Sécurité de transport HTTP</span><span class="sxs-lookup"><span data-stu-id="340c5-152">HTTP Transport Security</span></span>](http-transport-security.md)
