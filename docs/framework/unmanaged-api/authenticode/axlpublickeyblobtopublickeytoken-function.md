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
ms.openlocfilehash: b4d720480e4c8b21b3aa56ce81634a26ac9c75de
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776671"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="68383-102">\_AxlPublicKeyBlobToPublicKeyToken fonction)</span><span class="sxs-lookup"><span data-stu-id="68383-102">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="68383-103">Calcule le jeton de clé publique de nom fort à partir d'un format CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="68383-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68383-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68383-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68383-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="68383-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="68383-106">[en entrée] L'objet blob de clé publique CSP.</span><span class="sxs-lookup"><span data-stu-id="68383-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="68383-107">[en sortie] Un pointeur vers WCHAR \* pour recevoir le hachage de clé publique codé au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="68383-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68383-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="68383-108">Return Value</span></span>  
 <span data-ttu-id="68383-109">`S_OK` si la fonction réussit ; sinon `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="68383-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68383-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68383-110">See also</span></span>

- [<span data-ttu-id="68383-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="68383-111">Authenticode</span></span>](index.md)
