---
title: Autorisation de sécurité pour la redirection de liaison d’assembly
description: En savoir plus sur l’autorisation de sécurité requise pour la redirection de liaison d’assembly explicite dans un fichier de configuration d’application dans .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: 2de2c50f5adb9e9fa36ea015ef498e9953c83005
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165219"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="b293a-103">Autorisation de sécurité pour la redirection de liaison d’assembly</span><span class="sxs-lookup"><span data-stu-id="b293a-103">Assembly Binding Redirection Security Permission</span></span>

<span data-ttu-id="b293a-104">La redirection de liaison d’assembly explicite dans un fichier de configuration de l’application nécessite une autorisation de sécurité.</span><span class="sxs-lookup"><span data-stu-id="b293a-104">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="b293a-105">Cela s'applique à la redirection des assemblys .NET Framework et des assemblys tiers.</span><span class="sxs-lookup"><span data-stu-id="b293a-105">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="b293a-106">L’autorisation est accordée en définissant l' <xref:System.Security.Permissions.SecurityPermissionFlag> indicateur sur <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="b293a-106">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="b293a-107">Les assemblys managés n’ont pas d’autorisations par défaut.</span><span class="sxs-lookup"><span data-stu-id="b293a-107">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="b293a-108">L’autorisation de sécurité est accordée aux applications qui s’exécutent dans la zone de confiance (ordinateur local) et la zone intranet.</span><span class="sxs-lookup"><span data-stu-id="b293a-108">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="b293a-109">Les applications qui s’exécutent dans la zone Internet ne sont pas strictement autorisées à effectuer une redirection de liaison d’assembly.</span><span class="sxs-lookup"><span data-stu-id="b293a-109">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="b293a-110">L’autorisation n’est pas requise si la redirection d’assembly est effectuée dans un fichier de stratégie d’éditeur contrôlé par l’éditeur du composant ou dans le fichier de configuration de l’ordinateur contrôlé par l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="b293a-110">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="b293a-111">Toutefois, l’autorisation est requise pour qu’une application ignore explicitement la stratégie de l’éditeur à l’aide [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) de l’élément dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="b293a-111">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="b293a-112">Le tableau suivant présente les paramètres de sécurité par défaut de l’indicateur **BindingRedirects** .</span><span class="sxs-lookup"><span data-stu-id="b293a-112">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="b293a-113">Zone</span><span class="sxs-lookup"><span data-stu-id="b293a-113">Zone</span></span>|<span data-ttu-id="b293a-114">Paramètre de l’indicateur BindingRedirects</span><span class="sxs-lookup"><span data-stu-id="b293a-114">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="b293a-115">Zone approuvée (ordinateur local)</span><span class="sxs-lookup"><span data-stu-id="b293a-115">Trusted Zone (local machine)</span></span>|<span data-ttu-id="b293a-116">**ON**</span><span class="sxs-lookup"><span data-stu-id="b293a-116">**ON**</span></span>|  
|<span data-ttu-id="b293a-117">Zone Intranet</span><span class="sxs-lookup"><span data-stu-id="b293a-117">Intranet Zone</span></span>|<span data-ttu-id="b293a-118">**ON**</span><span class="sxs-lookup"><span data-stu-id="b293a-118">**ON**</span></span>|  
|<span data-ttu-id="b293a-119">Zone Internet</span><span class="sxs-lookup"><span data-stu-id="b293a-119">Internet Zone</span></span>|<span data-ttu-id="b293a-120">**OFF**</span><span class="sxs-lookup"><span data-stu-id="b293a-120">**OFF**</span></span>|  
|<span data-ttu-id="b293a-121">Zones non approuvées</span><span class="sxs-lookup"><span data-stu-id="b293a-121">Untrusted zones</span></span>|<span data-ttu-id="b293a-122">**OFF**</span><span class="sxs-lookup"><span data-stu-id="b293a-122">**OFF**</span></span>|  
  
 <span data-ttu-id="b293a-123">Un administrateur peut modifier ces paramètres de sécurité pour prendre en charge ou restreindre des scénarios spécifiques sur un ordinateur donné.</span><span class="sxs-lookup"><span data-stu-id="b293a-123">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="b293a-124">Il n’existe aucun outil permettant de modifier le paramètre d’indicateur **BindingRedirects** à partir de la valeur par défaut ; un administrateur doit modifier manuellement le fichier Security.config sur l’ordinateur d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b293a-124">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b293a-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b293a-125">See also</span></span>

- <span data-ttu-id="b293a-126">[Exécution côte à côte et fichiers de stratégie de l'éditeur](/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b293a-126">[Publisher Policy Files and Side-by-Side Execution](/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span></span>
- [<span data-ttu-id="b293a-127">Procédure : Activer et désactiver la redirection de liaison automatique</span><span class="sxs-lookup"><span data-stu-id="b293a-127">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="b293a-128">Exécution côte à côte</span><span class="sxs-lookup"><span data-stu-id="b293a-128">Side-by-Side Execution</span></span>](../deployment/side-by-side-execution.md)
