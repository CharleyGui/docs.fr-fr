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
ms.openlocfilehash: 904dcb707e704cfec2dba4e6587f7e3acaf7b538
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732328"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="f6e46-102">GetHashFromHandle, fonction</span><span class="sxs-lookup"><span data-stu-id="f6e46-102">GetHashFromHandle Function</span></span>

<span data-ttu-id="f6e46-103">Génère un hachage sur le contenu du fichier avec le handle de fichier spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="f6e46-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="f6e46-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="f6e46-104">This function has been deprecated.</span></span> <span data-ttu-id="f6e46-105">Utilisez la méthode [ICLRStrongName :: GetHashFromHandle (](../hosting/iclrstrongname-gethashfromhandle-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="f6e46-105">Use the [ICLRStrongName::GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6e46-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6e46-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6e46-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f6e46-107">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="f6e46-108">dans Handle du fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="f6e46-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="f6e46-109">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="f6e46-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="f6e46-110">Utilisez zéro pour l’algorithme par défaut.</span><span class="sxs-lookup"><span data-stu-id="f6e46-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="f6e46-111">à Mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="f6e46-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="f6e46-112">dans Taille maximale demandée de `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="f6e46-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="f6e46-113">à Taille, en octets, du retourné `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="f6e46-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6e46-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f6e46-114">Requirements</span></span>  

 <span data-ttu-id="f6e46-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6e46-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6e46-116">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="f6e46-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f6e46-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6e46-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f6e46-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6e46-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6e46-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6e46-119">See also</span></span>

- [<span data-ttu-id="f6e46-120">GetHashFromHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="f6e46-120">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="f6e46-121">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="f6e46-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
