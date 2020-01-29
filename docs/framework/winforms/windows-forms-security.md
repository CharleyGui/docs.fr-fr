---
title: Sécurité
ms.date: 03/30/2017
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
ms.openlocfilehash: a3debf487b9b2a04277d9ce3007f28662fa4899e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734492"
---
# <a name="windows-forms-security"></a><span data-ttu-id="ad4e4-102">Sécurité de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ad4e4-102">Windows Forms Security</span></span>
<span data-ttu-id="ad4e4-103">Windows Forms propose un modèle de sécurité basé sur du code (les niveaux de sécurité sont définis pour le code, quel que soit l’utilisateur qui exécute le code).</span><span class="sxs-lookup"><span data-stu-id="ad4e4-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="ad4e4-104">Cela s’ajoute à tous les schémas de sécurité qui peuvent être déjà en place sur votre système informatique.</span><span class="sxs-lookup"><span data-stu-id="ad4e4-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="ad4e4-105">Ceux-ci peuvent inclure ceux du navigateur (par exemple, la sécurité basée sur une zone disponible dans Internet Explorer) ou le système d’exploitation (par exemple, la sécurité basée sur les informations d’identification de Windows NT).</span><span class="sxs-lookup"><span data-stu-id="ad4e4-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad4e4-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ad4e4-106">In This Section</span></span>  
 [<span data-ttu-id="ad4e4-107">Vue d’ensemble de la sécurité dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ad4e4-107">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)  
 <span data-ttu-id="ad4e4-108">Explique brièvement le modèle de sécurité .NET Framework et les étapes de base nécessaires pour garantir la sécurité des Windows Forms dans votre application.</span><span class="sxs-lookup"><span data-stu-id="ad4e4-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="ad4e4-109">Accès plus sécurisé aux fichiers et aux données dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ad4e4-109">More Secure File and Data Access in Windows Forms</span></span>](more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="ad4e4-110">Décrit comment accéder aux fichiers et aux données dans un environnement de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="ad4e4-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="ad4e4-111">Impression plus sécurisée dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ad4e4-111">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="ad4e4-112">Décrit comment accéder aux fonctionnalités d’impression dans un environnement de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="ad4e4-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="ad4e4-113">Considérations supplémentaires sur la sécurité des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ad4e4-113">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="ad4e4-114">Décrit comment manipuler des fenêtres, utiliser le presse-papiers et effectuer des appels au code non managé dans un environnement de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="ad4e4-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ad4e4-115">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="ad4e4-115">Related Sections</span></span>  
 <span data-ttu-id="ad4e4-116">[Stratégie de sécurité par défaut](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ad4e4-116">[Default Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span></span>  
 <span data-ttu-id="ad4e4-117">Répertorie les autorisations par défaut accordées dans les jeux d’autorisations confiance totale, Intranet local et Internet.</span><span class="sxs-lookup"><span data-stu-id="ad4e4-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 <span data-ttu-id="ad4e4-118">[Administration générale de la stratégie de sécurité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ad4e4-118">[General Security Policy Administration](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span></span>  
 <span data-ttu-id="ad4e4-119">Donne des informations sur l’administration de la stratégie de sécurité .NET Framework et l’élévation d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="ad4e4-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="ad4e4-120">Autorisations et administration de stratégie dangereuses</span><span class="sxs-lookup"><span data-stu-id="ad4e4-120">Dangerous Permissions and Policy Administration</span></span>](../misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="ad4e4-121">Présente quelques-unes des autorisations de l’infrastructure the.NET qui peuvent permettre le contournement du système de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ad4e4-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="ad4e4-122">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="ad4e4-122">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="ad4e4-123">Liens vers des rubriques qui expliquent les meilleures pratiques pour écrire du code en toute sécurité sur le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad4e4-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 <span data-ttu-id="ad4e4-124">[Demande d’autorisations](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ad4e4-124">[Requesting Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span></span>  
 <span data-ttu-id="ad4e4-125">Traite de l’utilisation d’attributs pour permettre au runtime de savoir quelles autorisations votre code doit exécuter.</span><span class="sxs-lookup"><span data-stu-id="ad4e4-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="ad4e4-126">Concepts fondamentaux sur la sécurité</span><span class="sxs-lookup"><span data-stu-id="ad4e4-126">Key Security Concepts</span></span>](../../standard/security/key-security-concepts.md)  
 <span data-ttu-id="ad4e4-127">Liens vers des rubriques qui traitent des aspects fondamentaux de la sécurité du code.</span><span class="sxs-lookup"><span data-stu-id="ad4e4-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="ad4e4-128">Notions fondamentales de la sécurité d’accès du code</span><span class="sxs-lookup"><span data-stu-id="ad4e4-128">Code Access Security Basics</span></span>](../misc/code-access-security-basics.md)  
 <span data-ttu-id="ad4e4-129">Décrit les principes de base de l’utilisation de la stratégie de sécurité .NET Framework Runtime.</span><span class="sxs-lookup"><span data-stu-id="ad4e4-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 <span data-ttu-id="ad4e4-130">[Détermination de la modification de la stratégie de sécurité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ad4e4-130">[Determining When to Modify Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span></span>  
 <span data-ttu-id="ad4e4-131">Explique comment déterminer si vos applications doivent s’écarter de la stratégie de sécurité par défaut.</span><span class="sxs-lookup"><span data-stu-id="ad4e4-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 <span data-ttu-id="ad4e4-132">[Déploiement de la stratégie de sécurité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ad4e4-132">[Deploying Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span></span>  
 <span data-ttu-id="ad4e4-133">Décrit la meilleure façon de déployer les modifications de stratégie de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ad4e4-133">Discusses the best manner for deploying security policy changes.</span></span>
