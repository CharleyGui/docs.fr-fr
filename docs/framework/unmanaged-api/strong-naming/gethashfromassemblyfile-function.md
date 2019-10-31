---
title: GetHashFromAssemblyFile, fonction
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
ms.openlocfilehash: 866b34acae333f043d8e13f4d0ebd55f32046334
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140733"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="bd577-102">GetHashFromAssemblyFile, fonction</span><span class="sxs-lookup"><span data-stu-id="bd577-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="bd577-103">Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="bd577-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="bd577-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="bd577-104">This function has been deprecated.</span></span> <span data-ttu-id="bd577-105">Utilisez la méthode [ICLRStrongName :: GetHashFromAssemblyFile (](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="bd577-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd577-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd577-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd577-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bd577-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="bd577-108">dans Chemin d’accès au fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="bd577-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="bd577-109">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="bd577-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="bd577-110">Utilisez zéro pour l’algorithme de hachage par défaut.</span><span class="sxs-lookup"><span data-stu-id="bd577-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="bd577-111">à Mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="bd577-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="bd577-112">dans Taille maximale de `pbHash`demandée.</span><span class="sxs-lookup"><span data-stu-id="bd577-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="bd577-113">à Taille retournée, en octets, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="bd577-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd577-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="bd577-114">Requirements</span></span>  
 <span data-ttu-id="bd577-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd577-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd577-116">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="bd577-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="bd577-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bd577-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd577-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd577-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd577-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd577-119">See also</span></span>

- [<span data-ttu-id="bd577-120">GetHashFromAssemblyFile, méthode</span><span class="sxs-lookup"><span data-stu-id="bd577-120">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="bd577-121">GetHashFromAssemblyFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="bd577-121">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="bd577-122">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="bd577-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
