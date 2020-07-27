---
title: Vue d'ensemble de la sécurité UI Automation
description: Lisez une vue d’ensemble du modèle de sécurité pour Microsoft UI Automation. Comprendre le contrôle de compte d’utilisateur, les tâches qui requièrent des privilèges plus élevés et les fichiers manifestes.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: d483f282db8ce8e5653d6d83361fa44df05f63f5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163143"
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="425be-104">Vue d'ensemble de la sécurité UI Automation</span><span class="sxs-lookup"><span data-stu-id="425be-104">UI Automation Security Overview</span></span>

> [!NOTE]
> <span data-ttu-id="425be-105">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="425be-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="425be-106">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="425be-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="425be-107">Cette vue d’ensemble décrit le modèle de sécurité de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dans Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="425be-107">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in Windows Vista.</span></span>

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a><span data-ttu-id="425be-108">Contrôle de compte d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="425be-108">User Account Control</span></span>

<span data-ttu-id="425be-109">La sécurité est un objectif majeur de Windows Vista et, parmi les innovations, c’est la possibilité pour les utilisateurs de s’exécuter en tant qu’utilisateurs standard (non-administrateur) sans qu’il soit nécessaire de bloquer l’exécution d’applications et de services nécessitant des privilèges plus élevés.</span><span class="sxs-lookup"><span data-stu-id="425be-109">Security is a major focus of Windows Vista and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>

<span data-ttu-id="425be-110">Dans Windows Vista, la plupart des applications sont fournies avec un jeton d’administration ou standard.</span><span class="sxs-lookup"><span data-stu-id="425be-110">In Windows Vista, most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="425be-111">Si une application ne peut pas être identifiée en tant qu'application administrative, elle est lancée par défaut en tant qu'application standard.</span><span class="sxs-lookup"><span data-stu-id="425be-111">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="425be-112">Avant qu’une application identifiée comme administrative puisse être lancée, Windows Vista invite l’utilisateur à donner son consentement pour exécuter l’application avec des privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="425be-112">Before an application identified as administrative can be launched, Windows Vista prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="425be-113">L'invite de consentement s'affiche par défaut, même si l'utilisateur est membre du groupe Administrateurs local. Cela est dû au fait que les administrateurs sont considérés comme des utilisateurs standard jusqu'à ce qu'une application ou un composant système nécessitant des informations d'identification d'administration demande l'autorisation de s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="425be-113">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="425be-114">Tâches nécessitant des privilèges plus élevés</span><span class="sxs-lookup"><span data-stu-id="425be-114">Tasks Requiring Higher Privileges</span></span>

<span data-ttu-id="425be-115">Quand un utilisateur tente d’effectuer une tâche qui requiert des privilèges d’administrateur, Windows Vista présente une boîte de dialogue demandant à l’utilisateur de continuer.</span><span class="sxs-lookup"><span data-stu-id="425be-115">When a user attempts to perform a task that requires administrative privileges, Windows Vista presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="425be-116">Cette boîte de dialogue bénéficie d'une protection contre les communications interprocessus, ce qui empêche les logiciels malveillants de simuler l'entrée de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="425be-116">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="425be-117">De même, d'autres processus ne sont normalement pas autorisés à accéder à l'écran d'ouverture de session sur le Bureau.</span><span class="sxs-lookup"><span data-stu-id="425be-117">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>

<span data-ttu-id="425be-118">Les clients UI Automation doivent communiquer avec d’autres processus, certains d’entre eux pouvant être exécutés à un niveau de privilège supérieur.</span><span class="sxs-lookup"><span data-stu-id="425be-118">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="425be-119">Les clients peuvent aussi avoir besoin d'accéder à des boîtes de dialogue système qui ne sont normalement pas visibles à d'autres processus.</span><span class="sxs-lookup"><span data-stu-id="425be-119">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="425be-120">Par conséquent, les clients [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] doivent être approuvés par le système et s'exécuter avec des privilèges spéciaux.</span><span class="sxs-lookup"><span data-stu-id="425be-120">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>

<span data-ttu-id="425be-121">Pour avoir l'autorisation de communiquer avec des applications exécutées à un niveau de privilège plus élevé, les applications doivent être signées.</span><span class="sxs-lookup"><span data-stu-id="425be-121">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a><span data-ttu-id="425be-122">Fichiers manifeste</span><span class="sxs-lookup"><span data-stu-id="425be-122">Manifest Files</span></span>

<span data-ttu-id="425be-123">Pour accéder à l’interface utilisateur du système protégé, les applications doivent être générées avec un fichier manifeste qui comprend l' `uiAccess` attribut dans la `requestedExecutionLevel` balise, comme suit :</span><span class="sxs-lookup"><span data-stu-id="425be-123">To gain access to the protected system UI, applications must be built with a manifest file that includes the `uiAccess` attribute in the `requestedExecutionLevel` tag, as follows:</span></span>

```xml
<trustInfo xmlns="urn:schemas-microsoft-com:asm.v3">
  <security>
    <requestedPrivileges>
      <requestedExecutionLevel
        level="highestAvailable"
        uiAccess="true" />
    </requestedPrivileges>
  </security>
</trustInfo>
```

<span data-ttu-id="425be-124">Dans ce code, la valeur de l'attribut `level` n'est qu'un exemple.</span><span class="sxs-lookup"><span data-stu-id="425be-124">The value of the `level` attribute in this code is an example only.</span></span>

<span data-ttu-id="425be-125">`uiAccess`est « false » par défaut ; autrement dit, si l’attribut est omis ou s’il n’existe aucun manifeste pour l’assembly, l’application ne sera pas en mesure d’accéder à l’interface utilisateur protégée.</span><span class="sxs-lookup"><span data-stu-id="425be-125">`uiAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected UI.</span></span>
