---
title: IMetaDataEmit::DefineMethod, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
ms.openlocfilehash: c46b075341742aac605537a08b762b3cf47ef35b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431808"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="b9522-102">IMetaDataEmit::DefineMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="b9522-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="b9522-103">Crée une définition pour une méthode ou une fonction globale avec la signature spécifiée et retourne un jeton à cette définition de méthode.</span><span class="sxs-lookup"><span data-stu-id="b9522-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9522-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9522-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9522-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9522-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b9522-106">dans Jeton `mdTypedef` de la classe parente ou de l’interface parente de la méthode.</span><span class="sxs-lookup"><span data-stu-id="b9522-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="b9522-107">Définissez `td` sur `mdTokenNil`, si vous définissez une fonction globale.</span><span class="sxs-lookup"><span data-stu-id="b9522-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="b9522-108">dans Nom du membre au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9522-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="b9522-109">dans Valeur de l’énumération [CorMethodAttr,](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) qui spécifie les attributs de la méthode ou de la fonction globale.</span><span class="sxs-lookup"><span data-stu-id="b9522-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b9522-110">dans Signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="b9522-110">[in] The method signature.</span></span> <span data-ttu-id="b9522-111">La signature est conservée telle qu’elle est fournie.</span><span class="sxs-lookup"><span data-stu-id="b9522-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="b9522-112">Si vous devez spécifier des informations supplémentaires pour tous les paramètres, utilisez la méthode [IMetaDataEmit :: SetParamProps,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b9522-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b9522-113">dans Nombre d’octets dans `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="b9522-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="b9522-114">dans Adresse du code.</span><span class="sxs-lookup"><span data-stu-id="b9522-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="b9522-115">dans Valeur de l’énumération [CorMethodImpl,](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) qui spécifie les fonctionnalités d’implémentation de la méthode.</span><span class="sxs-lookup"><span data-stu-id="b9522-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="b9522-116">à Jeton de membre.</span><span class="sxs-lookup"><span data-stu-id="b9522-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9522-117">Notes</span><span class="sxs-lookup"><span data-stu-id="b9522-117">Remarks</span></span>  
 <span data-ttu-id="b9522-118">L’API de métadonnées garantit de conserver les méthodes dans le même ordre que celui que l’appelant les émet pour une interface ou une classe englobante donnée, spécifiée dans le paramètre `td`.</span><span class="sxs-lookup"><span data-stu-id="b9522-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="b9522-119">Vous trouverez ci-dessous des informations supplémentaires concernant l’utilisation des `DefineMethod` et des paramètres de paramètres particuliers.</span><span class="sxs-lookup"><span data-stu-id="b9522-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="b9522-120">Emplacements dans le V-table</span><span class="sxs-lookup"><span data-stu-id="b9522-120">Slots in the V-table</span></span>  
 <span data-ttu-id="b9522-121">Le runtime utilise les définitions de méthode pour configurer des emplacements v-table.</span><span class="sxs-lookup"><span data-stu-id="b9522-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="b9522-122">Dans le cas où un ou plusieurs emplacements doivent être ignorés, par exemple pour conserver la parité avec une disposition d’interface COM, une méthode factice est définie pour prendre l’emplacement ou les emplacements dans la v-table ; Affectez à la `dwMethodFlags` la valeur `mdRTSpecialName` de l’énumération [CorMethodAttr,](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) et spécifiez le nom comme suit :</span><span class="sxs-lookup"><span data-stu-id="b9522-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="b9522-123">_VtblGap\< *>* \<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="b9522-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="b9522-124">où *numéro* de séquence est le numéro de séquence de la méthode et *CountOfSlots* est le nombre d’emplacements à ignorer dans la table v.</span><span class="sxs-lookup"><span data-stu-id="b9522-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="b9522-125">Si *CountOfSlots* est omis, 1 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="b9522-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="b9522-126">Ces méthodes factices ne peuvent pas être appelées à partir de code managé ou non managé et toute tentative de les appeler à partir de code managé ou non managé génère une exception.</span><span class="sxs-lookup"><span data-stu-id="b9522-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="b9522-127">Leur seul but est d’occuper de l’espace dans la vtable générée par le runtime pour l’intégration COM.</span><span class="sxs-lookup"><span data-stu-id="b9522-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="b9522-128">Méthodes dupliquées</span><span class="sxs-lookup"><span data-stu-id="b9522-128">Duplicate Methods</span></span>  
 <span data-ttu-id="b9522-129">Vous ne devez pas définir de méthodes en double.</span><span class="sxs-lookup"><span data-stu-id="b9522-129">You should not define duplicate methods.</span></span> <span data-ttu-id="b9522-130">Autrement dit, vous ne devez pas appeler `DefineMethod` avec un ensemble de valeurs en double dans les paramètres `td`, `wzName`et `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="b9522-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="b9522-131">(Ces trois paramètres définissent ensemble la méthode de manière unique.).</span><span class="sxs-lookup"><span data-stu-id="b9522-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="b9522-132">Toutefois, vous pouvez utiliser un triple dupliqué fourni qui, pour l’une des définitions de méthode, vous définissez le bit `mdPrivateScope` dans le paramètre `dwMethodFlags`.</span><span class="sxs-lookup"><span data-stu-id="b9522-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="b9522-133">(Le bit `mdPrivateScope` signifie que le compilateur n’émet pas de référence à cette définition de méthode.)</span><span class="sxs-lookup"><span data-stu-id="b9522-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="b9522-134">Informations d’implémentation de la méthode</span><span class="sxs-lookup"><span data-stu-id="b9522-134">Method Implementation Information</span></span>  
 <span data-ttu-id="b9522-135">Les informations sur l’implémentation de la méthode sont souvent inconnues au moment où la méthode est déclarée.</span><span class="sxs-lookup"><span data-stu-id="b9522-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="b9522-136">Par conséquent, vous n’avez pas besoin de transmettre des valeurs dans les paramètres `ulCodeRVA` et `dwImplFlags` lors de l’appel de `DefineMethod`.</span><span class="sxs-lookup"><span data-stu-id="b9522-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="b9522-137">Les valeurs peuvent être fournies ultérieurement via [IMetaDataEmit :: SetMethodImplFlags,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [IMetaDataEmit :: SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), selon le cas.</span><span class="sxs-lookup"><span data-stu-id="b9522-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="b9522-138">Dans certaines situations, telles que l’appel de la plateforme (PInvoke) ou les scénarios de COM Interop, le corps de la méthode n’est pas fourni et `ulCodeRVA` doit être défini sur zéro.</span><span class="sxs-lookup"><span data-stu-id="b9522-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="b9522-139">Dans ces situations, la méthode ne doit pas être marquée comme abstract, car le runtime localise l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="b9522-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="b9522-140">Définition d’une méthode pour PInvoke</span><span class="sxs-lookup"><span data-stu-id="b9522-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="b9522-141">Pour chaque fonction non managée à appeler par le biais de PInvoke, vous devez définir une méthode managée qui représente la fonction non managée cible.</span><span class="sxs-lookup"><span data-stu-id="b9522-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="b9522-142">Pour définir la méthode managée, utilisez `DefineMethod` avec certains des paramètres définis sur certaines valeurs, en fonction de la façon dont PInvoke est utilisé :</span><span class="sxs-lookup"><span data-stu-id="b9522-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="b9522-143">True PInvoke : implique l’appel d’une méthode non managée externe qui réside dans une DLL non managée.</span><span class="sxs-lookup"><span data-stu-id="b9522-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="b9522-144">PInvoke local : implique l’appel d’une méthode Native non managée qui est incorporée dans le module managé actuel.</span><span class="sxs-lookup"><span data-stu-id="b9522-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="b9522-145">Les paramètres sont indiqués dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="b9522-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="b9522-146">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b9522-146">Parameter</span></span>|<span data-ttu-id="b9522-147">Valeurs pour True PInvoke</span><span class="sxs-lookup"><span data-stu-id="b9522-147">Values for true PInvoke</span></span>|<span data-ttu-id="b9522-148">Valeurs pour PInvoke local</span><span class="sxs-lookup"><span data-stu-id="b9522-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="b9522-149">Définir `mdStatic`; Désactivez `mdSynchronized` et `mdAbstract`.</span><span class="sxs-lookup"><span data-stu-id="b9522-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="b9522-150">Signature de méthode common language runtime (CLR) valide avec des paramètres qui sont des types managés valides.</span><span class="sxs-lookup"><span data-stu-id="b9522-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="b9522-151">Signature de méthode CLR valide avec des paramètres qui sont des types managés valides.</span><span class="sxs-lookup"><span data-stu-id="b9522-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="b9522-152">0</span><span class="sxs-lookup"><span data-stu-id="b9522-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="b9522-153">Définissez `miCil` et `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="b9522-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="b9522-154">Définissez `miNative` et `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="b9522-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b9522-155">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b9522-155">Requirements</span></span>  
 <span data-ttu-id="b9522-156">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9522-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9522-157">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b9522-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9522-158">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b9522-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9522-159">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9522-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9522-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9522-160">See also</span></span>

- [<span data-ttu-id="b9522-161">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="b9522-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b9522-162">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="b9522-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
