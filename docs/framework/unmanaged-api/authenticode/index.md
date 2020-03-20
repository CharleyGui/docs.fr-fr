---
title: Authenticode (Informations de référence sur les API non managées)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 1b8b2222950c75f7f9d2ec2704f722087645cd7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132454"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="eee4f-102">Authenticode (Informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="eee4f-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="eee4f-103">Prend en charge le module de création et de vérification des licences XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="eee4f-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eee4f-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="eee4f-104">In This Section</span></span>  
 [<span data-ttu-id="eee4f-105">_AxlGetIssuerPublicKeyHash, fonction</span><span class="sxs-lookup"><span data-stu-id="eee4f-105">_AxlGetIssuerPublicKeyHash Function</span></span>](axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="eee4f-106">Récupère le hachage SHA-1 de la clé publique associée à la clé privée utilisée pour signer le certificat spécifié.</span><span class="sxs-lookup"><span data-stu-id="eee4f-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="eee4f-107">_AxlPublicKeyBlobToPublicKeyToken, fonction</span><span class="sxs-lookup"><span data-stu-id="eee4f-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="eee4f-108">Calcule le jeton de clé publique de nom fort à partir d'un format CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="eee4f-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="eee4f-109">_AxlRSAKeyValueToPublicKeyToken, fonction</span><span class="sxs-lookup"><span data-stu-id="eee4f-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="eee4f-110">Convertit un modulo et un exposant en un jeton de clé publique de nom fort.</span><span class="sxs-lookup"><span data-stu-id="eee4f-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="eee4f-111">CertFreeAuthenticodeSignerInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="eee4f-111">CertFreeAuthenticodeSignerInfo Function</span></span>](certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="eee4f-112">Libère les ressources allouées pour la structure AXL_AUTHENTICODE_SIGNER_INFO.</span><span class="sxs-lookup"><span data-stu-id="eee4f-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="eee4f-113">CertFreeAuthenticodeTimestamperInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="eee4f-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="eee4f-114">Libère les ressources allouées pour la structure AXL_AUTHENTICODE_TIMESTAMPER_INFO.</span><span class="sxs-lookup"><span data-stu-id="eee4f-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="eee4f-115">CertTimestampAuthenticodeLicense, fonction</span><span class="sxs-lookup"><span data-stu-id="eee4f-115">CertTimestampAuthenticodeLicense Function</span></span>](certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="eee4f-116">Effectue un horodatage d'une licence XrML Authenticode créée par CertCreateAuthenticodeLicense.</span><span class="sxs-lookup"><span data-stu-id="eee4f-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="eee4f-117">CertVerifyAuthenticodeLicense, fonction</span><span class="sxs-lookup"><span data-stu-id="eee4f-117">CertVerifyAuthenticodeLicense Function</span></span>](certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="eee4f-118">Vérifie la validité d'une licence XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="eee4f-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="eee4f-119">AXL_AUTHENTICODE_SIGNER_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="eee4f-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="eee4f-120">Définit les informations du signataire Authenticode.</span><span class="sxs-lookup"><span data-stu-id="eee4f-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="eee4f-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="eee4f-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="eee4f-122">Définit les informations de l'horodateur Authenticode.</span><span class="sxs-lookup"><span data-stu-id="eee4f-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee4f-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eee4f-123">See also</span></span>

- [<span data-ttu-id="eee4f-124">Référence API non gestion</span><span class="sxs-lookup"><span data-stu-id="eee4f-124">Unmanaged API Reference</span></span>](../index.md)
