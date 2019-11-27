---
title: IMetaDataImport::FindMethod, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: 470b6511366cef1680eaf97f9ab376736add55c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437899"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="1257e-102">IMetaDataImport::FindMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="1257e-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="1257e-103">Obtient un pointeur vers le jeton MethodDef pour la méthode qui est entourée de la <xref:System.Type> spécifiée et qui a le nom et la signature de métadonnées spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1257e-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1257e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1257e-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1257e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1257e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="1257e-106">dans Jeton `mdTypeDef` pour le type (une classe ou une interface) qui englobe le membre à rechercher.</span><span class="sxs-lookup"><span data-stu-id="1257e-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="1257e-107">Si cette valeur est `mdTokenNil`, la recherche est effectuée pour une fonction globale.</span><span class="sxs-lookup"><span data-stu-id="1257e-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="1257e-108">dans Nom de la méthode à rechercher.</span><span class="sxs-lookup"><span data-stu-id="1257e-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="1257e-109">dans Pointeur vers la signature de métadonnées binaires de la méthode.</span><span class="sxs-lookup"><span data-stu-id="1257e-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="1257e-110">dans Taille en octets de `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="1257e-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="1257e-111">à Pointeur vers le jeton MethodDef correspondant.</span><span class="sxs-lookup"><span data-stu-id="1257e-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1257e-112">Notes</span><span class="sxs-lookup"><span data-stu-id="1257e-112">Remarks</span></span>  
 <span data-ttu-id="1257e-113">Vous spécifiez la méthode à l’aide de l’interface ou de la classe englobante (`td`), son nom (`szName`) et éventuellement sa signature (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="1257e-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="1257e-114">Il peut y avoir plusieurs méthodes portant le même nom dans une classe ou une interface.</span><span class="sxs-lookup"><span data-stu-id="1257e-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="1257e-115">Dans ce cas, transmettez la signature de la méthode pour rechercher la correspondance unique.</span><span class="sxs-lookup"><span data-stu-id="1257e-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="1257e-116">La signature transmise à `FindMethod` doit avoir été générée dans l’étendue actuelle, car les signatures sont liées à une portée particulière.</span><span class="sxs-lookup"><span data-stu-id="1257e-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="1257e-117">Une signature peut incorporer un jeton qui identifie la classe englobante ou le type valeur.</span><span class="sxs-lookup"><span data-stu-id="1257e-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="1257e-118">Le jeton est un index dans la table TypeDef locale.</span><span class="sxs-lookup"><span data-stu-id="1257e-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="1257e-119">Vous ne pouvez pas générer de signature au moment de l’exécution en dehors du contexte de l’étendue actuelle et utiliser cette signature comme entrée pour l’entrée dans `FindMethod`.</span><span class="sxs-lookup"><span data-stu-id="1257e-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="1257e-120">`FindMethod` recherche uniquement les méthodes qui ont été définies directement dans la classe ou l’interface ; il ne trouve pas les méthodes héritées.</span><span class="sxs-lookup"><span data-stu-id="1257e-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1257e-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1257e-121">Requirements</span></span>  
 <span data-ttu-id="1257e-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1257e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1257e-123">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1257e-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1257e-124">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1257e-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1257e-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1257e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1257e-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1257e-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="1257e-127">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="1257e-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1257e-128">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="1257e-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
