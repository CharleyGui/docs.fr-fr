---
title: GetHashFromHandle, fonction
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
ms.openlocfilehash: dc241324f5844610d7b86b7cb9668f84d4525395
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140665"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="ea9b3-102">GetHashFromHandle, fonction</span><span class="sxs-lookup"><span data-stu-id="ea9b3-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="ea9b3-103">Génère un hachage sur le contenu du fichier avec le handle de fichier spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="ea9b3-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-104">This function has been deprecated.</span></span> <span data-ttu-id="ea9b3-105">Utilisez la méthode [ICLRStrongName :: GetHashFromHandle (](../hosting/iclrstrongname-gethashfromhandle-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-105">Use the [ICLRStrongName::GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea9b3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea9b3-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea9b3-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ea9b3-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="ea9b3-108">dans Handle du fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="ea9b3-109">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="ea9b3-110">Utilisez zéro pour l’algorithme par défaut.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="ea9b3-111">à Mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="ea9b3-112">dans Taille maximale de `pbHash`demandée.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="ea9b3-113">à Taille, en octets, de la `pbHash`retournée.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea9b3-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="ea9b3-114">Requirements</span></span>  
 <span data-ttu-id="ea9b3-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea9b3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea9b3-116">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="ea9b3-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ea9b3-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ea9b3-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea9b3-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea9b3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea9b3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea9b3-119">See also</span></span>

- [<span data-ttu-id="ea9b3-120">GetHashFromHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="ea9b3-120">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="ea9b3-121">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="ea9b3-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
