---
title: Événements de sécurité ETW
description: Comprendre les événements ETW de sécurité, qui sont déclenchés pendant la vérification de nom fort et la vérification Authenticode dans .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: 4402bf5690a53ce518077268a3e20a95aeb14e8a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272512"
---
# <a name="security-etw-events"></a><span data-ttu-id="ccbe3-103">Événements de sécurité ETW</span><span class="sxs-lookup"><span data-stu-id="ccbe3-103">Security ETW Events</span></span>

<span data-ttu-id="ccbe3-104">Les événements de sécurité sont déclenchés pendant la vérification de nom fort et la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-104">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="ccbe3-105">Événements StrongNameVerificationStart_V1 et StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="ccbe3-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  

 <span data-ttu-id="ccbe3-106">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-106">The following table shows the keyword and level.</span></span> <span data-ttu-id="ccbe3-107">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="ccbe3-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="ccbe3-108">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="ccbe3-108">Keyword for raising the event</span></span>|<span data-ttu-id="ccbe3-109">Level</span><span class="sxs-lookup"><span data-stu-id="ccbe3-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ccbe3-110">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="ccbe3-110">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="ccbe3-111">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="ccbe3-111">Informational(4)</span></span>|  
  
 <span data-ttu-id="ccbe3-112">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-112">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ccbe3-113">Événement</span><span class="sxs-lookup"><span data-stu-id="ccbe3-113">Event</span></span>|<span data-ttu-id="ccbe3-114">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="ccbe3-114">Event ID</span></span>|<span data-ttu-id="ccbe3-115">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="ccbe3-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="ccbe3-116">181</span><span class="sxs-lookup"><span data-stu-id="ccbe3-116">181</span></span>|<span data-ttu-id="ccbe3-117">Début de la vérification de nom fort.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-117">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="ccbe3-118">182</span><span class="sxs-lookup"><span data-stu-id="ccbe3-118">182</span></span>|<span data-ttu-id="ccbe3-119">Fin de la vérification de nom fort.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-119">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="ccbe3-120">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ccbe3-121">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="ccbe3-121">Field name</span></span>|<span data-ttu-id="ccbe3-122">Type de données</span><span class="sxs-lookup"><span data-stu-id="ccbe3-122">Data type</span></span>|<span data-ttu-id="ccbe3-123">Description</span><span class="sxs-lookup"><span data-stu-id="ccbe3-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ccbe3-124">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="ccbe3-124">VerificationFlags</span></span>|<span data-ttu-id="ccbe3-125">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="ccbe3-125">win:UInt32</span></span>|<span data-ttu-id="ccbe3-126">Indicateurs de vérification.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-126">The verification flags.</span></span>|  
|<span data-ttu-id="ccbe3-127">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="ccbe3-127">ErrorCode</span></span>|<span data-ttu-id="ccbe3-128">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="ccbe3-128">win:UInt32</span></span>|<span data-ttu-id="ccbe3-129">Code d'erreur HResult.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-129">The HResult error code.</span></span>|  
|<span data-ttu-id="ccbe3-130">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="ccbe3-130">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="ccbe3-131">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="ccbe3-131">win:UnicodeString</span></span>|<span data-ttu-id="ccbe3-132">Nom d'assembly qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-132">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="ccbe3-133">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ccbe3-133">ClrInstanceID</span></span>|<span data-ttu-id="ccbe3-134">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="ccbe3-134">win:UInt16</span></span>|<span data-ttu-id="ccbe3-135">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-135">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="ccbe3-136">Événements AuthenticodeVerificationStart_V1 et AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="ccbe3-136">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  

 <span data-ttu-id="ccbe3-137">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-137">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ccbe3-138">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="ccbe3-138">Keyword for raising the event</span></span>|<span data-ttu-id="ccbe3-139">Level</span><span class="sxs-lookup"><span data-stu-id="ccbe3-139">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ccbe3-140">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="ccbe3-140">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="ccbe3-141">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="ccbe3-141">Informational(4)</span></span>|  
  
 <span data-ttu-id="ccbe3-142">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-142">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ccbe3-143">Événement</span><span class="sxs-lookup"><span data-stu-id="ccbe3-143">Event</span></span>|<span data-ttu-id="ccbe3-144">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="ccbe3-144">Event ID</span></span>|<span data-ttu-id="ccbe3-145">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="ccbe3-145">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="ccbe3-146">183</span><span class="sxs-lookup"><span data-stu-id="ccbe3-146">183</span></span>|<span data-ttu-id="ccbe3-147">Début de la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-147">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="ccbe3-148">184</span><span class="sxs-lookup"><span data-stu-id="ccbe3-148">184</span></span>|<span data-ttu-id="ccbe3-149">Fin de la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-149">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="ccbe3-150">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-150">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ccbe3-151">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="ccbe3-151">Field name</span></span>|<span data-ttu-id="ccbe3-152">Type de données</span><span class="sxs-lookup"><span data-stu-id="ccbe3-152">Data type</span></span>|<span data-ttu-id="ccbe3-153">Description</span><span class="sxs-lookup"><span data-stu-id="ccbe3-153">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ccbe3-154">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="ccbe3-154">VerificationFlags</span></span>|<span data-ttu-id="ccbe3-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="ccbe3-155">win:UInt32</span></span>|<span data-ttu-id="ccbe3-156">Indicateurs de vérification.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-156">The verification flags.</span></span>|  
|<span data-ttu-id="ccbe3-157">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="ccbe3-157">ErrorCode</span></span>|<span data-ttu-id="ccbe3-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="ccbe3-158">win:UInt32</span></span>|<span data-ttu-id="ccbe3-159">Code d'erreur HResult.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-159">The HResult error code.</span></span>|  
|<span data-ttu-id="ccbe3-160">ModulePath</span><span class="sxs-lookup"><span data-stu-id="ccbe3-160">ModulePath</span></span>|<span data-ttu-id="ccbe3-161">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="ccbe3-161">win:UnicodeString</span></span>|<span data-ttu-id="ccbe3-162">Chemin d’accès du module.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-162">The module path.</span></span>|  
|<span data-ttu-id="ccbe3-163">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ccbe3-163">ClrInstanceID</span></span>|<span data-ttu-id="ccbe3-164">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="ccbe3-164">win:UInt16</span></span>|<span data-ttu-id="ccbe3-165">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ccbe3-165">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccbe3-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccbe3-166">See also</span></span>

- [<span data-ttu-id="ccbe3-167">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="ccbe3-167">CLR ETW Events</span></span>](clr-etw-events.md)
