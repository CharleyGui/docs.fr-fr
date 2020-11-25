---
title: CompareAssemblyIdentity, fonction
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
ms.openlocfilehash: da32ce6a40378a6f88cf71bd7707be2079d71068
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717589"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="20874-102">CompareAssemblyIdentity, fonction</span><span class="sxs-lookup"><span data-stu-id="20874-102">CompareAssemblyIdentity Function</span></span>

<span data-ttu-id="20874-103">Compare deux identités d’assembly pour déterminer si elles sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="20874-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20874-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20874-104">Syntax</span></span>  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="20874-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="20874-105">Parameters</span></span>  

 `pwzAssemblyIdentity1`  
 <span data-ttu-id="20874-106">dans Identité textuelle du premier assembly dans la comparaison.</span><span class="sxs-lookup"><span data-stu-id="20874-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="20874-107">dans Indicateur booléen qui indique l’unification spécifiée par l’utilisateur pour `pwzAssemblyIdentity1` .</span><span class="sxs-lookup"><span data-stu-id="20874-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="20874-108">dans Identité textuelle du deuxième assembly dans la comparaison.</span><span class="sxs-lookup"><span data-stu-id="20874-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="20874-109">dans Indicateur booléen qui indique l’unification spécifiée par l’utilisateur pour `pwzAssemblyIdentity2` .</span><span class="sxs-lookup"><span data-stu-id="20874-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="20874-110">à Indicateur booléen qui indique si les deux assemblys sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="20874-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="20874-111">à Énumération [AssemblyComparisonResult,](assemblycomparisonresult-enumeration.md) qui contient des informations détaillées sur la comparaison.</span><span class="sxs-lookup"><span data-stu-id="20874-111">[out] An [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20874-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="20874-112">Return Value</span></span>  

 <span data-ttu-id="20874-113">`pfEquivalent` retourne une valeur booléenne qui indique si les deux assemblys sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="20874-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="20874-114">`pResult` retourne l’une des `AssemblyComparisonResult` valeurs, pour fournir une raison plus détaillée de la valeur de `pfEquivalent` .</span><span class="sxs-lookup"><span data-stu-id="20874-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20874-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="20874-115">Remarks</span></span>  

 <span data-ttu-id="20874-116">`CompareAssemblyIdentity` vérifie si `pwzAssemblyIdentity1` et `pwzAssemblyIdentity2` sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="20874-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="20874-117">`pfEquivalent` a la valeur `true` dans une ou plusieurs des conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="20874-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
- <span data-ttu-id="20874-118">Les deux identités d’assembly sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="20874-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="20874-119">Pour les assemblys avec nom fort, l’équivalence exige que le nom de l’assembly, la version, le jeton de clé publique et la culture soient identiques.</span><span class="sxs-lookup"><span data-stu-id="20874-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="20874-120">Pour les assemblys simplement nommés, l’équivalence requiert une correspondance sur le nom et la culture de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="20874-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
- <span data-ttu-id="20874-121">Les deux identités d’assembly font référence aux assemblys qui s’exécutent sur le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="20874-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="20874-122">Cette condition retourne `true` même si les numéros de version de l’assembly ne correspondent pas.</span><span class="sxs-lookup"><span data-stu-id="20874-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
- <span data-ttu-id="20874-123">Les deux assemblys ne sont pas des assemblys managés, mais `fUnified1` ou `fUnified2` ont la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="20874-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="20874-124">L' `fUnified` indicateur indique que tous les numéros de version jusqu’au numéro de version de l’assembly avec nom fort sont considérés comme équivalents à l’assembly avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="20874-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="20874-125">Par exemple, si la valeur de `pwzAssemblyIndentity1` est « myAssembly, version = 3.0.0.0, culture = neutral, PublicKeyToken =.... » et que la valeur de `fUnified1` est `true` , cela indique que toutes les versions de MyAssembly de la version 0.0.0.0 à 3.0.0.0 doivent être traitées comme équivalentes.</span><span class="sxs-lookup"><span data-stu-id="20874-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="20874-126">Dans ce cas, si `pwzAssemblyIndentity2` fait référence au même assembly que `pwzAssemblyIndentity1` , sauf qu’il a un numéro de version inférieur, `pfEquivalent` a la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="20874-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="20874-127">Si `pwzAssemblyIdentity2` fait référence à un numéro de version plus élevé, `pfEquivalent` est défini sur `true` uniquement si la valeur de `fUnified2` est `true` .</span><span class="sxs-lookup"><span data-stu-id="20874-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="20874-128">Le `pResult` paramètre contient des informations spécifiques sur la raison pour laquelle les deux assemblys sont considérés comme équivalents ou non équivalents.</span><span class="sxs-lookup"><span data-stu-id="20874-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="20874-129">Pour plus d’informations, consultez [énumération AssemblyComparisonResult,](assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="20874-129">For more information, see [AssemblyComparisonResult Enumeration](assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20874-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="20874-130">Requirements</span></span>  

 <span data-ttu-id="20874-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20874-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20874-132">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="20874-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="20874-133">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20874-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="20874-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20874-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20874-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20874-135">See also</span></span>

- [<span data-ttu-id="20874-136">Fonctions statiques globales de la fusion</span><span class="sxs-lookup"><span data-stu-id="20874-136">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="20874-137">AssemblyComparisonResult, énumération</span><span class="sxs-lookup"><span data-stu-id="20874-137">AssemblyComparisonResult Enumeration</span></span>](assemblycomparisonresult-enumeration.md)
