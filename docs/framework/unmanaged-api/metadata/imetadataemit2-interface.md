---
title: IMetaDataEmit2, interface
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
ms.openlocfilehash: 5a232f30da8812c6f3bd94647d74151312a8593b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493035"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="37b25-102">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="37b25-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="37b25-103">Étend l’interface [IMetaDataEmit](imetadataemit-interface.md) principalement pour offrir la possibilité d’utiliser des types génériques.</span><span class="sxs-lookup"><span data-stu-id="37b25-103">Extends the [IMetaDataEmit](imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37b25-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="37b25-104">Methods</span></span>  
  
|<span data-ttu-id="37b25-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="37b25-105">Method</span></span>|<span data-ttu-id="37b25-106">Description</span><span class="sxs-lookup"><span data-stu-id="37b25-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37b25-107">DefineGenericParam, méthode</span><span class="sxs-lookup"><span data-stu-id="37b25-107">DefineGenericParam Method</span></span>](imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="37b25-108">Crée une définition pour un paramètre de type générique et obtient un jeton pour ce paramètre de type générique.</span><span class="sxs-lookup"><span data-stu-id="37b25-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="37b25-109">DefineMethodSpec, méthode</span><span class="sxs-lookup"><span data-stu-id="37b25-109">DefineMethodSpec Method</span></span>](imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="37b25-110">Crée une instance générique d’une méthode et obtient un jeton pour la définition.</span><span class="sxs-lookup"><span data-stu-id="37b25-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="37b25-111">GetDeltaSaveSize, méthode</span><span class="sxs-lookup"><span data-stu-id="37b25-111">GetDeltaSaveSize Method</span></span>](imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="37b25-112">Obtient une valeur qui indique la différence de taille des données requises pour exprimer les modifications de la session de modification et de continuation en cours.</span><span class="sxs-lookup"><span data-stu-id="37b25-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="37b25-113">ResetENCLog, méthode</span><span class="sxs-lookup"><span data-stu-id="37b25-113">ResetENCLog Method</span></span>](imetadataemit2-resetenclog-method.md)|<span data-ttu-id="37b25-114">Réinitialise le journal Edit-and-continue et démarre une nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="37b25-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="37b25-115">SaveDelta, méthode</span><span class="sxs-lookup"><span data-stu-id="37b25-115">SaveDelta Method</span></span>](imetadataemit2-savedelta-method.md)|<span data-ttu-id="37b25-116">Enregistre les modifications de la session de modification et de poursuite en cours dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="37b25-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="37b25-117">SaveDeltaToMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="37b25-117">SaveDeltaToMemory Method</span></span>](imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="37b25-118">Enregistre les modifications de la session en cours de modification et de continuation dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="37b25-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="37b25-119">SaveDeltaToStream, méthode</span><span class="sxs-lookup"><span data-stu-id="37b25-119">SaveDeltaToStream Method</span></span>](imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="37b25-120">Enregistre les modifications de la session de modification et de continuation actuelle dans le flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="37b25-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="37b25-121">SetGenericParamProps, méthode</span><span class="sxs-lookup"><span data-stu-id="37b25-121">SetGenericParamProps Method</span></span>](imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="37b25-122">Définit des valeurs de propriété pour la définition de paramètre générique référencée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="37b25-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37b25-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="37b25-123">Requirements</span></span>  
 <span data-ttu-id="37b25-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37b25-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37b25-125">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="37b25-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37b25-126">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="37b25-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37b25-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37b25-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37b25-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37b25-128">See also</span></span>

- [<span data-ttu-id="37b25-129">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="37b25-129">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="37b25-130">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="37b25-130">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
