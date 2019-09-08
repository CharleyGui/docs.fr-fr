---
title: StrongNameKeyInstall, fonction
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 353898b72f41acd0c49a43ff05e54f61b99444c4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798992"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="64eaf-102">StrongNameKeyInstall, fonction</span><span class="sxs-lookup"><span data-stu-id="64eaf-102">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="64eaf-103">Importe une paire de clés publique/privée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="64eaf-103">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="64eaf-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="64eaf-104">This function has been deprecated.</span></span> <span data-ttu-id="64eaf-105">Utilisez la méthode [ICLRStrongName :: StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="64eaf-105">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="64eaf-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64eaf-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="64eaf-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="64eaf-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="64eaf-108">dans Nom du conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="64eaf-108">[in] The name of the key container.</span></span> <span data-ttu-id="64eaf-109">`wszKeyContainer`doit être une chaîne non vide.</span><span class="sxs-lookup"><span data-stu-id="64eaf-109">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="64eaf-110">dans Paire de clés binaires.</span><span class="sxs-lookup"><span data-stu-id="64eaf-110">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="64eaf-111">dans Taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="64eaf-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="64eaf-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="64eaf-112">Return Value</span></span>

<span data-ttu-id="64eaf-113">`true`en cas de réussite de l’opération ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="64eaf-113">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="64eaf-114">Notes</span><span class="sxs-lookup"><span data-stu-id="64eaf-114">Remarks</span></span>

<span data-ttu-id="64eaf-115">Utilisez la fonction [StrongNameKeyDelete (](strongnamekeydelete-function.md) pour supprimer le conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="64eaf-115">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="64eaf-116">Si la `StrongNameKeyInstall` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="64eaf-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="64eaf-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="64eaf-117">Requirements</span></span>

<span data-ttu-id="64eaf-118">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64eaf-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="64eaf-119">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="64eaf-119">**Header:** StrongName.h</span></span>

<span data-ttu-id="64eaf-120">**Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="64eaf-120">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="64eaf-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64eaf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="64eaf-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64eaf-122">See also</span></span>

- [<span data-ttu-id="64eaf-123">StrongNameKeyInstall, méthode</span><span class="sxs-lookup"><span data-stu-id="64eaf-123">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="64eaf-124">StrongNameKeyDelete, méthode</span><span class="sxs-lookup"><span data-stu-id="64eaf-124">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="64eaf-125">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="64eaf-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
