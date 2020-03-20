---
title: 'Comment : rendre des certificats X.509 accessibles à WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 14f2242ab55795c74fa169382fef846bc0e60ace
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184893"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="bb4b2-102">Comment : rendre des certificats X.509 accessibles à WCF</span><span class="sxs-lookup"><span data-stu-id="bb4b2-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="bb4b2-103">Pour rendre un certificat X.509 accessible à la Windows Communication Foundation (WCF), le code de demande doit spécifier le nom et l’emplacement du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="bb4b2-104">Dans certains cas, l'identité du processus doit avoir accès au fichier contenant la clé privée associée au certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="bb4b2-105">Pour obtenir la clé privée associée à un certificat X.509 dans un magasin de certificats, WCF doit avoir la permission de le faire.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="bb4b2-106">Par défaut, seuls le propriétaire et le compte système peuvent accéder à la clé privée d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="bb4b2-107">Pour rendre des certificats X.509 accessibles à WCF</span><span class="sxs-lookup"><span data-stu-id="bb4b2-107">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="bb4b2-108">Donnez au compte en vertu duquel WCF est en cours d’exécution l’accès lu au fichier qui contient la clé privée associée au certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="bb4b2-109">Déterminer si WCF exige l’accès à la clé privée pour le certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="bb4b2-110">Le tableau suivant précise si une clé privée doit être disponible lors de l'utilisation d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="bb4b2-111">Utilisation d'un certificat X.509</span><span class="sxs-lookup"><span data-stu-id="bb4b2-111">X.509 certificate use</span></span>|<span data-ttu-id="bb4b2-112">Clé privée</span><span class="sxs-lookup"><span data-stu-id="bb4b2-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="bb4b2-113">Signature numérique d'un message SOAP sortant.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="bb4b2-114">Oui</span><span class="sxs-lookup"><span data-stu-id="bb4b2-114">Yes</span></span>|  
        |<span data-ttu-id="bb4b2-115">Vérification de la signature d'un message SOAP entrant.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="bb4b2-116">Non </span><span class="sxs-lookup"><span data-stu-id="bb4b2-116">No</span></span>|  
        |<span data-ttu-id="bb4b2-117">Chiffrement d'un message SOAP sortant.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="bb4b2-118">Non </span><span class="sxs-lookup"><span data-stu-id="bb4b2-118">No</span></span>|  
        |<span data-ttu-id="bb4b2-119">Déchiffrement d'un message SOAP entrant.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="bb4b2-120">Oui</span><span class="sxs-lookup"><span data-stu-id="bb4b2-120">Yes</span></span>|  
  
    2. <span data-ttu-id="bb4b2-121">Déterminez l'emplacement et le nom du magasin de certificats dans lequel le certificat est stocké.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="bb4b2-122">Le magasin de certificats dans lequel le certificat est stocké est spécifié dans le code d'application ou dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="bb4b2-123">Ainsi, l'exemple suivant spécifie que le certificat se trouve dans le magasin de certificats `CurrentUser` nommé `My`.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="bb4b2-124">Déterminez où se trouve la clé privée du certificat sur l’ordinateur en utilisant [l’outil FindPrivateKey.](../../../../docs/framework/wcf/samples/findprivatekey.md)</span><span class="sxs-lookup"><span data-stu-id="bb4b2-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="bb4b2-125">[L’outil FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) exige le nom du magasin de certificats, l’emplacement du magasin de certificats, et quelque chose qui identifie uniquement le certificat.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="bb4b2-126">Il accepte le nom de sujet du certificat ou son empreinte numérique comme identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="bb4b2-127">Pour plus d’informations sur la façon de déterminer l’empreinte du pouce pour un certificat, voir [comment: Récupérer l’empreinte de pouce d’un certificat](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="bb4b2-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="bb4b2-128">L’exemple de code suivant utilise [l’outil FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) pour déterminer `My` l’emplacement de la clé privée pour un certificat dans `CurrentUser` le magasin avec une empreinte de pouce de `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="bb4b2-129">Déterminez le compte sous lequel WCF est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="bb4b2-130">Le tableau suivant détaille le compte dans lequel WCF est en cours d’exécution pour un scénario donné.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="bb4b2-131">Scénario</span><span class="sxs-lookup"><span data-stu-id="bb4b2-131">Scenario</span></span>|<span data-ttu-id="bb4b2-132">Identité du processus</span><span class="sxs-lookup"><span data-stu-id="bb4b2-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="bb4b2-133">Client (console ou application WinForms).</span><span class="sxs-lookup"><span data-stu-id="bb4b2-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="bb4b2-134">Utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="bb4b2-135">Service auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-135">Service that is self-hosted.</span></span>|<span data-ttu-id="bb4b2-136">Utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="bb4b2-137">Service hébergé dans IIS 6.0 (Windows Server 2003) ou IIS 7.0 (Windows Vista).</span><span class="sxs-lookup"><span data-stu-id="bb4b2-137">Service that is hosted in IIS 6.0 (Windows Server 2003) or IIS 7.0 (Windows Vista).</span></span>|<span data-ttu-id="bb4b2-138">SERVICE RÉSEAU</span><span class="sxs-lookup"><span data-stu-id="bb4b2-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="bb4b2-139">Service hébergé dans IIS 5.X (Windows XP).</span><span class="sxs-lookup"><span data-stu-id="bb4b2-139">Service that is hosted in IIS 5.X (Windows XP).</span></span>|<span data-ttu-id="bb4b2-140">Contrôlé par l'élément `<processModel>` dans le fichier Machine.config.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="bb4b2-141">Le compte par défaut est ASPNET.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-141">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="bb4b2-142">Grant lire l’accès au fichier qui contient la clé privée du compte que WCF est en cours d’exécution sous, en utilisant un outil tel que icacls.exe.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="bb4b2-143">L’exemple de code suivant modifie la liste de contrôle d’accès discrétionnaire (DACL) pour que le fichier spécifié accorde au compte NETWORK SERVICE lus (:R) l’accès au fichier.</span><span class="sxs-lookup"><span data-stu-id="bb4b2-143">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="bb4b2-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb4b2-144">See also</span></span>

- [<span data-ttu-id="bb4b2-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="bb4b2-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [<span data-ttu-id="bb4b2-146">Comment : récupérer l'empreinte numérique d'un certificat</span><span class="sxs-lookup"><span data-stu-id="bb4b2-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="bb4b2-147">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="bb4b2-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
