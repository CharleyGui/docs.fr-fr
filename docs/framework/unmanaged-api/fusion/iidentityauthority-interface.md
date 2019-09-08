---
title: IIdentityAuthority, interface
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7421e0d0e1a1f0e1a5fbe0d0eb7d5a0ab2a48b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796420"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="f2a30-102">IIdentityAuthority, interface</span><span class="sxs-lookup"><span data-stu-id="f2a30-102">IIdentityAuthority Interface</span></span>

<span data-ttu-id="f2a30-103">Gère les clés d’identité pour les objets de code.</span><span class="sxs-lookup"><span data-stu-id="f2a30-103">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="f2a30-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f2a30-104">Methods</span></span>

|<span data-ttu-id="f2a30-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f2a30-105">Method</span></span>|<span data-ttu-id="f2a30-106">Description</span><span class="sxs-lookup"><span data-stu-id="f2a30-106">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="f2a30-107">Obtient une valeur qui indique si les deux instances de [IDefinitionIdentity](idefinitionidentity-interface.md) spécifiées sont égales.</span><span class="sxs-lookup"><span data-stu-id="f2a30-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="f2a30-108">Obtient une valeur qui indique si les deux instances [IReferenceIdentity](ireferenceidentity-interface.md) spécifiées sont égales.</span><span class="sxs-lookup"><span data-stu-id="f2a30-108">Gets a value that indicates whether the two specified [IReferenceIdentity](ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="f2a30-109">Obtient une valeur qui indique si les deux représentations d’identité de définition de chaîne spécifiées sont égales.</span><span class="sxs-lookup"><span data-stu-id="f2a30-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="f2a30-110">Obtient une valeur qui indique si les deux représentations d’identité de référence de chaîne spécifiées sont égales.</span><span class="sxs-lookup"><span data-stu-id="f2a30-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="f2a30-111">Obtient un pointeur vers une nouvelle `IDefinitionIdentity` instance de qui représente l’objet de code dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="f2a30-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="f2a30-112">Obtient un pointeur vers une nouvelle `IReferenceIdentity` instance de qui représente l’objet de code dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="f2a30-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="f2a30-113">Obtient une version de chaîne mise en forme `IDefinitionIdentity`du spécifié.</span><span class="sxs-lookup"><span data-stu-id="f2a30-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="f2a30-114">Remplit la mémoire tampon de caractères larges spécifiée avec une version de chaîne du `IDefinitionIdentity`spécifié.</span><span class="sxs-lookup"><span data-stu-id="f2a30-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="f2a30-115">Obtient une valeur qui indique si les instances `IDefinitionIdentity` et `IReferenceIdentity` spécifiées font référence au même objet de code.</span><span class="sxs-lookup"><span data-stu-id="f2a30-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="f2a30-116">Obtient une valeur qui indique si les chaînes spécifiées font référence au même objet de code.</span><span class="sxs-lookup"><span data-stu-id="f2a30-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="f2a30-117">Obtient un pointeur vers une clé de chaîne nouvellement créée pour le `IDefinitionIdentity`spécifié.</span><span class="sxs-lookup"><span data-stu-id="f2a30-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="f2a30-118">Obtient un pointeur vers une clé de chaîne nouvellement créée pour le `IReferenceIdentity`spécifié.</span><span class="sxs-lookup"><span data-stu-id="f2a30-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="f2a30-119">Obtient une valeur de hachage pour le `IDefinitionIdentity`spécifié.</span><span class="sxs-lookup"><span data-stu-id="f2a30-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="f2a30-120">Obtient une valeur de hachage pour le `IReferenceIdentity`spécifié.</span><span class="sxs-lookup"><span data-stu-id="f2a30-120">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="f2a30-121">Obtient une version de chaîne mise en forme `IReferenceIdentity`du spécifié.</span><span class="sxs-lookup"><span data-stu-id="f2a30-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="f2a30-122">Remplit la mémoire tampon de caractères larges spécifiée avec une version de chaîne du `IReferenceIdentity`spécifié.</span><span class="sxs-lookup"><span data-stu-id="f2a30-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="f2a30-123">Obtient un pointeur d’interface vers `IDefinitionIdentity` une instance générée à partir de la chaîne mise en forme spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f2a30-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="f2a30-124">Obtient un pointeur d’interface vers `IReferenceIdentity` une instance générée à partir de la chaîne mise en forme spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f2a30-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="f2a30-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f2a30-125">Requirements</span></span>

<span data-ttu-id="f2a30-126">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2a30-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f2a30-127">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="f2a30-127">**Header:** Isolation.h</span></span>

<span data-ttu-id="f2a30-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2a30-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f2a30-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2a30-129">See also</span></span>

- [<span data-ttu-id="f2a30-130">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="f2a30-130">Fusion Interfaces</span></span>](fusion-interfaces.md)
