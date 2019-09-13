---
title: 'Procédure : configurer un port avec un certificat SSL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 6e21311802b0a3ce4e415b14686b101d31f18035
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893314"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="83bf4-102">Procédure : configurer un port avec un certificat SSL</span><span class="sxs-lookup"><span data-stu-id="83bf4-102">How to: Configure a Port with an SSL Certificate</span></span>
<span data-ttu-id="83bf4-103">Lorsque vous créez un service de Windows Communication Foundation (WCF) auto-hébergé <xref:System.ServiceModel.WSHttpBinding> avec la classe qui utilise la sécurité de transport, vous devez également configurer un port avec un certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="83bf4-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="83bf4-104">Si vous ne créez pas de service auto-hébergé, vous pouvez héberger votre service sur les services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="83bf4-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="83bf4-105">Pour plus d’informations, consultez [sécurité du transport http](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="83bf4-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="83bf4-106">Pour configurer un port, l'outil que vous utilisez dépend du système d'exploitation qui s'exécute sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="83bf4-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="83bf4-107">Si vous exécutez [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], utilisez l'outil HttpCfg.exe.</span><span class="sxs-lookup"><span data-stu-id="83bf4-107">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool.</span></span> <span data-ttu-id="83bf4-108">Avec [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], cet outil est installé.</span><span class="sxs-lookup"><span data-stu-id="83bf4-108">With [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] this tool is installed.</span></span> <span data-ttu-id="83bf4-109">Avec [!INCLUDE[wxp](../../../../includes/wxp-md.md)], vous pouvez télécharger l’outil à partir des [outils de support de Windows XP Service Pack 2](https://go.microsoft.com/fwlink/?LinkId=88606).</span><span class="sxs-lookup"><span data-stu-id="83bf4-109">With [!INCLUDE[wxp](../../../../includes/wxp-md.md)], you can download the tool at [Windows XP Service Pack 2 Support Tools](https://go.microsoft.com/fwlink/?LinkId=88606).</span></span> <span data-ttu-id="83bf4-110">Pour plus d’informations, consultez [vue d’ensemble de Httpcfg](https://go.microsoft.com/fwlink/?LinkId=88605).</span><span class="sxs-lookup"><span data-stu-id="83bf4-110">For more information, see [Httpcfg Overview](https://go.microsoft.com/fwlink/?LinkId=88605).</span></span> <span data-ttu-id="83bf4-111">La [documentation](https://go.microsoft.com/fwlink/?LinkId=94840) sur les outils de support de Windows explique la syntaxe de l’outil HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="83bf4-111">The [Windows Support Tools documentation](https://go.microsoft.com/fwlink/?LinkId=94840) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="83bf4-112">Si vous exécutez [!INCLUDE[wv](../../../../includes/wv-md.md)], utilisez l'outil Netsh.exe qui est déjà installé.</span><span class="sxs-lookup"><span data-stu-id="83bf4-112">If you are running [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool that is already installed.</span></span>  
  
 <span data-ttu-id="83bf4-113">Cette rubrique décrit comment exécuter plusieurs procédures :</span><span class="sxs-lookup"><span data-stu-id="83bf4-113">This topic describes how to accomplish several procedures:</span></span>  
  
- <span data-ttu-id="83bf4-114">Détermination de la configuration de port actuelle d'un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="83bf4-114">Determining a computer's current port configuration.</span></span>  
  
- <span data-ttu-id="83bf4-115">Obtention de l'empreinte numérique d'un certificat (nécessaire pour les deux procédures suivantes).</span><span class="sxs-lookup"><span data-stu-id="83bf4-115">Getting a certificate's thumbprint (necessary for the following two procedures).</span></span>  
  
- <span data-ttu-id="83bf4-116">Liaison d’un certificat SSL à une configuration de port.</span><span class="sxs-lookup"><span data-stu-id="83bf4-116">Binding an SSL certificate to a port configuration.</span></span>  
  
- <span data-ttu-id="83bf4-117">Liaison d'un certificat SSL à une configuration de port et prise en charge des certificats clients.</span><span class="sxs-lookup"><span data-stu-id="83bf4-117">Binding an SSL certificate to a port configuration and supporting client certificates.</span></span>  
  
- <span data-ttu-id="83bf4-118">Suppression d’un certificat SSL d’un numéro de port.</span><span class="sxs-lookup"><span data-stu-id="83bf4-118">Deleting an SSL certificate from a port number.</span></span>  
  
 <span data-ttu-id="83bf4-119">Notez que la modification des certificats stockés sur l'ordinateur requiert des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="83bf4-119">Note that modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
### <a name="to-determine-how-ports-are-configured"></a><span data-ttu-id="83bf4-120">Pour déterminer comment sont configurés les ports</span><span class="sxs-lookup"><span data-stu-id="83bf4-120">To determine how ports are configured</span></span>  
  
1. <span data-ttu-id="83bf4-121">Dans [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], utilisez l’outil HttpCfg. exe pour afficher la configuration de port actuelle, à l’aide des commutateurs de **requête** et **SSL** , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="83bf4-121">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="83bf4-122">Dans [!INCLUDE[wv](../../../../includes/wv-md.md)], utilisez l'outil Netsh.exe pour consulter la configuration de port actuelle, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="83bf4-122">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a><span data-ttu-id="83bf4-123">Pour obtenir l'empreinte numérique d'un certificat</span><span class="sxs-lookup"><span data-stu-id="83bf4-123">To get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="83bf4-124">Utilisez le composant logiciel enfichable MMC Certificats pour rechercher un certificat X.509 ayant pour objectif l'authentification du client.</span><span class="sxs-lookup"><span data-stu-id="83bf4-124">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="83bf4-125">Pour plus d'informations, voir [Procédure : Affichez les certificats avec le composant logiciel](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)enfichable MMC.</span><span class="sxs-lookup"><span data-stu-id="83bf4-125">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="83bf4-126">Accédez à l'empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="83bf4-126">Access the certificate's thumbprint.</span></span> <span data-ttu-id="83bf4-127">Pour plus d’informations, consultez [Guide pratique pour Récupérez l’empreinte numérique d'](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)un certificat.</span><span class="sxs-lookup"><span data-stu-id="83bf4-127">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="83bf4-128">Copiez l'empreinte numérique du certificat dans un éditeur de texte, tel que le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="83bf4-128">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="83bf4-129">Supprimez tous les espaces entre les caractères hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="83bf4-129">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="83bf4-130">Pour ce faire, vous pouvez utiliser la fonctionnalité rechercher et remplacer de l’éditeur de texte pour remplacer chaque espace par un caractère Null.</span><span class="sxs-lookup"><span data-stu-id="83bf4-130">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="83bf4-131">Pour lier un certificat SSL à un numéro de port</span><span class="sxs-lookup"><span data-stu-id="83bf4-131">To bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="83bf4-132">Dans [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], utilisez l'outil HttpCfg.exe en mode « défini » dans le magasin SSL (Secure Sockets Layer) pour lier le certificat à un numéro de port.</span><span class="sxs-lookup"><span data-stu-id="83bf4-132">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="83bf4-133">L'outil utilise l'empreinte numérique pour identifier le certificat, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="83bf4-133">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="83bf4-134">Le commutateur **-i** a la syntaxe `IP`suivante :`port` et indique à l’outil de définir le certificat sur le port 8012 de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="83bf4-134">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="83bf4-135">Le cas échéant, les quatre zéros qui précédent le nombre peuvent aussi être remplacés par l'adresse IP réelle de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="83bf4-135">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="83bf4-136">Le commutateur **-h** spécifie l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="83bf4-136">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="83bf4-137">Dans [!INCLUDE[wv](../../../../includes/wv-md.md)], utilisez l'outil Netsh.exe, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="83bf4-137">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - <span data-ttu-id="83bf4-138">Le paramètre **certhash** spécifie l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="83bf4-138">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="83bf4-139">Le paramètre **ipport** spécifie l’adresse IP et le port, et fonctionne comme le commutateur **-i** de l’outil HttpCfg. exe décrit.</span><span class="sxs-lookup"><span data-stu-id="83bf4-139">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="83bf4-140">Le paramètre **AppID** est un GUID qui peut être utilisé pour identifier l’application propriétaire.</span><span class="sxs-lookup"><span data-stu-id="83bf4-140">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="83bf4-141">Pour lier un certificat SSL à un numéro de port et prendre en charge les certificats clients</span><span class="sxs-lookup"><span data-stu-id="83bf4-141">To bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="83bf4-142">Dans [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], pour prendre en charge les clients authentifiés avec les certificats X.509 au niveau de la couche de transport, suivez la procédure précédente mais passez un paramètre de ligne de commande supplémentaire à HttpCfg.exe, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="83bf4-142">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="83bf4-143">Le commutateur **-f** a la syntaxe `n` , où n est un nombre compris entre 1 et 7.</span><span class="sxs-lookup"><span data-stu-id="83bf4-143">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="83bf4-144">Une valeur de 2, comme indiqué dans l'exemple précédent, active des certificats clients au niveau de la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="83bf4-144">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="83bf4-145">La valeur 3 active les certificats clients et mappe ces certificats à un compte Windows.</span><span class="sxs-lookup"><span data-stu-id="83bf4-145">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="83bf4-146">Consultez l'aide de HttpCfg.exe pour connaître le comportement des autres valeurs.</span><span class="sxs-lookup"><span data-stu-id="83bf4-146">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="83bf4-147">Dans [!INCLUDE[wv](../../../../includes/wv-md.md)], pour prendre en charge les clients authentifiés avec les certificats X.509 au niveau de la couche de transport, suivez la procédure précédente mais avec un paramètre supplémentaire, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="83bf4-147">In [!INCLUDE[wv](../../../../includes/wv-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="83bf4-148">Pour supprimer un certificat SSL d’un numéro de port</span><span class="sxs-lookup"><span data-stu-id="83bf4-148">To delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="83bf4-149">Utilisez l’outil HttpCfg.exe ou Netsh.exe pour consulter les ports et les empreintes numériques de toutes les liaisons sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="83bf4-149">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="83bf4-150">Pour imprimer les informations sur le disque, utilisez le caractère de redirection « > », comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="83bf4-150">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="83bf4-151">Dans [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], utilisez l’outil HttpCfg. exe avec les mots clés **Delete** et **SSL** .</span><span class="sxs-lookup"><span data-stu-id="83bf4-151">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="83bf4-152">Utilisez le commutateur **-i** pour spécifier le `IP`nombre`port` : et le commutateur **-h** pour spécifier l’empreinte numérique.</span><span class="sxs-lookup"><span data-stu-id="83bf4-152">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="83bf4-153">Dans [!INCLUDE[wv](../../../../includes/wv-md.md)], utilisez l'outil Netsh.exe, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="83bf4-153">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="83bf4-154">Exemple</span><span class="sxs-lookup"><span data-stu-id="83bf4-154">Example</span></span>  
 <span data-ttu-id="83bf4-155">Le code suivant montre comment créer un service auto-hébergé à l'aide de la classe <xref:System.ServiceModel.WSHttpBinding> à laquelle est attribuée la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="83bf4-155">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="83bf4-156">Lorsque vous créez une application, spécifiez le numéro de port dans l'adresse.</span><span class="sxs-lookup"><span data-stu-id="83bf4-156">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="83bf4-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83bf4-157">See also</span></span>

- [<span data-ttu-id="83bf4-158">Sécurité de transport HTTP</span><span class="sxs-lookup"><span data-stu-id="83bf4-158">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
