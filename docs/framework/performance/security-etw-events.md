---
title: Événements de sécurité ETW
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: c443bda8cdc2c6b32760e9dcba8b81a29d81660b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715938"
---
# <a name="security-etw-events"></a><span data-ttu-id="d0c0b-102">Événements de sécurité ETW</span><span class="sxs-lookup"><span data-stu-id="d0c0b-102">Security ETW Events</span></span>

<span data-ttu-id="d0c0b-103">Les événements de sécurité sont déclenchés pendant la vérification de nom fort et la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="d0c0b-104">Événements StrongNameVerificationStart_V1 et StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="d0c0b-104">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="d0c0b-105">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-105">The following table shows the keyword and level.</span></span> <span data-ttu-id="d0c0b-106">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="d0c0b-106">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="d0c0b-107">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="d0c0b-107">Keyword for raising the event</span></span>|<span data-ttu-id="d0c0b-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="d0c0b-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d0c0b-109">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="d0c0b-109">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="d0c0b-110">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="d0c0b-110">Informational(4)</span></span>|  
  
 <span data-ttu-id="d0c0b-111">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-111">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d0c0b-112">Event</span><span class="sxs-lookup"><span data-stu-id="d0c0b-112">Event</span></span>|<span data-ttu-id="d0c0b-113">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="d0c0b-113">Event ID</span></span>|<span data-ttu-id="d0c0b-114">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="d0c0b-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="d0c0b-115">181</span><span class="sxs-lookup"><span data-stu-id="d0c0b-115">181</span></span>|<span data-ttu-id="d0c0b-116">Début de la vérification de nom fort.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-116">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="d0c0b-117">182</span><span class="sxs-lookup"><span data-stu-id="d0c0b-117">182</span></span>|<span data-ttu-id="d0c0b-118">Fin de la vérification de nom fort.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-118">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="d0c0b-119">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d0c0b-120">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="d0c0b-120">Field name</span></span>|<span data-ttu-id="d0c0b-121">Type de données</span><span class="sxs-lookup"><span data-stu-id="d0c0b-121">Data type</span></span>|<span data-ttu-id="d0c0b-122">Description</span><span class="sxs-lookup"><span data-stu-id="d0c0b-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d0c0b-123">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="d0c0b-123">VerificationFlags</span></span>|<span data-ttu-id="d0c0b-124">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d0c0b-124">win:UInt32</span></span>|<span data-ttu-id="d0c0b-125">Indicateurs de vérification.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-125">The verification flags.</span></span>|  
|<span data-ttu-id="d0c0b-126">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="d0c0b-126">ErrorCode</span></span>|<span data-ttu-id="d0c0b-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d0c0b-127">win:UInt32</span></span>|<span data-ttu-id="d0c0b-128">Code d'erreur HResult.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-128">The HResult error code.</span></span>|  
|<span data-ttu-id="d0c0b-129">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="d0c0b-129">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="d0c0b-130">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d0c0b-130">win:UnicodeString</span></span>|<span data-ttu-id="d0c0b-131">Nom d'assembly qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-131">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="d0c0b-132">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d0c0b-132">ClrInstanceID</span></span>|<span data-ttu-id="d0c0b-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d0c0b-133">win:UInt16</span></span>|<span data-ttu-id="d0c0b-134">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-134">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="d0c0b-135">Événements AuthenticodeVerificationStart_V1 et AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="d0c0b-135">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="d0c0b-136">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-136">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d0c0b-137">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="d0c0b-137">Keyword for raising the event</span></span>|<span data-ttu-id="d0c0b-138">Niveau</span><span class="sxs-lookup"><span data-stu-id="d0c0b-138">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d0c0b-139">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="d0c0b-139">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="d0c0b-140">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="d0c0b-140">Informational(4)</span></span>|  
  
 <span data-ttu-id="d0c0b-141">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-141">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d0c0b-142">Event</span><span class="sxs-lookup"><span data-stu-id="d0c0b-142">Event</span></span>|<span data-ttu-id="d0c0b-143">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="d0c0b-143">Event ID</span></span>|<span data-ttu-id="d0c0b-144">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="d0c0b-144">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="d0c0b-145">183</span><span class="sxs-lookup"><span data-stu-id="d0c0b-145">183</span></span>|<span data-ttu-id="d0c0b-146">Début de la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-146">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="d0c0b-147">184</span><span class="sxs-lookup"><span data-stu-id="d0c0b-147">184</span></span>|<span data-ttu-id="d0c0b-148">Fin de la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-148">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="d0c0b-149">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-149">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d0c0b-150">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="d0c0b-150">Field name</span></span>|<span data-ttu-id="d0c0b-151">Type de données</span><span class="sxs-lookup"><span data-stu-id="d0c0b-151">Data type</span></span>|<span data-ttu-id="d0c0b-152">Description</span><span class="sxs-lookup"><span data-stu-id="d0c0b-152">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d0c0b-153">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="d0c0b-153">VerificationFlags</span></span>|<span data-ttu-id="d0c0b-154">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d0c0b-154">win:UInt32</span></span>|<span data-ttu-id="d0c0b-155">Indicateurs de vérification.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-155">The verification flags.</span></span>|  
|<span data-ttu-id="d0c0b-156">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="d0c0b-156">ErrorCode</span></span>|<span data-ttu-id="d0c0b-157">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d0c0b-157">win:UInt32</span></span>|<span data-ttu-id="d0c0b-158">Code d'erreur HResult.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-158">The HResult error code.</span></span>|  
|<span data-ttu-id="d0c0b-159">ModulePath</span><span class="sxs-lookup"><span data-stu-id="d0c0b-159">ModulePath</span></span>|<span data-ttu-id="d0c0b-160">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d0c0b-160">win:UnicodeString</span></span>|<span data-ttu-id="d0c0b-161">Chemin d'accès du module.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-161">The module path.</span></span>|  
|<span data-ttu-id="d0c0b-162">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d0c0b-162">ClrInstanceID</span></span>|<span data-ttu-id="d0c0b-163">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d0c0b-163">win:UInt16</span></span>|<span data-ttu-id="d0c0b-164">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-164">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0c0b-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0c0b-165">See also</span></span>

- [<span data-ttu-id="d0c0b-166">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="d0c0b-166">CLR ETW Events</span></span>](clr-etw-events.md)
