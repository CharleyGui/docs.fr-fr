---
title: Événements de sécurité ETW
description: Comprendre les événements ETW de sécurité, qui sont déclenchés pendant la vérification de nom fort et la vérification Authenticode dans .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: 2fd2d450223cd16a7791b8f6c67afe6bcb954eb3
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474213"
---
# <a name="security-etw-events"></a><span data-ttu-id="95a25-103">Événements de sécurité ETW</span><span class="sxs-lookup"><span data-stu-id="95a25-103">Security ETW Events</span></span>

<span data-ttu-id="95a25-104">Les événements de sécurité sont déclenchés pendant la vérification de nom fort et la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="95a25-104">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="95a25-105">Événements StrongNameVerificationStart_V1 et StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="95a25-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="95a25-106">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="95a25-106">The following table shows the keyword and level.</span></span> <span data-ttu-id="95a25-107">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="95a25-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="95a25-108">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="95a25-108">Keyword for raising the event</span></span>|<span data-ttu-id="95a25-109">Level</span><span class="sxs-lookup"><span data-stu-id="95a25-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="95a25-110">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="95a25-110">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="95a25-111">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="95a25-111">Informational(4)</span></span>|  
  
 <span data-ttu-id="95a25-112">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="95a25-112">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="95a25-113">Événement</span><span class="sxs-lookup"><span data-stu-id="95a25-113">Event</span></span>|<span data-ttu-id="95a25-114">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="95a25-114">Event ID</span></span>|<span data-ttu-id="95a25-115">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="95a25-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="95a25-116">181</span><span class="sxs-lookup"><span data-stu-id="95a25-116">181</span></span>|<span data-ttu-id="95a25-117">Début de la vérification de nom fort.</span><span class="sxs-lookup"><span data-stu-id="95a25-117">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="95a25-118">182</span><span class="sxs-lookup"><span data-stu-id="95a25-118">182</span></span>|<span data-ttu-id="95a25-119">Fin de la vérification de nom fort.</span><span class="sxs-lookup"><span data-stu-id="95a25-119">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="95a25-120">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="95a25-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="95a25-121">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="95a25-121">Field name</span></span>|<span data-ttu-id="95a25-122">Type de données</span><span class="sxs-lookup"><span data-stu-id="95a25-122">Data type</span></span>|<span data-ttu-id="95a25-123">Description</span><span class="sxs-lookup"><span data-stu-id="95a25-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="95a25-124">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="95a25-124">VerificationFlags</span></span>|<span data-ttu-id="95a25-125">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="95a25-125">win:UInt32</span></span>|<span data-ttu-id="95a25-126">Indicateurs de vérification.</span><span class="sxs-lookup"><span data-stu-id="95a25-126">The verification flags.</span></span>|  
|<span data-ttu-id="95a25-127">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="95a25-127">ErrorCode</span></span>|<span data-ttu-id="95a25-128">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="95a25-128">win:UInt32</span></span>|<span data-ttu-id="95a25-129">Code d'erreur HResult.</span><span class="sxs-lookup"><span data-stu-id="95a25-129">The HResult error code.</span></span>|  
|<span data-ttu-id="95a25-130">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="95a25-130">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="95a25-131">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="95a25-131">win:UnicodeString</span></span>|<span data-ttu-id="95a25-132">Nom d'assembly qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="95a25-132">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="95a25-133">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="95a25-133">ClrInstanceID</span></span>|<span data-ttu-id="95a25-134">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="95a25-134">win:UInt16</span></span>|<span data-ttu-id="95a25-135">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="95a25-135">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="95a25-136">Événements AuthenticodeVerificationStart_V1 et AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="95a25-136">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="95a25-137">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="95a25-137">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="95a25-138">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="95a25-138">Keyword for raising the event</span></span>|<span data-ttu-id="95a25-139">Level</span><span class="sxs-lookup"><span data-stu-id="95a25-139">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="95a25-140">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="95a25-140">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="95a25-141">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="95a25-141">Informational(4)</span></span>|  
  
 <span data-ttu-id="95a25-142">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="95a25-142">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="95a25-143">Événement</span><span class="sxs-lookup"><span data-stu-id="95a25-143">Event</span></span>|<span data-ttu-id="95a25-144">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="95a25-144">Event ID</span></span>|<span data-ttu-id="95a25-145">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="95a25-145">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="95a25-146">183</span><span class="sxs-lookup"><span data-stu-id="95a25-146">183</span></span>|<span data-ttu-id="95a25-147">Début de la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="95a25-147">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="95a25-148">184</span><span class="sxs-lookup"><span data-stu-id="95a25-148">184</span></span>|<span data-ttu-id="95a25-149">Fin de la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="95a25-149">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="95a25-150">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="95a25-150">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="95a25-151">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="95a25-151">Field name</span></span>|<span data-ttu-id="95a25-152">Type de données</span><span class="sxs-lookup"><span data-stu-id="95a25-152">Data type</span></span>|<span data-ttu-id="95a25-153">Description</span><span class="sxs-lookup"><span data-stu-id="95a25-153">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="95a25-154">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="95a25-154">VerificationFlags</span></span>|<span data-ttu-id="95a25-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="95a25-155">win:UInt32</span></span>|<span data-ttu-id="95a25-156">Indicateurs de vérification.</span><span class="sxs-lookup"><span data-stu-id="95a25-156">The verification flags.</span></span>|  
|<span data-ttu-id="95a25-157">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="95a25-157">ErrorCode</span></span>|<span data-ttu-id="95a25-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="95a25-158">win:UInt32</span></span>|<span data-ttu-id="95a25-159">Code d'erreur HResult.</span><span class="sxs-lookup"><span data-stu-id="95a25-159">The HResult error code.</span></span>|  
|<span data-ttu-id="95a25-160">ModulePath</span><span class="sxs-lookup"><span data-stu-id="95a25-160">ModulePath</span></span>|<span data-ttu-id="95a25-161">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="95a25-161">win:UnicodeString</span></span>|<span data-ttu-id="95a25-162">Chemin d’accès du module.</span><span class="sxs-lookup"><span data-stu-id="95a25-162">The module path.</span></span>|  
|<span data-ttu-id="95a25-163">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="95a25-163">ClrInstanceID</span></span>|<span data-ttu-id="95a25-164">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="95a25-164">win:UInt16</span></span>|<span data-ttu-id="95a25-165">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="95a25-165">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95a25-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95a25-166">See also</span></span>

- [<span data-ttu-id="95a25-167">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="95a25-167">CLR ETW Events</span></span>](clr-etw-events.md)
