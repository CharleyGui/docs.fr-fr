---
title: Schéma des paramètres de démarrage
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "61701513"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="ed660-102">Schéma des paramètres de démarrage</span><span class="sxs-lookup"><span data-stu-id="ed660-102">Startup settings schema</span></span>

<span data-ttu-id="ed660-103">Les paramètres de démarrage spécifient la version du common language runtime qui doit exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="ed660-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="ed660-104">Élément</span><span class="sxs-lookup"><span data-stu-id="ed660-104">Element</span></span>|<span data-ttu-id="ed660-105">Description</span><span class="sxs-lookup"><span data-stu-id="ed660-105">Description</span></span>|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="ed660-106">Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="ed660-106">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="ed660-107">Les applications générées avec la version 1,1 du Runtime doivent utiliser l' **\<supportedRuntime>** élément.</span><span class="sxs-lookup"><span data-stu-id="ed660-107">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="ed660-108">Spécifie quelles versions du Common Language Runtime sont prises en charge par l'application.</span><span class="sxs-lookup"><span data-stu-id="ed660-108">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[\<startup>](startup-element.md)|<span data-ttu-id="ed660-109">Contient les **\<requiredRuntime>** **\<supportedRuntime>** éléments et.</span><span class="sxs-lookup"><span data-stu-id="ed660-109">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed660-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed660-110">See also</span></span>

- [<span data-ttu-id="ed660-111">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="ed660-111">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ed660-112">Comment : configurer une application pour prendre en charge .NET Framework 4 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="ed660-112">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
