---
title: IAppIdAuthority, interface
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
ms.openlocfilehash: a344f2ab5d9a7aa92018c47ee7a162cd1721aeb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732110"
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="b73ea-102">IAppIdAuthority, interface</span><span class="sxs-lookup"><span data-stu-id="b73ea-102">IAppIdAuthority Interface</span></span>

<span data-ttu-id="b73ea-103">Fournit des méthodes qui génèrent et comparent des clés pour les identités et les références d’application.</span><span class="sxs-lookup"><span data-stu-id="b73ea-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b73ea-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b73ea-104">Methods</span></span>  
  
|<span data-ttu-id="b73ea-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b73ea-105">Method</span></span>|<span data-ttu-id="b73ea-106">Description</span><span class="sxs-lookup"><span data-stu-id="b73ea-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="b73ea-107">Obtient une valeur qui indique si les deux instances [IDefinitionAppId](idefinitionappid-interface.md) spécifiées sont égales.</span><span class="sxs-lookup"><span data-stu-id="b73ea-107">Gets a value that indicates whether the two specified [IDefinitionAppId](idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="b73ea-108">Vous pouvez passer la valeur de l’indicateur IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.</span><span class="sxs-lookup"><span data-stu-id="b73ea-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="b73ea-109">Obtient une valeur qui indique si les deux instances [IReferenceAppId](ireferenceappid-interface.md) spécifiées sont égales.</span><span class="sxs-lookup"><span data-stu-id="b73ea-109">Gets a value that indicates whether the two specified [IReferenceAppId](ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="b73ea-110">Vous pouvez passer la valeur de l’indicateur IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.</span><span class="sxs-lookup"><span data-stu-id="b73ea-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="b73ea-111">Obtient une valeur qui indique si les deux définitions de chaîne spécifiées sont égales.</span><span class="sxs-lookup"><span data-stu-id="b73ea-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="b73ea-112">Vous pouvez passer la valeur de l’indicateur IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.</span><span class="sxs-lookup"><span data-stu-id="b73ea-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="b73ea-113">Obtient une valeur qui indique si les deux références de chaîne spécifiées sont égales.</span><span class="sxs-lookup"><span data-stu-id="b73ea-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="b73ea-114">Vous pouvez passer la valeur de l’indicateur IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.</span><span class="sxs-lookup"><span data-stu-id="b73ea-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="b73ea-115">Obtient un pointeur d’interface vers une instance nouvellement générée `IDefinitionAppId` qui représente l’assembly dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="b73ea-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="b73ea-116">Obtient un pointeur d’interface vers un objet qui vient d’être créé `IReferenceAppId` et qui représente l’assembly dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="b73ea-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="b73ea-117">Obtient une version de chaîne du spécifié `IDefinitionAppId` , à l’aide des valeurs d’indicateur spécifiées.</span><span class="sxs-lookup"><span data-stu-id="b73ea-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="b73ea-118">Obtient une valeur qui indique si le spécifié `IDefinitionAppId` et `IReferenceAppId` représente le même assembly.</span><span class="sxs-lookup"><span data-stu-id="b73ea-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="b73ea-119">Obtient une valeur qui indique si la chaîne de définition et la chaîne de référence spécifiées représentent le même assembly.</span><span class="sxs-lookup"><span data-stu-id="b73ea-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="b73ea-120">Obtient une clé de chaîne qui représente l' `IDefinitionAppId` instance spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b73ea-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="b73ea-121">Obtient une clé de chaîne qui représente l' `IReferenceAppId` instance spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b73ea-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="b73ea-122">Obtient une clé de hachage pour l' `IDefinitionAppId` instance spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b73ea-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="b73ea-123">Obtient une clé de hachage pour l' `IReferenceAppId` instance spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b73ea-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="b73ea-124">Obtient une version de chaîne du spécifié `IReferenceAppId` , à l’aide des valeurs d’indicateur spécifiées.</span><span class="sxs-lookup"><span data-stu-id="b73ea-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="b73ea-125">Obtient un pointeur d’interface vers une `IDefinitionAppId` instance de qui représente l’assembly référencé par la clé de chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b73ea-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="b73ea-126">Obtient un pointeur d’interface vers une `IReferenceAppId` instance de qui représente l’assembly référencé par la clé de chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b73ea-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b73ea-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b73ea-127">Requirements</span></span>  

 <span data-ttu-id="b73ea-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b73ea-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b73ea-129">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="b73ea-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b73ea-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b73ea-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b73ea-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b73ea-131">See also</span></span>

- [<span data-ttu-id="b73ea-132">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="b73ea-132">Fusion Interfaces</span></span>](fusion-interfaces.md)
