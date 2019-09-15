---
title: 'Procédure : rendre des certificats X.509 accessibles à WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 401371bf01a62a20f2834cb76df19d9ddaacf83d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972352"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="b1768-102">Procédure : rendre des certificats X.509 accessibles à WCF</span><span class="sxs-lookup"><span data-stu-id="b1768-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="b1768-103">Pour rendre un certificat X. 509 accessible à Windows Communication Foundation (WCF), le code d’application doit spécifier le nom et l’emplacement du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="b1768-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="b1768-104">Dans certains cas, l'identité du processus doit avoir accès au fichier contenant la clé privée associée au certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="b1768-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="b1768-105">Pour obtenir la clé privée associée à un certificat X. 509 dans un magasin de certificats, WCF doit avoir l’autorisation de le faire.</span><span class="sxs-lookup"><span data-stu-id="b1768-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="b1768-106">Par défaut, seuls le propriétaire et le compte système peuvent accéder à la clé privée d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="b1768-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="b1768-107">Pour rendre des certificats X.509 accessibles à WCF</span><span class="sxs-lookup"><span data-stu-id="b1768-107">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="b1768-108">Donnez au compte sous lequel WCF exécute l’accès en lecture au fichier contenant la clé privée associée au certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="b1768-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="b1768-109">Déterminez si WCF requiert un accès en lecture à la clé privée pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="b1768-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="b1768-110">Le tableau suivant précise si une clé privée doit être disponible lors de l'utilisation d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="b1768-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="b1768-111">Utilisation d'un certificat X.509</span><span class="sxs-lookup"><span data-stu-id="b1768-111">X.509 certificate use</span></span>|<span data-ttu-id="b1768-112">Clé privée</span><span class="sxs-lookup"><span data-stu-id="b1768-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="b1768-113">Signature numérique d'un message SOAP sortant.</span><span class="sxs-lookup"><span data-stu-id="b1768-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="b1768-114">Oui</span><span class="sxs-lookup"><span data-stu-id="b1768-114">Yes</span></span>|  
        |<span data-ttu-id="b1768-115">Vérification de la signature d'un message SOAP entrant.</span><span class="sxs-lookup"><span data-stu-id="b1768-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="b1768-116">Non</span><span class="sxs-lookup"><span data-stu-id="b1768-116">No</span></span>|  
        |<span data-ttu-id="b1768-117">Chiffrement d'un message SOAP sortant.</span><span class="sxs-lookup"><span data-stu-id="b1768-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="b1768-118">Non</span><span class="sxs-lookup"><span data-stu-id="b1768-118">No</span></span>|  
        |<span data-ttu-id="b1768-119">Déchiffrement d'un message SOAP entrant.</span><span class="sxs-lookup"><span data-stu-id="b1768-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="b1768-120">Oui</span><span class="sxs-lookup"><span data-stu-id="b1768-120">Yes</span></span>|  
  
    2. <span data-ttu-id="b1768-121">Déterminez l'emplacement et le nom du magasin de certificats dans lequel le certificat est stocké.</span><span class="sxs-lookup"><span data-stu-id="b1768-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="b1768-122">Le magasin de certificats dans lequel le certificat est stocké est spécifié dans le code d'application ou dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="b1768-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="b1768-123">Ainsi, l'exemple suivant spécifie que le certificat se trouve dans le magasin de certificats `CurrentUser` nommé `My`.</span><span class="sxs-lookup"><span data-stu-id="b1768-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="b1768-124">Déterminez où se trouve la clé privée du certificat sur l’ordinateur à l’aide de l’outil [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) .</span><span class="sxs-lookup"><span data-stu-id="b1768-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="b1768-125">L’outil [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) requiert le nom du magasin de certificats, l’emplacement du magasin de certificats et un nom qui identifie de façon unique le certificat.</span><span class="sxs-lookup"><span data-stu-id="b1768-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="b1768-126">Il accepte le nom de sujet du certificat ou son empreinte numérique comme identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="b1768-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="b1768-127">Pour plus d’informations sur la façon de déterminer l’empreinte numérique d’un [certificat, consultez Procédure : Récupérez l’empreinte numérique d'](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)un certificat.</span><span class="sxs-lookup"><span data-stu-id="b1768-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="b1768-128">L’exemple de code suivant utilise l’outil [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) pour déterminer l’emplacement de la clé privée pour un certificat dans `My` le magasin `CurrentUser` dans avec une empreinte `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`numérique.</span><span class="sxs-lookup"><span data-stu-id="b1768-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="b1768-129">Déterminez le compte sous lequel WCF s’exécute.</span><span class="sxs-lookup"><span data-stu-id="b1768-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="b1768-130">Le tableau suivant détaille le compte sous lequel WCF s’exécute pour un scénario donné.</span><span class="sxs-lookup"><span data-stu-id="b1768-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="b1768-131">Scénario</span><span class="sxs-lookup"><span data-stu-id="b1768-131">Scenario</span></span>|<span data-ttu-id="b1768-132">Identité du processus</span><span class="sxs-lookup"><span data-stu-id="b1768-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="b1768-133">Client (console ou application WinForms).</span><span class="sxs-lookup"><span data-stu-id="b1768-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="b1768-134">Utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="b1768-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="b1768-135">Service auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="b1768-135">Service that is self-hosted.</span></span>|<span data-ttu-id="b1768-136">Utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="b1768-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="b1768-137">Service hébergé dans IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) ou IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="b1768-137">Service that is hosted in IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) or IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span></span>|<span data-ttu-id="b1768-138">SERVICE RÉSEAU</span><span class="sxs-lookup"><span data-stu-id="b1768-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="b1768-139">Service hébergé dans IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="b1768-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="b1768-140">Contrôlé par l'élément `<processModel>` dans le fichier Machine.config.</span><span class="sxs-lookup"><span data-stu-id="b1768-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="b1768-141">Le compte par défaut est ASPNET.</span><span class="sxs-lookup"><span data-stu-id="b1768-141">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="b1768-142">Accordez l’accès en lecture au fichier contenant la clé privée pour le compte sous lequel WCF s’exécute, à l’aide d’un outil tel que icacls. exe.</span><span class="sxs-lookup"><span data-stu-id="b1768-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="b1768-143">L’exemple de code suivant modifie la liste de contrôle d’accès discrétionnaire (DACL, Discretionary Access Control List) du fichier spécifié pour accorder au compte de SERVICE réseau l’accès en lecture ( : R) au fichier.</span><span class="sxs-lookup"><span data-stu-id="b1768-143">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console 
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="b1768-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1768-144">See also</span></span>

- [<span data-ttu-id="b1768-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="b1768-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [<span data-ttu-id="b1768-146">Guide pratique pour Récupérer l’empreinte numérique d’un certificat</span><span class="sxs-lookup"><span data-stu-id="b1768-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="b1768-147">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="b1768-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
