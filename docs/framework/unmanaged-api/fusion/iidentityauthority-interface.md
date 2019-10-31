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
ms.openlocfilehash: 3e2d2335e37ced9139ea44092f10b19566894681
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127097"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="b2dab-102">IIdentityAuthority, interface</span><span class="sxs-lookup"><span data-stu-id="b2dab-102">IIdentityAuthority Interface</span></span>

<span data-ttu-id="b2dab-103">Gère les clés d’identité pour les objets de code.</span><span class="sxs-lookup"><span data-stu-id="b2dab-103">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="b2dab-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b2dab-104">Methods</span></span>

|<span data-ttu-id="b2dab-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b2dab-105">Method</span></span>|<span data-ttu-id="b2dab-106">Description</span><span class="sxs-lookup"><span data-stu-id="b2dab-106">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="b2dab-107">Obtient une valeur qui indique si les deux instances de [IDefinitionIdentity](idefinitionidentity-interface.md) spécifiées sont égales.</span><span class="sxs-lookup"><span data-stu-id="b2dab-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="b2dab-108">Obtient une valeur qui indique si les deux instances [IReferenceIdentity](ireferenceidentity-interface.md) spécifiées sont égales.</span><span class="sxs-lookup"><span data-stu-id="b2dab-108">Gets a value that indicates whether the two specified [IReferenceIdentity](ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="b2dab-109">Obtient une valeur qui indique si les deux représentations d’identité de définition de chaîne spécifiées sont égales.</span><span class="sxs-lookup"><span data-stu-id="b2dab-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="b2dab-110">Obtient une valeur qui indique si les deux représentations d’identité de référence de chaîne spécifiées sont égales.</span><span class="sxs-lookup"><span data-stu-id="b2dab-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="b2dab-111">Obtient un pointeur vers une nouvelle instance de `IDefinitionIdentity` qui représente l’objet de code dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="b2dab-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="b2dab-112">Obtient un pointeur vers une nouvelle instance de `IReferenceIdentity` qui représente l’objet de code dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="b2dab-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="b2dab-113">Obtient une version de chaîne mise en forme du `IDefinitionIdentity`spécifié.</span><span class="sxs-lookup"><span data-stu-id="b2dab-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="b2dab-114">Remplit la mémoire tampon de caractères larges spécifiée avec une version de chaîne du `IDefinitionIdentity`spécifié.</span><span class="sxs-lookup"><span data-stu-id="b2dab-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="b2dab-115">Obtient une valeur qui indique si le `IDefinitionIdentity` et les instances de `IReferenceIdentity` spécifiés font référence au même objet de code.</span><span class="sxs-lookup"><span data-stu-id="b2dab-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="b2dab-116">Obtient une valeur qui indique si les chaînes spécifiées font référence au même objet de code.</span><span class="sxs-lookup"><span data-stu-id="b2dab-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="b2dab-117">Obtient un pointeur vers une clé de chaîne nouvellement créée pour le `IDefinitionIdentity`spécifié.</span><span class="sxs-lookup"><span data-stu-id="b2dab-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="b2dab-118">Obtient un pointeur vers une clé de chaîne nouvellement créée pour le `IReferenceIdentity`spécifié.</span><span class="sxs-lookup"><span data-stu-id="b2dab-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="b2dab-119">Obtient une valeur de hachage pour le `IDefinitionIdentity`spécifié.</span><span class="sxs-lookup"><span data-stu-id="b2dab-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="b2dab-120">Obtient une valeur de hachage pour le `IReferenceIdentity`spécifié.</span><span class="sxs-lookup"><span data-stu-id="b2dab-120">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="b2dab-121">Obtient une version de chaîne mise en forme du `IReferenceIdentity`spécifié.</span><span class="sxs-lookup"><span data-stu-id="b2dab-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="b2dab-122">Remplit la mémoire tampon de caractères larges spécifiée avec une version de chaîne du `IReferenceIdentity`spécifié.</span><span class="sxs-lookup"><span data-stu-id="b2dab-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="b2dab-123">Obtient un pointeur d’interface vers une instance de `IDefinitionIdentity` générée à partir de la chaîne mise en forme spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b2dab-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="b2dab-124">Obtient un pointeur d’interface vers une instance de `IReferenceIdentity` générée à partir de la chaîne mise en forme spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b2dab-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="b2dab-125">spécifications</span><span class="sxs-lookup"><span data-stu-id="b2dab-125">Requirements</span></span>

<span data-ttu-id="b2dab-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2dab-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="b2dab-127">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="b2dab-127">**Header:** Isolation.h</span></span>

<span data-ttu-id="b2dab-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2dab-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b2dab-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2dab-129">See also</span></span>

- [<span data-ttu-id="b2dab-130">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="b2dab-130">Fusion Interfaces</span></span>](fusion-interfaces.md)
