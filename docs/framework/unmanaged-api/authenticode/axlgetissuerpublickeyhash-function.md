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
ms.openlocfilehash: 4b101a912eb58ed14f81d847ea2fd6ce9f22c065
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787089"
---
# <a name="_axlgetissuerpublickeyhash-function"></a><span data-ttu-id="2b459-102">\_AxlGetIssuerPublicKeyHash fonction)</span><span class="sxs-lookup"><span data-stu-id="2b459-102">\_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="2b459-103">Récupère le hachage SHA-1 de la clé publique associée à la clé privée utilisée pour signer le certificat spécifié.</span><span class="sxs-lookup"><span data-stu-id="2b459-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b459-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b459-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b459-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2b459-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="2b459-106">[en entrée] L'objet blob de clé publique CSP.</span><span class="sxs-lookup"><span data-stu-id="2b459-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="2b459-107">Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="2b459-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="2b459-108">[en sortie] Un pointeur vers WCHAR \* pour recevoir le jeton de clé publique codé en hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="2b459-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b459-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2b459-109">Return Value</span></span>  
 <span data-ttu-id="2b459-110">`S_OK` si la fonction réussit ; sinon `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="2b459-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b459-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b459-111">See also</span></span>

- [<span data-ttu-id="2b459-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2b459-112">Authenticode</span></span>](index.md)
