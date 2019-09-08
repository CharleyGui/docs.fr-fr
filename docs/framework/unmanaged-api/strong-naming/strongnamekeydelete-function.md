---
title: StrongNameKeyDelete, fonction
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17d35193f69966e02ac5e483924fcb3ee2e06758
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799018"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="a457d-102">StrongNameKeyDelete, fonction</span><span class="sxs-lookup"><span data-stu-id="a457d-102">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="a457d-103">Supprime le conteneur de clé spécifié.</span><span class="sxs-lookup"><span data-stu-id="a457d-103">Deletes the specified key container.</span></span>

<span data-ttu-id="a457d-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="a457d-104">This function has been deprecated.</span></span> <span data-ttu-id="a457d-105">Utilisez la méthode [ICLRStrongName :: StrongNameKeyDelete (](../hosting/iclrstrongname-strongnamekeydelete-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="a457d-105">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="a457d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a457d-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="a457d-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a457d-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="a457d-108">dans Nom du conteneur de clé à supprimer.</span><span class="sxs-lookup"><span data-stu-id="a457d-108">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="a457d-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a457d-109">Return Value</span></span>

<span data-ttu-id="a457d-110">`true`en cas de réussite de l’opération ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="a457d-110">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="a457d-111">Notes</span><span class="sxs-lookup"><span data-stu-id="a457d-111">Remarks</span></span>

<span data-ttu-id="a457d-112">Utilisez la fonction [StrongNameKeyInstall](strongnamekeyinstall-function.md) pour importer une paire de clés publique/privée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="a457d-112">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="a457d-113">Si la `StrongNameKeyDelete` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="a457d-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="a457d-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a457d-114">Requirements</span></span>

<span data-ttu-id="a457d-115">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a457d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a457d-116">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a457d-116">**Header:** StrongName.h</span></span>

<span data-ttu-id="a457d-117">**Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a457d-117">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="a457d-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a457d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a457d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a457d-119">See also</span></span>

- [<span data-ttu-id="a457d-120">StrongNameKeyDelete, méthode</span><span class="sxs-lookup"><span data-stu-id="a457d-120">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="a457d-121">StrongNameKeyInstall, méthode</span><span class="sxs-lookup"><span data-stu-id="a457d-121">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="a457d-122">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="a457d-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
