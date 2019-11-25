---
title: Événements de sécurité ETW
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1dad042595608a805f978673858acaa5c01130f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974879"
---
# <a name="security-etw-events"></a><span data-ttu-id="c2b2c-102">Événements de sécurité ETW</span><span class="sxs-lookup"><span data-stu-id="c2b2c-102">Security ETW Events</span></span>

<span data-ttu-id="c2b2c-103">Les événements de sécurité sont déclenchés pendant la vérification de nom fort et la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="c2b2c-104">Événements StrongNameVerificationStart_V1 et StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="c2b2c-104">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="c2b2c-105">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-105">The following table shows the keyword and level.</span></span> <span data-ttu-id="c2b2c-106">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="c2b2c-106">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="c2b2c-107">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="c2b2c-107">Keyword for raising the event</span></span>|<span data-ttu-id="c2b2c-108">Level</span><span class="sxs-lookup"><span data-stu-id="c2b2c-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c2b2c-109">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="c2b2c-109">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="c2b2c-110">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="c2b2c-110">Informational(4)</span></span>|  
  
 <span data-ttu-id="c2b2c-111">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-111">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c2b2c-112">événement</span><span class="sxs-lookup"><span data-stu-id="c2b2c-112">Event</span></span>|<span data-ttu-id="c2b2c-113">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c2b2c-113">Event ID</span></span>|<span data-ttu-id="c2b2c-114">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="c2b2c-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="c2b2c-115">181</span><span class="sxs-lookup"><span data-stu-id="c2b2c-115">181</span></span>|<span data-ttu-id="c2b2c-116">Début de la vérification de nom fort.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-116">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="c2b2c-117">182</span><span class="sxs-lookup"><span data-stu-id="c2b2c-117">182</span></span>|<span data-ttu-id="c2b2c-118">Fin de la vérification de nom fort.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-118">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="c2b2c-119">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c2b2c-120">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="c2b2c-120">Field name</span></span>|<span data-ttu-id="c2b2c-121">Type de données</span><span class="sxs-lookup"><span data-stu-id="c2b2c-121">Data type</span></span>|<span data-ttu-id="c2b2c-122">Description</span><span class="sxs-lookup"><span data-stu-id="c2b2c-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c2b2c-123">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="c2b2c-123">VerificationFlags</span></span>|<span data-ttu-id="c2b2c-124">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c2b2c-124">win:UInt32</span></span>|<span data-ttu-id="c2b2c-125">Indicateurs de vérification.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-125">The verification flags.</span></span>|  
|<span data-ttu-id="c2b2c-126">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="c2b2c-126">ErrorCode</span></span>|<span data-ttu-id="c2b2c-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c2b2c-127">win:UInt32</span></span>|<span data-ttu-id="c2b2c-128">Code d'erreur HResult.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-128">The HResult error code.</span></span>|  
|<span data-ttu-id="c2b2c-129">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="c2b2c-129">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="c2b2c-130">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c2b2c-130">win:UnicodeString</span></span>|<span data-ttu-id="c2b2c-131">Nom d'assembly qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-131">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="c2b2c-132">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c2b2c-132">ClrInstanceID</span></span>|<span data-ttu-id="c2b2c-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c2b2c-133">win:UInt16</span></span>|<span data-ttu-id="c2b2c-134">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-134">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="c2b2c-135">Événements AuthenticodeVerificationStart_V1 et AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="c2b2c-135">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="c2b2c-136">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-136">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c2b2c-137">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="c2b2c-137">Keyword for raising the event</span></span>|<span data-ttu-id="c2b2c-138">Level</span><span class="sxs-lookup"><span data-stu-id="c2b2c-138">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c2b2c-139">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="c2b2c-139">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="c2b2c-140">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="c2b2c-140">Informational(4)</span></span>|  
  
 <span data-ttu-id="c2b2c-141">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-141">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c2b2c-142">événement</span><span class="sxs-lookup"><span data-stu-id="c2b2c-142">Event</span></span>|<span data-ttu-id="c2b2c-143">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c2b2c-143">Event ID</span></span>|<span data-ttu-id="c2b2c-144">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="c2b2c-144">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="c2b2c-145">183</span><span class="sxs-lookup"><span data-stu-id="c2b2c-145">183</span></span>|<span data-ttu-id="c2b2c-146">Début de la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-146">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="c2b2c-147">184</span><span class="sxs-lookup"><span data-stu-id="c2b2c-147">184</span></span>|<span data-ttu-id="c2b2c-148">Fin de la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-148">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="c2b2c-149">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-149">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c2b2c-150">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="c2b2c-150">Field name</span></span>|<span data-ttu-id="c2b2c-151">Type de données</span><span class="sxs-lookup"><span data-stu-id="c2b2c-151">Data type</span></span>|<span data-ttu-id="c2b2c-152">Description</span><span class="sxs-lookup"><span data-stu-id="c2b2c-152">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c2b2c-153">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="c2b2c-153">VerificationFlags</span></span>|<span data-ttu-id="c2b2c-154">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c2b2c-154">win:UInt32</span></span>|<span data-ttu-id="c2b2c-155">Indicateurs de vérification.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-155">The verification flags.</span></span>|  
|<span data-ttu-id="c2b2c-156">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="c2b2c-156">ErrorCode</span></span>|<span data-ttu-id="c2b2c-157">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c2b2c-157">win:UInt32</span></span>|<span data-ttu-id="c2b2c-158">Code d'erreur HResult.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-158">The HResult error code.</span></span>|  
|<span data-ttu-id="c2b2c-159">ModulePath</span><span class="sxs-lookup"><span data-stu-id="c2b2c-159">ModulePath</span></span>|<span data-ttu-id="c2b2c-160">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c2b2c-160">win:UnicodeString</span></span>|<span data-ttu-id="c2b2c-161">Chemin d’accès du module.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-161">The module path.</span></span>|  
|<span data-ttu-id="c2b2c-162">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c2b2c-162">ClrInstanceID</span></span>|<span data-ttu-id="c2b2c-163">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c2b2c-163">win:UInt16</span></span>|<span data-ttu-id="c2b2c-164">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c2b2c-164">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2b2c-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2b2c-165">See also</span></span>

- [<span data-ttu-id="c2b2c-166">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="c2b2c-166">CLR ETW Events</span></span>](clr-etw-events.md)
