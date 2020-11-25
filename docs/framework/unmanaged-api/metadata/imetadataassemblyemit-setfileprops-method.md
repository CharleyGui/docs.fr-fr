---
title: IMetaDataAssemblyEmit::SetFileProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
ms.openlocfilehash: 9cf5f3d926c1e742dd9134e7bf292df53e1a4909
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720176"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="038cc-102">IMetaDataAssemblyEmit::SetFileProps, méthode</span><span class="sxs-lookup"><span data-stu-id="038cc-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>

<span data-ttu-id="038cc-103">Modifie la structure de métadonnées `File` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="038cc-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="038cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="038cc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="038cc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="038cc-105">Parameters</span></span>  

 `file`  
 <span data-ttu-id="038cc-106">dans Jeton de métadonnées qui spécifie la `File` structure de métadonnées à modifier.</span><span class="sxs-lookup"><span data-stu-id="038cc-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="038cc-107">dans Pointeur vers les données de hachage associées au fichier.</span><span class="sxs-lookup"><span data-stu-id="038cc-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="038cc-108">dans Taille en octets de `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="038cc-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="038cc-109">dans Combinaison d’opérations de bits de valeurs [CorFileFlags,](corfileflags-enumeration.md) qui spécifient différents attributs du fichier.</span><span class="sxs-lookup"><span data-stu-id="038cc-109">[in] A bitwise combination of [CorFileFlags](corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="038cc-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="038cc-110">Remarks</span></span>  

 <span data-ttu-id="038cc-111">Pour créer une `File` structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit ::D efinefile](imetadataassemblyemit-definefile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="038cc-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="038cc-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="038cc-112">Requirements</span></span>  

 <span data-ttu-id="038cc-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="038cc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="038cc-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="038cc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="038cc-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="038cc-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="038cc-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="038cc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="038cc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="038cc-117">See also</span></span>

- [<span data-ttu-id="038cc-118">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="038cc-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
