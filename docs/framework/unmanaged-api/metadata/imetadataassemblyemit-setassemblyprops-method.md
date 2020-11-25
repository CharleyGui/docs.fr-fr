---
title: IMetaDataAssemblyEmit::SetAssemblyProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
ms.openlocfilehash: 3736e7279056e015b157758b1233cf6dc5aa6d8d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720202"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="30b1e-102">IMetaDataAssemblyEmit::SetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="30b1e-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>

<span data-ttu-id="30b1e-103">Modifie la structure de métadonnées `Assembly` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="30b1e-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30b1e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30b1e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="30b1e-105">Parameters</span></span>  

 `pma`  
 <span data-ttu-id="30b1e-106">dans Jeton de métadonnées qui spécifie la `Assembly` structure de métadonnées à modifier.</span><span class="sxs-lookup"><span data-stu-id="30b1e-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="30b1e-107">dans Pointeur vers la clé publique de l’éditeur de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="30b1e-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="30b1e-108">dans Taille en octets de `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="30b1e-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="30b1e-109">dans Identificateur de l’algorithme de hachage utilisé pour hacher les fichiers d’assembly.</span><span class="sxs-lookup"><span data-stu-id="30b1e-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="30b1e-110">dans Nom de texte explicite de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="30b1e-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="30b1e-111">dans Pointeur vers ASSEMBLYMETADATA qui contient les informations de version, de plateforme et de paramètres régionaux de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="30b1e-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="30b1e-112">dans Combinaison d’opérations de bits de valeurs [AssemblyFlags](assemblyflags-enumeration.md) qui spécifient différents attributs de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="30b1e-112">[in] A bitwise combination of [AssemblyFlags](assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30b1e-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="30b1e-113">Remarks</span></span>  

 <span data-ttu-id="30b1e-114">Pour créer une `Assembly` structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit ::D efineassembly](imetadataassemblyemit-defineassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="30b1e-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30b1e-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="30b1e-115">Requirements</span></span>  

 <span data-ttu-id="30b1e-116">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30b1e-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30b1e-117">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="30b1e-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30b1e-118">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="30b1e-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30b1e-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30b1e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b1e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30b1e-120">See also</span></span>

- [<span data-ttu-id="30b1e-121">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="30b1e-121">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
