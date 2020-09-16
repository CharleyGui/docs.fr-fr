---
title: Autorisations dangereuses et administration de stratégie
description: Consultez des liens vers les différentes autorisations dangereuses dans .NET. Ces autorisations doivent être accordées uniquement au code fiable et uniquement lorsque cela est nécessaire.
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
ms.openlocfilehash: a2f4469590fea38924430b07eaf20d49f4dc46e9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556939"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="050ed-104">Autorisations dangereuses et administration de stratégie</span><span class="sxs-lookup"><span data-stu-id="050ed-104">Dangerous Permissions and Policy Administration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="050ed-105">Plusieurs des opérations protégées pour lesquelles le .NET Framework fournit des autorisations risquent de permettre le contournement du système de sécurité.</span><span class="sxs-lookup"><span data-stu-id="050ed-105">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="050ed-106">Ces autorisations dangereuses doivent être accordées uniquement à du code fiable, et seulement en cas de nécessité.</span><span class="sxs-lookup"><span data-stu-id="050ed-106">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="050ed-107">Il n’existe généralement aucune défense contre du code malveillant, si ces autorisations sont accordées.</span><span class="sxs-lookup"><span data-stu-id="050ed-107">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="050ed-108">Dans le .NET Framework 4, des modifications importantes ont été apportées à la terminologie et au modèle de sécurité .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="050ed-108">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="050ed-109">Pour plus d’informations sur ces modifications, consultez [modifications de sécurité](/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="050ed-109">For more information about these changes, see [Security Changes](/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="050ed-110">Les autorisations dangereuses sont expliquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="050ed-110">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="050ed-111">Autorisation</span><span class="sxs-lookup"><span data-stu-id="050ed-111">Permission</span></span>|<span data-ttu-id="050ed-112">Risque potentiel</span><span class="sxs-lookup"><span data-stu-id="050ed-112">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="050ed-113">Permet au code managé d’appeler du code non managé, ce qui est souvent dangereux.</span><span class="sxs-lookup"><span data-stu-id="050ed-113">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="050ed-114">En l’absence de vérification, le code peut tout faire.</span><span class="sxs-lookup"><span data-stu-id="050ed-114">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="050ed-115">Les preuves invalidées peuvent tromper la stratégie de sécurité.</span><span class="sxs-lookup"><span data-stu-id="050ed-115">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="050ed-116">La modification de la stratégie de sécurité peut permettre de désactiver la sécurité.</span><span class="sxs-lookup"><span data-stu-id="050ed-116">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="050ed-117">L’utilisation de la sérialisation peut constituer un moyen de contourner les mécanismes d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="050ed-117">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="050ed-118">Pour plus d’informations, consultez [Sécurité et sérialisation](security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="050ed-118">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="050ed-119">La capacité à définir le principal actuel peut permettre de tromper la sécurité basée sur les rôles.</span><span class="sxs-lookup"><span data-stu-id="050ed-119">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="050ed-120">La manipulation des threads est dangereuse en raison de l’état de sécurité associé aux threads.</span><span class="sxs-lookup"><span data-stu-id="050ed-120">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="050ed-121">Permet d’utiliser des membres privés pour passer outre les mécanismes d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="050ed-121">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="050ed-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="050ed-122">See also</span></span>

- [<span data-ttu-id="050ed-123">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="050ed-123">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
