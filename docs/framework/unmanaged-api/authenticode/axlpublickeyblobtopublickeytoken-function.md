---
title: _AxlPublicKeyBlobToPublicKeyToken, fonction
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e2459b4f91e7e189990b65fa4d7ca860ff73c51
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741317"
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="96c54-102">\_AxlPublicKeyBlobToPublicKeyToken (fonction)</span><span class="sxs-lookup"><span data-stu-id="96c54-102">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="96c54-103">Calcule le jeton de clé publique de nom fort à partir d'un format CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="96c54-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96c54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96c54-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96c54-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="96c54-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="96c54-106">[en entrée] L'objet blob de clé publique CSP.</span><span class="sxs-lookup"><span data-stu-id="96c54-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="96c54-107">[en sortie] Un pointeur vers WCHAR \* pour recevoir le hachage de clé publique codé au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="96c54-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96c54-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="96c54-108">Return Value</span></span>  
 <span data-ttu-id="96c54-109">`S_OK` si la fonction réussit ; sinon `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="96c54-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96c54-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96c54-110">See also</span></span>

- [<span data-ttu-id="96c54-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="96c54-111">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
