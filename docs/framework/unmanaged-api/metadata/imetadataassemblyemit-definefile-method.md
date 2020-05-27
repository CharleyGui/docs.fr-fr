---
title: IMetaDataAssemblyEmit::DefineFile, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
ms.openlocfilehash: 61d81c94e3a9c092b5d45791962635c761e8da8a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008142"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="db271-102">IMetaDataAssemblyEmit::DefineFile, méthode</span><span class="sxs-lookup"><span data-stu-id="db271-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="db271-103">Crée une structure `File` contenant les métadonnées pour l'assembly référencé par cet assembly et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="db271-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db271-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db271-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db271-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="db271-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="db271-106">dans Nom du fichier à consommer.</span><span class="sxs-lookup"><span data-stu-id="db271-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="db271-107">dans Pointeur vers les données de hachage associées à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="db271-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="db271-108">dans Taille en octets de `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="db271-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="db271-109">dans Combinaison d’opérations de bits de `FileFlags` valeurs qui spécifient des paramètres de propriété.</span><span class="sxs-lookup"><span data-stu-id="db271-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="db271-110">à Pointeur vers le jeton retourné `File` .</span><span class="sxs-lookup"><span data-stu-id="db271-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db271-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="db271-111">Remarks</span></span>  
 <span data-ttu-id="db271-112">Une `File` structure de métadonnées doit être définie pour chaque fichier qui faisait partie de cet assembly au moment de la génération de cet assembly, à l’exception du fichier qui contient les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="db271-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db271-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="db271-113">Requirements</span></span>  
 <span data-ttu-id="db271-114">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db271-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db271-115">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="db271-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db271-116">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="db271-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db271-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db271-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db271-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db271-118">See also</span></span>

- [<span data-ttu-id="db271-119">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="db271-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
