---
title: 'Comment : rendre des certificats X.509 accessibles à WCF'
description: Découvrez comment rendre un certificat X. 509 accessible à WCF. Le code d’application doit spécifier le nom et l’emplacement du magasin de certificats. Il peut y avoir d’autres exigences.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 5cc1118640bcf1262d88cb8cdb39939ae315cae3
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246868"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="f6e85-105">Comment : rendre des certificats X.509 accessibles à WCF</span><span class="sxs-lookup"><span data-stu-id="f6e85-105">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="f6e85-106">Pour rendre un certificat X. 509 accessible à Windows Communication Foundation (WCF), le code d’application doit spécifier le nom et l’emplacement du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="f6e85-106">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="f6e85-107">Dans certains cas, l'identité du processus doit avoir accès au fichier contenant la clé privée associée au certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="f6e85-107">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="f6e85-108">Pour obtenir la clé privée associée à un certificat X. 509 dans un magasin de certificats, WCF doit avoir l’autorisation de le faire.</span><span class="sxs-lookup"><span data-stu-id="f6e85-108">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="f6e85-109">Par défaut, seuls le propriétaire et le compte système peuvent accéder à la clé privée d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="f6e85-109">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="f6e85-110">Pour rendre des certificats X.509 accessibles à WCF</span><span class="sxs-lookup"><span data-stu-id="f6e85-110">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="f6e85-111">Donnez au compte sous lequel WCF exécute l’accès en lecture au fichier contenant la clé privée associée au certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="f6e85-111">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="f6e85-112">Déterminez si WCF requiert un accès en lecture à la clé privée pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="f6e85-112">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="f6e85-113">Le tableau suivant précise si une clé privée doit être disponible lors de l'utilisation d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="f6e85-113">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="f6e85-114">Utilisation d'un certificat X.509</span><span class="sxs-lookup"><span data-stu-id="f6e85-114">X.509 certificate use</span></span>|<span data-ttu-id="f6e85-115">Clé privée</span><span class="sxs-lookup"><span data-stu-id="f6e85-115">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="f6e85-116">Signature numérique d'un message SOAP sortant.</span><span class="sxs-lookup"><span data-stu-id="f6e85-116">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="f6e85-117">Oui</span><span class="sxs-lookup"><span data-stu-id="f6e85-117">Yes</span></span>|  
        |<span data-ttu-id="f6e85-118">Vérification de la signature d'un message SOAP entrant.</span><span class="sxs-lookup"><span data-stu-id="f6e85-118">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="f6e85-119">Non</span><span class="sxs-lookup"><span data-stu-id="f6e85-119">No</span></span>|  
        |<span data-ttu-id="f6e85-120">Chiffrement d'un message SOAP sortant.</span><span class="sxs-lookup"><span data-stu-id="f6e85-120">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="f6e85-121">Non</span><span class="sxs-lookup"><span data-stu-id="f6e85-121">No</span></span>|  
        |<span data-ttu-id="f6e85-122">Déchiffrement d'un message SOAP entrant.</span><span class="sxs-lookup"><span data-stu-id="f6e85-122">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="f6e85-123">Oui</span><span class="sxs-lookup"><span data-stu-id="f6e85-123">Yes</span></span>|  
  
    2. <span data-ttu-id="f6e85-124">Déterminez l'emplacement et le nom du magasin de certificats dans lequel le certificat est stocké.</span><span class="sxs-lookup"><span data-stu-id="f6e85-124">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="f6e85-125">Le magasin de certificats dans lequel le certificat est stocké est spécifié dans le code d'application ou dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="f6e85-125">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="f6e85-126">Ainsi, l'exemple suivant spécifie que le certificat se trouve dans le magasin de certificats `CurrentUser` nommé `My`.</span><span class="sxs-lookup"><span data-stu-id="f6e85-126">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="f6e85-127">Déterminez où se trouve la clé privée du certificat sur l’ordinateur à l’aide de l’outil [FindPrivateKey](../samples/findprivatekey.md) .</span><span class="sxs-lookup"><span data-stu-id="f6e85-127">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="f6e85-128">L’outil [FindPrivateKey](../samples/findprivatekey.md) requiert le nom du magasin de certificats, l’emplacement du magasin de certificats et un nom qui identifie de façon unique le certificat.</span><span class="sxs-lookup"><span data-stu-id="f6e85-128">The [FindPrivateKey](../samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="f6e85-129">Il accepte le nom de sujet du certificat ou son empreinte numérique comme identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="f6e85-129">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="f6e85-130">Pour plus d’informations sur la façon de déterminer l’empreinte numérique d’un certificat, consultez [Comment : récupérer l’empreinte numérique d’un certificat](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="f6e85-130">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="f6e85-131">L’exemple de code suivant utilise l’outil [FindPrivateKey](../samples/findprivatekey.md) pour déterminer l’emplacement de la clé privée pour un certificat dans le `My` magasin dans `CurrentUser` avec une empreinte numérique `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d` .</span><span class="sxs-lookup"><span data-stu-id="f6e85-131">The following code example uses the [FindPrivateKey](../samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="f6e85-132">Déterminez le compte sous lequel WCF s’exécute.</span><span class="sxs-lookup"><span data-stu-id="f6e85-132">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="f6e85-133">Le tableau suivant détaille le compte sous lequel WCF s’exécute pour un scénario donné.</span><span class="sxs-lookup"><span data-stu-id="f6e85-133">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="f6e85-134">Scénario</span><span class="sxs-lookup"><span data-stu-id="f6e85-134">Scenario</span></span>|<span data-ttu-id="f6e85-135">Identité du processus</span><span class="sxs-lookup"><span data-stu-id="f6e85-135">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="f6e85-136">Client (console ou application WinForms).</span><span class="sxs-lookup"><span data-stu-id="f6e85-136">Client (console or WinForms application).</span></span>|<span data-ttu-id="f6e85-137">Utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="f6e85-137">Currently logged in user.</span></span>|  
        |<span data-ttu-id="f6e85-138">Service auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="f6e85-138">Service that is self-hosted.</span></span>|<span data-ttu-id="f6e85-139">Utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="f6e85-139">Currently logged in user.</span></span>|  
        |<span data-ttu-id="f6e85-140">Service hébergé dans IIS 6,0 (Windows Server 2003) ou IIS 7,0 (Windows Vista).</span><span class="sxs-lookup"><span data-stu-id="f6e85-140">Service that is hosted in IIS 6.0 (Windows Server 2003) or IIS 7.0 (Windows Vista).</span></span>|<span data-ttu-id="f6e85-141">SERVICE RÉSEAU</span><span class="sxs-lookup"><span data-stu-id="f6e85-141">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="f6e85-142">Service hébergé dans IIS 5. X (Windows XP).</span><span class="sxs-lookup"><span data-stu-id="f6e85-142">Service that is hosted in IIS 5.X (Windows XP).</span></span>|<span data-ttu-id="f6e85-143">Contrôlé par l'élément `<processModel>` dans le fichier Machine.config.</span><span class="sxs-lookup"><span data-stu-id="f6e85-143">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="f6e85-144">Le compte par défaut est ASPNET.</span><span class="sxs-lookup"><span data-stu-id="f6e85-144">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="f6e85-145">Accordez l’accès en lecture au fichier contenant la clé privée pour le compte sous lequel WCF s’exécute, à l’aide d’un outil tel que icacls.exe.</span><span class="sxs-lookup"><span data-stu-id="f6e85-145">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="f6e85-146">L’exemple de code suivant modifie la liste de contrôle d’accès discrétionnaire (DACL, Discretionary Access Control List) du fichier spécifié pour accorder au compte de SERVICE réseau l’accès en lecture ( : R) au fichier.</span><span class="sxs-lookup"><span data-stu-id="f6e85-146">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="f6e85-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6e85-147">See also</span></span>

- [<span data-ttu-id="f6e85-148">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="f6e85-148">FindPrivateKey</span></span>](../samples/findprivatekey.md)
- [<span data-ttu-id="f6e85-149">Comment : récupérer l'empreinte numérique d'un certificat</span><span class="sxs-lookup"><span data-stu-id="f6e85-149">How to: Retrieve the Thumbprint of a Certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="f6e85-150">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="f6e85-150">Working with Certificates</span></span>](working-with-certificates.md)
