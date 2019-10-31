---
title: CertTimestampAuthenticodeLicense, fonction
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
ms.openlocfilehash: 3c5e803c874e1254510f75189846d7cb12cb1ee2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132475"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="29ab5-102">CertTimestampAuthenticodeLicense, fonction</span><span class="sxs-lookup"><span data-stu-id="29ab5-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="29ab5-103">Horodate une licence XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="29ab5-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ab5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29ab5-104">Syntax</span></span>  
  
```cpp  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29ab5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="29ab5-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="29ab5-106">[en entrée] La licence XrML Authenticode signée à horodater.</span><span class="sxs-lookup"><span data-stu-id="29ab5-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="29ab5-107">Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="29ab5-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="29ab5-108">[en entrée] L'URI du server d'horodatage.</span><span class="sxs-lookup"><span data-stu-id="29ab5-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="29ab5-109">[en sortie] Un pointeur vers CRYPT_DATA_BLOB pour recevoir la signature de l'horodatage codé en base64.</span><span class="sxs-lookup"><span data-stu-id="29ab5-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="29ab5-110">Il incombe à l’appelant de libérer `pTimestampSignatureBlob`->`pbData` avec `HepFree()` après utilisation.</span><span class="sxs-lookup"><span data-stu-id="29ab5-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="29ab5-111">Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="29ab5-111">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29ab5-112">Notes</span><span class="sxs-lookup"><span data-stu-id="29ab5-112">Remarks</span></span>  
 <span data-ttu-id="29ab5-113">La signature de l'horodatage est en réalité un message PKCS #7 SignedData dont le contenu est la forme binaire de la valeur de SignatureValue de la signature de la licence.</span><span class="sxs-lookup"><span data-stu-id="29ab5-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="29ab5-114">Ceci agit comme une contre-signature de la licence.</span><span class="sxs-lookup"><span data-stu-id="29ab5-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29ab5-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="29ab5-115">Return Value</span></span>  
 <span data-ttu-id="29ab5-116">`S_OK` si la fonction réussit.</span><span class="sxs-lookup"><span data-stu-id="29ab5-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="29ab5-117">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="29ab5-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ab5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29ab5-118">See also</span></span>

- [<span data-ttu-id="29ab5-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="29ab5-119">Authenticode</span></span>](index.md)
