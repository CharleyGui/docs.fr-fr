---
title: Méthode ICLRStrongName::GetHashFromHandle
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
ms.openlocfilehash: e2d71f7c61b02273bdcaf182f6f79ca3c2a2c75f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762072"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="d18bf-102">Méthode ICLRStrongName::GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="d18bf-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="d18bf-103">Génère un hachage sur le contenu du fichier qui a le handle de fichier spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="d18bf-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d18bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d18bf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d18bf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d18bf-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="d18bf-106">dans Handle du fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="d18bf-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d18bf-107">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="d18bf-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="d18bf-108">Utilisez zéro pour l’algorithme par défaut.</span><span class="sxs-lookup"><span data-stu-id="d18bf-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d18bf-109">à Mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="d18bf-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d18bf-110">dans Taille maximale demandée de `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="d18bf-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d18bf-111">à Taille, en octets, du retourné `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="d18bf-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d18bf-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d18bf-112">Return Value</span></span>  
 <span data-ttu-id="d18bf-113">`S_OK`Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="d18bf-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d18bf-114">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="d18bf-114">Requirements</span></span>  
 <span data-ttu-id="d18bf-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d18bf-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d18bf-116">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="d18bf-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d18bf-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d18bf-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d18bf-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d18bf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d18bf-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d18bf-119">See also</span></span>

- [<span data-ttu-id="d18bf-120">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="d18bf-120">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
