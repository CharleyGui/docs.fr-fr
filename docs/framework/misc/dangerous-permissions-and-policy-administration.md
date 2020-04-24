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
ms.openlocfilehash: 15d28ff7d11b5d15ce44d9ab1f56548256850ff8
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645758"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="0b478-102">Autorisations dangereuses et administration de stratégie</span><span class="sxs-lookup"><span data-stu-id="0b478-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="0b478-103">Plusieurs des opérations protégées pour lesquelles le .NET Framework fournit des autorisations risquent de permettre le contournement du système de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0b478-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="0b478-104">Ces autorisations dangereuses doivent être accordées uniquement à du code fiable, et seulement en cas de nécessité.</span><span class="sxs-lookup"><span data-stu-id="0b478-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="0b478-105">Il n’existe généralement aucune défense contre du code malveillant, si ces autorisations sont accordées.</span><span class="sxs-lookup"><span data-stu-id="0b478-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b478-106">Dans le cadre .NET 4, il y a eu d’importants changements au modèle et à la terminologie de la sécurité du cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="0b478-106">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="0b478-107">Pour plus d’informations sur ces changements, voir [changements de sécurité](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="0b478-107">For more information about these changes, see [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="0b478-108">Les autorisations dangereuses sont expliquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="0b478-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="0b478-109">Autorisation</span><span class="sxs-lookup"><span data-stu-id="0b478-109">Permission</span></span>|<span data-ttu-id="0b478-110">Risque potentiel</span><span class="sxs-lookup"><span data-stu-id="0b478-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="0b478-111">Permet au code managé d’appeler du code non managé, ce qui est souvent dangereux.</span><span class="sxs-lookup"><span data-stu-id="0b478-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="0b478-112">En l’absence de vérification, le code peut tout faire.</span><span class="sxs-lookup"><span data-stu-id="0b478-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="0b478-113">Les preuves invalidées peuvent tromper la stratégie de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0b478-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="0b478-114">La modification de la stratégie de sécurité peut permettre de désactiver la sécurité.</span><span class="sxs-lookup"><span data-stu-id="0b478-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="0b478-115">L’utilisation de la sérialisation peut constituer un moyen de contourner les mécanismes d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="0b478-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="0b478-116">Pour plus d’informations, consultez [Sécurité et sérialisation](security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="0b478-116">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="0b478-117">La capacité à définir le principal actuel peut permettre de tromper la sécurité basée sur les rôles.</span><span class="sxs-lookup"><span data-stu-id="0b478-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="0b478-118">La manipulation des threads est dangereuse en raison de l’état de sécurité associé aux threads.</span><span class="sxs-lookup"><span data-stu-id="0b478-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="0b478-119">Permet d’utiliser des membres privés pour passer outre les mécanismes d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="0b478-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b478-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b478-120">See also</span></span>

- [<span data-ttu-id="0b478-121">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="0b478-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
