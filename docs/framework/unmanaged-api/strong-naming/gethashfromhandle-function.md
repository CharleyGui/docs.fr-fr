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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3eac353252f5a97402cbd883895b3e397c39edd6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799179"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="798cd-102">GetHashFromHandle, fonction</span><span class="sxs-lookup"><span data-stu-id="798cd-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="798cd-103">Génère un hachage sur le contenu du fichier avec le handle de fichier spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="798cd-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="798cd-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="798cd-104">This function has been deprecated.</span></span> <span data-ttu-id="798cd-105">Utilisez la méthode [ICLRStrongName :: GetHashFromHandle (](../hosting/iclrstrongname-gethashfromhandle-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="798cd-105">Use the [ICLRStrongName::GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="798cd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="798cd-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="798cd-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="798cd-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="798cd-108">dans Handle du fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="798cd-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="798cd-109">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="798cd-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="798cd-110">Utilisez zéro pour l’algorithme par défaut.</span><span class="sxs-lookup"><span data-stu-id="798cd-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="798cd-111">à Mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="798cd-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="798cd-112">dans Taille maximale demandée de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="798cd-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="798cd-113">à Taille, en octets, du retourné `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="798cd-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="798cd-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="798cd-114">Requirements</span></span>  
 <span data-ttu-id="798cd-115">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="798cd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="798cd-116">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="798cd-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="798cd-117">**Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="798cd-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="798cd-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="798cd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="798cd-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="798cd-119">See also</span></span>

- [<span data-ttu-id="798cd-120">GetHashFromHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="798cd-120">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="798cd-121">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="798cd-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
