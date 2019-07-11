---
title: _AxlGetIssuerPublicKeyHash, fonction
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de55594db68e084009a095a083e065fbd0b8f0df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741327"
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="f8a44-102">\_AxlGetIssuerPublicKeyHash (fonction)</span><span class="sxs-lookup"><span data-stu-id="f8a44-102">\_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="f8a44-103">Récupère le hachage SHA-1 de la clé publique associée à la clé privée utilisée pour signer le certificat spécifié.</span><span class="sxs-lookup"><span data-stu-id="f8a44-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8a44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8a44-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8a44-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8a44-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="f8a44-106">[en entrée] L'objet blob de clé publique CSP.</span><span class="sxs-lookup"><span data-stu-id="f8a44-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="f8a44-107">Consultez le [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span><span class="sxs-lookup"><span data-stu-id="f8a44-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="f8a44-108">[en sortie] Un pointeur vers WCHAR \* pour recevoir le jeton de clé publique codé en hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="f8a44-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8a44-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f8a44-109">Return Value</span></span>  
 <span data-ttu-id="f8a44-110">`S_OK` si la fonction réussit ; sinon `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="f8a44-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8a44-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8a44-111">See also</span></span>

- [<span data-ttu-id="f8a44-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="f8a44-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
