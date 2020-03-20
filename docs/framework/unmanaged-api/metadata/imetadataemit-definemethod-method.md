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
ms.openlocfilehash: d4f3c95428d6f0f8807e284c5b54582428176511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177674"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="8f6e2-102">IMetaDataEmit::DefineMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="8f6e2-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="8f6e2-103">Crée une définition pour une méthode ou une fonction globale avec la signature spécifiée, et renvoie un jeton à cette définition de méthode.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f6e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f6e2-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8f6e2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8f6e2-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8f6e2-106">[dans] Le `mdTypedef` jeton de la classe mère ou de l’interface parente de la méthode.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="8f6e2-107">Définissez-vous, `td` `mdTokenNil`si vous définissez une fonction globale.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="8f6e2-108">[dans] Le nom du membre dans Unicode.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="8f6e2-109">[dans] Une valeur du recensement [de CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) qui spécifie les attributs de la méthode ou de la fonction globale.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8f6e2-110">[dans] La signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-110">[in] The method signature.</span></span> <span data-ttu-id="8f6e2-111">La signature est persistée comme fourni.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="8f6e2-112">Si vous avez besoin de spécifier des informations supplémentaires pour tous les paramètres, utilisez la méthode [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) méthode.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8f6e2-113">[dans] Le compte d’octets dans `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="8f6e2-114">[dans] L’adresse du code.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="8f6e2-115">[dans] Une valeur de l’énumération [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) qui spécifie les caractéristiques de mise en œuvre de la méthode.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="8f6e2-116">[out] Le jeton du membre.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f6e2-117">Notes </span><span class="sxs-lookup"><span data-stu-id="8f6e2-117">Remarks</span></span>  
 <span data-ttu-id="8f6e2-118">L’API métadonnées garantit de maintenir des méthodes dans le même ordre que l’appelant les `td` émet pour une classe ou une interface fermée, qui est spécifiée dans le paramètre.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="8f6e2-119">Des informations supplémentaires `DefineMethod` concernant l’utilisation et des paramètres particuliers sont données ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="8f6e2-120">Machines à sous dans la table en V</span><span class="sxs-lookup"><span data-stu-id="8f6e2-120">Slots in the V-table</span></span>  
 <span data-ttu-id="8f6e2-121">Le temps d’exécution utilise des définitions de méthode pour configurer des emplacements v-table.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="8f6e2-122">Dans le cas où une ou plusieurs fentes doivent être ignorées, par exemple pour préserver la parité avec une disposition d’interface COM, une méthode factice est définie pour prendre la fente ou les fentes dans la table en v; définir `dwMethodFlags` la `mdRTSpecialName` valeur de l’énumération [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) et spécifier le nom comme:</span><span class="sxs-lookup"><span data-stu-id="8f6e2-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="8f6e2-123">\<_VtblGap>\<\_*SéquenceAumeurs\*\*DeSlots*></span><span class="sxs-lookup"><span data-stu-id="8f6e2-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="8f6e2-124">où *SequenceNumber* est le numéro de séquence de la méthode et *CountOfSlots* est le nombre de fentes à sauter dans la table en v.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="8f6e2-125">Si *CountOfSlots* est omis, 1 est supposé.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="8f6e2-126">Ces méthodes factices ne sont pas callables à partir de code géré ou non géré et toute tentative de les appeler, à partir de code géré ou non géré, génère une exception.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="8f6e2-127">Leur seul but est de prendre de l’espace dans la table en v que le temps d’exécution génère pour l’intégration COM.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="8f6e2-128">Méthodes dupliqué</span><span class="sxs-lookup"><span data-stu-id="8f6e2-128">Duplicate Methods</span></span>  
 <span data-ttu-id="8f6e2-129">Vous ne devez pas définir les méthodes en double.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-129">You should not define duplicate methods.</span></span> <span data-ttu-id="8f6e2-130">Autrement dit, vous `DefineMethod` ne devriez pas appeler `td`avec `wzName`un `pvSig` ensemble de valeurs en double dans le , , et les paramètres.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="8f6e2-131">(Ces trois paramètres ensemble définissent uniquement la méthode.).</span><span class="sxs-lookup"><span data-stu-id="8f6e2-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="8f6e2-132">Cependant, vous pouvez utiliser un triple en double à condition que, pour l’une des définitions de la méthode, vous définissez le `mdPrivateScope` bit dans le `dwMethodFlags` paramètre.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="8f6e2-133">(Le `mdPrivateScope` bit signifie que le compilateur n’émettra pas de référence à cette définition de méthode.)</span><span class="sxs-lookup"><span data-stu-id="8f6e2-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="8f6e2-134">Informations sur la mise en œuvre de la méthode</span><span class="sxs-lookup"><span data-stu-id="8f6e2-134">Method Implementation Information</span></span>  
 <span data-ttu-id="8f6e2-135">L’information sur la mise en œuvre de la méthode n’est souvent pas connue au moment où la méthode est déclarée.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="8f6e2-136">Par conséquent, vous n’avez pas `ulCodeRVA` `dwImplFlags` besoin de `DefineMethod`passer des valeurs dans le et les paramètres lors de l’appel .</span><span class="sxs-lookup"><span data-stu-id="8f6e2-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="8f6e2-137">Les valeurs peuvent être fournies plus tard par [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="8f6e2-138">Dans certaines situations, telles que l’invocation de la plate-forme (PInvoke) `ulCodeRVA` ou les scénarios d’interop COM, le corps de méthode ne sera pas fourni, et doit être réglé à zéro.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="8f6e2-139">Dans ces situations, la méthode ne doit pas être étiquetée comme abstraite, car le temps d’exécution localisera la mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="8f6e2-140">Définir une méthode pour PInvoke</span><span class="sxs-lookup"><span data-stu-id="8f6e2-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="8f6e2-141">Pour que chaque fonction non gérée soit appelée par PInvoke, vous devez définir une méthode gérée qui représente la fonction cible non gérée.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="8f6e2-142">Pour définir la méthode `DefineMethod` gérée, utilisez avec certains des paramètres définis à certaines valeurs, selon la façon dont PInvoke est utilisé :</span><span class="sxs-lookup"><span data-stu-id="8f6e2-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="8f6e2-143">Vrai PInvoke - implique l’invocation d’une méthode externe non gestion qui réside dans un DLL non gestion.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="8f6e2-144">PInvoke local - implique l’invocation d’une méthode indigène non gérée qui est intégré dans le module géré actuel.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="8f6e2-145">Les paramètres sont donnés dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="8f6e2-146">Paramètre</span><span class="sxs-lookup"><span data-stu-id="8f6e2-146">Parameter</span></span>|<span data-ttu-id="8f6e2-147">Valeurs pour le vrai PInvoke</span><span class="sxs-lookup"><span data-stu-id="8f6e2-147">Values for true PInvoke</span></span>|<span data-ttu-id="8f6e2-148">Valeurs pour PInvoke local</span><span class="sxs-lookup"><span data-stu-id="8f6e2-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="8f6e2-149">Ensemble `mdStatic`; clair `mdSynchronized` `mdAbstract`et .</span><span class="sxs-lookup"><span data-stu-id="8f6e2-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="8f6e2-150">Une signature valide de méthode de course de langue commune (CLR) avec des paramètres qui sont des types gérés valides.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="8f6e2-151">Une signature de méthode CLR valide avec des paramètres qui sont valides types gérés.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="8f6e2-152">0</span><span class="sxs-lookup"><span data-stu-id="8f6e2-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="8f6e2-153">Définissez `miCil` et `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="8f6e2-154">Définissez `miNative` et `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f6e2-155">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8f6e2-155">Requirements</span></span>  
 <span data-ttu-id="8f6e2-156">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f6e2-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f6e2-157">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="8f6e2-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8f6e2-158">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8f6e2-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f6e2-159">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f6e2-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f6e2-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f6e2-160">See also</span></span>

- [<span data-ttu-id="8f6e2-161">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="8f6e2-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8f6e2-162">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="8f6e2-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
