---
title: Autorisations dangereuses et administration de stratégie
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ffe4f3e000c80610d5a105dddef90f9cfd51f0dc
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205590"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="c15a1-102">Autorisations dangereuses et administration de stratégie</span><span class="sxs-lookup"><span data-stu-id="c15a1-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="c15a1-103">Plusieurs des opérations protégées pour lesquelles le .NET Framework fournit des autorisations risquent de permettre le contournement du système de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c15a1-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="c15a1-104">Ces autorisations dangereuses doivent être accordées uniquement à du code fiable, et seulement en cas de nécessité.</span><span class="sxs-lookup"><span data-stu-id="c15a1-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="c15a1-105">Il n’existe généralement aucune défense contre du code malveillant, si ces autorisations sont accordées.</span><span class="sxs-lookup"><span data-stu-id="c15a1-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c15a1-106">Dans le .NET Framework 4, des modifications importantes ont été apportées à la terminologie et au modèle de sécurité .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c15a1-106">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="c15a1-107">Pour plus d’informations sur ces modifications, consultez [modifications de sécurité](../security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="c15a1-107">For more information about these changes, see [Security Changes](../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="c15a1-108">Les autorisations dangereuses sont expliquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="c15a1-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="c15a1-109">Autorisation</span><span class="sxs-lookup"><span data-stu-id="c15a1-109">Permission</span></span>|<span data-ttu-id="c15a1-110">Risque potentiel</span><span class="sxs-lookup"><span data-stu-id="c15a1-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="c15a1-111">Permet au code managé d’appeler du code non managé, ce qui est souvent dangereux.</span><span class="sxs-lookup"><span data-stu-id="c15a1-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="c15a1-112">En l’absence de vérification, le code peut tout faire.</span><span class="sxs-lookup"><span data-stu-id="c15a1-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="c15a1-113">Les preuves invalidées peuvent tromper la stratégie de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c15a1-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="c15a1-114">La modification de la stratégie de sécurité peut permettre de désactiver la sécurité.</span><span class="sxs-lookup"><span data-stu-id="c15a1-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="c15a1-115">L’utilisation de la sérialisation peut constituer un moyen de contourner les mécanismes d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="c15a1-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="c15a1-116">Pour plus d’informations, consultez [Sécurité et sérialisation](security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="c15a1-116">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="c15a1-117">La capacité à définir le principal actuel peut permettre de tromper la sécurité basée sur les rôles.</span><span class="sxs-lookup"><span data-stu-id="c15a1-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="c15a1-118">La manipulation des threads est dangereuse en raison de l’état de sécurité associé aux threads.</span><span class="sxs-lookup"><span data-stu-id="c15a1-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="c15a1-119">Permet d’utiliser des membres privés pour passer outre les mécanismes d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="c15a1-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c15a1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c15a1-120">See also</span></span>

- [<span data-ttu-id="c15a1-121">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="c15a1-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
