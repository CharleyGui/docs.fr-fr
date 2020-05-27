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
ms.openlocfilehash: 7c6adcbcfe64f63048078b4ccba6727a58531033
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008103"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="ad77a-102">IMetaDataAssemblyEmit::SetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="ad77a-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="ad77a-103">Modifie la structure de métadonnées `Assembly` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ad77a-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad77a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad77a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ad77a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ad77a-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="ad77a-106">dans Jeton de métadonnées qui spécifie la `Assembly` structure de métadonnées à modifier.</span><span class="sxs-lookup"><span data-stu-id="ad77a-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="ad77a-107">dans Pointeur vers la clé publique de l’éditeur de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ad77a-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="ad77a-108">dans Taille en octets de `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="ad77a-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="ad77a-109">dans Identificateur de l’algorithme de hachage utilisé pour hacher les fichiers d’assembly.</span><span class="sxs-lookup"><span data-stu-id="ad77a-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="ad77a-110">dans Nom de texte explicite de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ad77a-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="ad77a-111">dans Pointeur vers ASSEMBLYMETADATA qui contient les informations de version, de plateforme et de paramètres régionaux de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ad77a-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="ad77a-112">dans Combinaison d’opérations de bits de valeurs [AssemblyFlags](assemblyflags-enumeration.md) qui spécifient différents attributs de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ad77a-112">[in] A bitwise combination of [AssemblyFlags](assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad77a-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="ad77a-113">Remarks</span></span>  
 <span data-ttu-id="ad77a-114">Pour créer une `Assembly` structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit ::D efineassembly](imetadataassemblyemit-defineassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ad77a-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad77a-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ad77a-115">Requirements</span></span>  
 <span data-ttu-id="ad77a-116">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad77a-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad77a-117">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ad77a-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad77a-118">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ad77a-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad77a-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad77a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad77a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad77a-120">See also</span></span>

- [<span data-ttu-id="ad77a-121">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ad77a-121">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
