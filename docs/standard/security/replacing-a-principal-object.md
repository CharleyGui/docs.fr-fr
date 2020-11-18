---
title: Remplacement d'un objet Principal
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET], replacing principal objects
- security [.NET], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
ms.openlocfilehash: b8f7a8fbd3b9c65126d6a3a65a5f6722f2ad93de
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824172"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="76234-102">Remplacement d'un objet Principal</span><span class="sxs-lookup"><span data-stu-id="76234-102">Replacing a Principal Object</span></span>

<span data-ttu-id="76234-103">Les applications qui fournissent des services d’authentification doivent pouvoir remplacer l’objet **Principal** (<xref:System.Security.Principal.IPrincipal>) d’un thread donné.</span><span class="sxs-lookup"><span data-stu-id="76234-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="76234-104">En outre, le système de sécurité doit permettre de protéger la possibilité de remplacer les objets **Principal** si un **Principal** malveillant et incorrect attaché compromet la sécurité de votre application en simulant une fausse identité ou un faux rôle.</span><span class="sxs-lookup"><span data-stu-id="76234-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="76234-105">Par conséquent, les applications ayant besoin de pouvoir remplacer les objets **Principal** doivent se voir attribuer l’objet <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> pour le contrôle du principal.</span><span class="sxs-lookup"><span data-stu-id="76234-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="76234-106">(Notez que cette autorisation n’est pas obligatoire pour effectuer des vérifications de sécurité basée sur les rôles ou créer des objets **Principal** .)</span><span class="sxs-lookup"><span data-stu-id="76234-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
<span data-ttu-id="76234-107">L’objet **Principal** actuel peut être remplacé en effectuant les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="76234-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="76234-108">Créer l’objet **Principal** de remplacement et l’objet **Identity** associé.</span><span class="sxs-lookup"><span data-stu-id="76234-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2. <span data-ttu-id="76234-109">Attacher le nouvel objet **Principal** au contexte d’appel.</span><span class="sxs-lookup"><span data-stu-id="76234-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76234-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="76234-110">Example</span></span>

<span data-ttu-id="76234-111">L’exemple suivant montre comment créer un objet principal générique et l’utiliser pour définir le principal d’un thread.</span><span class="sxs-lookup"><span data-stu-id="76234-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
[!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
[!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="76234-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76234-112">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [<span data-ttu-id="76234-113">Objets Principal et Identity</span><span class="sxs-lookup"><span data-stu-id="76234-113">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="76234-114">Sécurité ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="76234-114">ASP.NET Core Security</span></span>](/aspnet/core/security/)
