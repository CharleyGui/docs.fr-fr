---
title: Méthode ICLRStrongName::GetHashFromAssemblyFile
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
ms.openlocfilehash: 007de0365bf70b1f4a9a9e0f01807e7fdac19f54
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762147"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="a4dc8-102">Méthode ICLRStrongName::GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="a4dc8-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="a4dc8-103">Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="a4dc8-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4dc8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4dc8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4dc8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a4dc8-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="a4dc8-106">dans Chemin d’accès au fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="a4dc8-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="a4dc8-107">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="a4dc8-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="a4dc8-108">Utilisez zéro pour l’algorithme de hachage par défaut.</span><span class="sxs-lookup"><span data-stu-id="a4dc8-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="a4dc8-109">à Mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="a4dc8-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="a4dc8-110">dans Taille maximale demandée de `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="a4dc8-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="a4dc8-111">à Taille retournée, en octets, de `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="a4dc8-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4dc8-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a4dc8-112">Return Value</span></span>  
 <span data-ttu-id="a4dc8-113">`S_OK`Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="a4dc8-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4dc8-114">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="a4dc8-114">Requirements</span></span>  
 <span data-ttu-id="a4dc8-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4dc8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4dc8-116">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="a4dc8-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a4dc8-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a4dc8-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4dc8-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4dc8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4dc8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4dc8-119">See also</span></span>

- [<span data-ttu-id="a4dc8-120">GetHashFromAssemblyFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="a4dc8-120">GetHashFromAssemblyFileW Method</span></span>](iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="a4dc8-121">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="a4dc8-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
