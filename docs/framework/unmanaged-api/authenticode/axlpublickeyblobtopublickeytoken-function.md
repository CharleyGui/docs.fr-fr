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
ms.openlocfilehash: 989e99198efd1519f607a2e3164ff4de584e88af
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679882"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="b5450-102">\_AxlPublicKeyBlobToPublicKeyToken fonction)</span><span class="sxs-lookup"><span data-stu-id="b5450-102">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>

<span data-ttu-id="b5450-103">Calcule le jeton de clé publique de nom fort à partir d'un format CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="b5450-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5450-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5450-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5450-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b5450-105">Parameters</span></span>  

 `pCspPublicKeyBlob`  
 <span data-ttu-id="b5450-106">[en entrée] L'objet blob de clé publique CSP.</span><span class="sxs-lookup"><span data-stu-id="b5450-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="b5450-107">[en sortie] Un pointeur vers WCHAR \* pour recevoir le hachage de clé publique codé au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="b5450-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5450-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="b5450-108">Return Value</span></span>  

 <span data-ttu-id="b5450-109">`S_OK` si la fonction réussit ; sinon `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="b5450-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5450-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5450-110">See also</span></span>

- [<span data-ttu-id="b5450-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="b5450-111">Authenticode</span></span>](index.md)
