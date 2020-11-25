---
title: IMetaDataAssemblyEmit::SetExportedTypeProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: 076d027945dc27942e4b0989e14e86d829f76679
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713483"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="42915-102">IMetaDataAssemblyEmit::SetExportedTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="42915-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>

<span data-ttu-id="42915-103">Modifie la structure de métadonnées `ExportedType` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="42915-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42915-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42915-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42915-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="42915-105">Parameters</span></span>  

 `ct`  
 <span data-ttu-id="42915-106">dans Jeton de métadonnées qui spécifie la `ExportedType` structure de métadonnées à modifier.</span><span class="sxs-lookup"><span data-stu-id="42915-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="42915-107">dans Jeton, de type `File` , `AssemblyRef` ou `ExportedType` , qui spécifie la façon dont ce type est implémenté.</span><span class="sxs-lookup"><span data-stu-id="42915-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="42915-108">dans `TypeDef` Jeton référencé dans le fichier de code.</span><span class="sxs-lookup"><span data-stu-id="42915-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="42915-109">dans Combinaison d’opérations de bits de valeurs qui spécifient des attributs du type.</span><span class="sxs-lookup"><span data-stu-id="42915-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42915-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="42915-110">Remarks</span></span>  

 <span data-ttu-id="42915-111">Pour créer une `ExportedType` structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit ::D efineexportedtype](imetadataassemblyemit-defineexportedtype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="42915-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42915-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="42915-112">Requirements</span></span>  

 <span data-ttu-id="42915-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42915-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42915-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="42915-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42915-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42915-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42915-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42915-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42915-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42915-117">See also</span></span>

- [<span data-ttu-id="42915-118">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="42915-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
