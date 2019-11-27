---
title: Modifications de sécurité dans le .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af2869e5ca3b41778c094b7a78a9493e74868811
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204504"
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="47d43-102">Modifications de sécurité dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="47d43-102">Security Changes in the .NET Framework</span></span>

<span data-ttu-id="47d43-103">La modification la plus importante de la sécurité dans le .NET Framework 4,5 est l’attribution d’un nom fort.</span><span class="sxs-lookup"><span data-stu-id="47d43-103">The most important change to security in the .NET Framework 4.5 is in strong naming.</span></span> <span data-ttu-id="47d43-104">Pour obtenir une description de ces modifications, consultez [Enhanced Strong Naming](../../standard/assembly/enhanced-strong-naming.md) .</span><span class="sxs-lookup"><span data-stu-id="47d43-104">See [Enhanced Strong Naming](../../standard/assembly/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
<span data-ttu-id="47d43-105">Le .NET Framework fournit un modèle de sécurité à deux niveaux pour les applications managées.</span><span class="sxs-lookup"><span data-stu-id="47d43-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> <span data-ttu-id="47d43-106">Les applications du Windows 8. x Store s’exécutent dans un conteneur de sécurité Windows qui limite l’accès aux ressources.</span><span class="sxs-lookup"><span data-stu-id="47d43-106">Windows 8.x Store apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="47d43-107">Dans ce conteneur, les applications managées s'exécutent en mode confiance totale.</span><span class="sxs-lookup"><span data-stu-id="47d43-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="47d43-108">Du point de vue de la sécurité d'accès du code (CAS), un développeur ne peut rien faire pour élever les privilèges.</span><span class="sxs-lookup"><span data-stu-id="47d43-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="47d43-109">Pour plus d’informations sur les privilèges octroyés par Windows, consultez [Déclarations des fonctionnalités d’application (applications du Windows Store)](https://go.microsoft.com/fwlink/?LinkId=230436) dans le centre de développement Windows.</span><span class="sxs-lookup"><span data-stu-id="47d43-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="47d43-110">Pour plus d’informations sur la création d’une application Windows 8. x Store, consultez [créer votre première C# application du Windows Store à l’aide de ou Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="47d43-110">For information about creating a Windows 8.x Store app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span></span>
