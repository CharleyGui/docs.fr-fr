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
ms.openlocfilehash: 717d2104db8addf40e5187cee4cc8c46e5dc355e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636739"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="bd0ec-102">StrongNameKeyDelete, fonction</span><span class="sxs-lookup"><span data-stu-id="bd0ec-102">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="bd0ec-103">Supprime le conteneur de clé spécifié.</span><span class="sxs-lookup"><span data-stu-id="bd0ec-103">Deletes the specified key container.</span></span>

<span data-ttu-id="bd0ec-104">Cette fonction a été déconseillée.</span><span class="sxs-lookup"><span data-stu-id="bd0ec-104">This function has been deprecated.</span></span> <span data-ttu-id="bd0ec-105">Utilisez le [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="bd0ec-105">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="bd0ec-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd0ec-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="bd0ec-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bd0ec-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="bd0ec-108">[in] Le nom du conteneur de clé à supprimer.</span><span class="sxs-lookup"><span data-stu-id="bd0ec-108">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="bd0ec-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bd0ec-109">Return Value</span></span>

<span data-ttu-id="bd0ec-110">`true` de réussite ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="bd0ec-110">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd0ec-111">Notes</span><span class="sxs-lookup"><span data-stu-id="bd0ec-111">Remarks</span></span>

<span data-ttu-id="bd0ec-112">Utilisez le [StrongNameKeyInstall](strongnamekeyinstall-function.md) (fonction) pour importer une paire de clés publique/privée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="bd0ec-112">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="bd0ec-113">Si le `StrongNameKeyDelete` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="bd0ec-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="bd0ec-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bd0ec-114">Requirements</span></span>

<span data-ttu-id="bd0ec-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd0ec-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="bd0ec-116">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="bd0ec-116">**Header:** StrongName.h</span></span>

<span data-ttu-id="bd0ec-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd0ec-117">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="bd0ec-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd0ec-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bd0ec-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd0ec-119">See also</span></span>

- [<span data-ttu-id="bd0ec-120">StrongNameKeyDelete, méthode</span><span class="sxs-lookup"><span data-stu-id="bd0ec-120">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="bd0ec-121">StrongNameKeyInstall, méthode</span><span class="sxs-lookup"><span data-stu-id="bd0ec-121">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="bd0ec-122">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="bd0ec-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
