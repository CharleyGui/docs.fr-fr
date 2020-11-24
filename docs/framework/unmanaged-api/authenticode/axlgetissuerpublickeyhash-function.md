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
ms.openlocfilehash: 49674e43109108e41b135cecbec061ad61e14865
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679960"
---
# <a name="_axlgetissuerpublickeyhash-function"></a><span data-ttu-id="ec86f-102">\_AxlGetIssuerPublicKeyHash fonction)</span><span class="sxs-lookup"><span data-stu-id="ec86f-102">\_AxlGetIssuerPublicKeyHash Function</span></span>

<span data-ttu-id="ec86f-103">Récupère le hachage SHA-1 de la clé publique associée à la clé privée utilisée pour signer le certificat spécifié.</span><span class="sxs-lookup"><span data-stu-id="ec86f-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec86f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec86f-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec86f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ec86f-105">Parameters</span></span>  

 `pChainContext`  
 <span data-ttu-id="ec86f-106">[en entrée] L'objet blob de clé publique CSP.</span><span class="sxs-lookup"><span data-stu-id="ec86f-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="ec86f-107">Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="ec86f-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="ec86f-108">[en sortie] Un pointeur vers WCHAR \* pour recevoir le jeton de clé publique codé en hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="ec86f-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec86f-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ec86f-109">Return Value</span></span>  

 <span data-ttu-id="ec86f-110">`S_OK` si la fonction réussit ; sinon `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="ec86f-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec86f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec86f-111">See also</span></span>

- [<span data-ttu-id="ec86f-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="ec86f-112">Authenticode</span></span>](index.md)
