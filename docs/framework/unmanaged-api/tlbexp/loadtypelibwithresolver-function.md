---
title: LoadTypeLibWithResolver, fonction
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
ms.openlocfilehash: 395d5f63eef12570c07f1f601de7f9e480d62905
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540503"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="8a980-102">LoadTypeLibWithResolver, fonction</span><span class="sxs-lookup"><span data-stu-id="8a980-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="8a980-103">Charge une bibliothèque de types et utilise l' [interface ITypeLibResolver](itypelibresolver-interface.md) fournie pour résoudre toutes les bibliothèques de types référencées en interne.</span><span class="sxs-lookup"><span data-stu-id="8a980-103">Loads a type library and uses the supplied [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a980-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a980-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a980-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a980-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="8a980-106">dans Chemin d’accès de fichier de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="8a980-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="8a980-107">dans Indicateur d' [énumération REGKIND](/windows/win32/api/oleauto/ne-oleauto-regkind) qui contrôle la façon dont la bibliothèque de types est inscrite.</span><span class="sxs-lookup"><span data-stu-id="8a980-107">[in] A [REGKIND enumeration](/windows/win32/api/oleauto/ne-oleauto-regkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="8a980-108">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a980-108">Its possible values are:</span></span>  
  
- <span data-ttu-id="8a980-109">`REGKIND_DEFAULT`: Utilisez le comportement d’inscription par défaut.</span><span class="sxs-lookup"><span data-stu-id="8a980-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
- <span data-ttu-id="8a980-110">`REGKIND_REGISTER`: Inscrivez cette bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="8a980-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
- <span data-ttu-id="8a980-111">`REGKIND_NONE`: N’inscrivez pas cette bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="8a980-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="8a980-112">dans Pointeur vers l’implémentation de l' [interface ITypeLibResolver](itypelibresolver-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8a980-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="8a980-113">à Référence à la bibliothèque de types en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="8a980-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a980-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8a980-114">Return Value</span></span>  
 <span data-ttu-id="8a980-115">L’une des valeurs HRESULT indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="8a980-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="8a980-116">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="8a980-116">Return value</span></span>|<span data-ttu-id="8a980-117">Signification</span><span class="sxs-lookup"><span data-stu-id="8a980-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="8a980-118">Opération réussie.</span><span class="sxs-lookup"><span data-stu-id="8a980-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="8a980-119">Mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="8a980-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="8a980-120">Un ou plusieurs pointeurs ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="8a980-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="8a980-121">Un ou plusieurs arguments ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="8a980-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="8a980-122">La fonction n’a pas pu écrire dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="8a980-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="8a980-123">Impossible d’ouvrir la base de données d’inscription du système.</span><span class="sxs-lookup"><span data-stu-id="8a980-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="8a980-124">Impossible d’ouvrir la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="8a980-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="8a980-125">La bibliothèque de types ou la DLL n’a pas pu être chargée.</span><span class="sxs-lookup"><span data-stu-id="8a980-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a980-126">Notes</span><span class="sxs-lookup"><span data-stu-id="8a980-126">Remarks</span></span>  
 <span data-ttu-id="8a980-127">Le [Tlbexp.exe (exportateur de bibliothèques de types)](../../tools/tlbexp-exe-type-library-exporter.md) appelle la `LoadTypeLibWithResolver` fonction pendant le processus de conversion d’assembly en bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="8a980-127">The [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="8a980-128">Cette fonction charge la bibliothèque de types spécifiée avec un accès minimal au registre.</span><span class="sxs-lookup"><span data-stu-id="8a980-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="8a980-129">La fonction examine ensuite la bibliothèque de types pour les bibliothèques de types référencées en interne, chacune d’elles devant être chargée et ajoutée à la bibliothèque de types parente.</span><span class="sxs-lookup"><span data-stu-id="8a980-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="8a980-130">Pour pouvoir charger une bibliothèque de types référencée, son chemin d’accès au fichier de référence doit être résolu en chemin d’accès complet au fichier.</span><span class="sxs-lookup"><span data-stu-id="8a980-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="8a980-131">Pour ce faire, vous devez utiliser la [méthode ResolveTypeLib (](resolvetypelib-method.md) fournie par l' [interface ITypeLibResolver](itypelibresolver-interface.md), qui est transmise dans le `pTlbResolver` paramètre.</span><span class="sxs-lookup"><span data-stu-id="8a980-131">This is accomplished through the [ResolveTypeLib method](resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="8a980-132">Lorsque le chemin de fichier complet de la bibliothèque de types référencée est connu, la `LoadTypeLibWithResolver` fonction se charge et ajoute la bibliothèque de types référencée à la bibliothèque de types parente, en créant une bibliothèque de types principaux combinée.</span><span class="sxs-lookup"><span data-stu-id="8a980-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="8a980-133">Une fois que la fonction a résolu et chargé toutes les bibliothèques de types référencées en interne, elle retourne une référence à la bibliothèque de types résolue principale dans le `pptlib` paramètre.</span><span class="sxs-lookup"><span data-stu-id="8a980-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="8a980-134">La `LoadTypeLibWithResolver` fonction est généralement appelée par le [Tlbexp.exe (exportateur de bibliothèques de types)](../../tools/tlbexp-exe-type-library-exporter.md), qui fournit sa propre implémentation d' [interface ITypeLibResolver](itypelibresolver-interface.md) interne dans le `pTlbResolver` paramètre.</span><span class="sxs-lookup"><span data-stu-id="8a980-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="8a980-135">Si vous appelez `LoadTypeLibWithResolver` directement, vous devez fournir votre propre implémentation d' [interface ITypeLibResolver](itypelibresolver-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8a980-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a980-136">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8a980-136">Requirements</span></span>  
 <span data-ttu-id="8a980-137">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a980-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a980-138">**En-tête :** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="8a980-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="8a980-139">**Bibliothèque :** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="8a980-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="8a980-140">**Version de .NET Framework :** 3,5, 3,0, 2,0</span><span class="sxs-lookup"><span data-stu-id="8a980-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a980-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a980-141">See also</span></span>

- [<span data-ttu-id="8a980-142">Fonctions d’assistance Tlbexp</span><span class="sxs-lookup"><span data-stu-id="8a980-142">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="8a980-143">LoadTypeLibEx fonction)</span><span class="sxs-lookup"><span data-stu-id="8a980-143">LoadTypeLibEx Function</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
