---
title: 'Procédure : créer une identité de principal de sécurité personnalisée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
ms.openlocfilehash: 6c50d6b0ac2baa2dc61431af4afb8dca3860456a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249304"
---
# <a name="how-to-create-a-custom-principal-identity"></a><span data-ttu-id="00ac4-102">Procédure : créer une identité de principal de sécurité personnalisée</span><span class="sxs-lookup"><span data-stu-id="00ac4-102">How to: Create a Custom Principal Identity</span></span>

<span data-ttu-id="00ac4-103">Le <xref:System.Security.Permissions.PrincipalPermissionAttribute> constitue un moyen déclaratif de contrôler l'accès aux méthodes de service.</span><span class="sxs-lookup"><span data-stu-id="00ac4-103">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is a declarative means of controlling access to service methods.</span></span> <span data-ttu-id="00ac4-104">Lors de l'utilisation de cet attribut, l'énumération <xref:System.ServiceModel.Description.PrincipalPermissionMode> spécifie le mode d'exécution des contrôles d'autorisation.</span><span class="sxs-lookup"><span data-stu-id="00ac4-104">When using this attribute, the <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeration specifies the mode for performing authorization checks.</span></span> <span data-ttu-id="00ac4-105">Lorsque ce mode a la valeur <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, il permet à l'utilisateur de spécifier une classe <xref:System.Security.Principal.IPrincipal> personnalisée retournée par la propriété <xref:System.Threading.Thread.CurrentPrincipal%2A>.</span><span class="sxs-lookup"><span data-stu-id="00ac4-105">When this mode is set to <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, it enables the user to specify a custom <xref:System.Security.Principal.IPrincipal> class returned by the <xref:System.Threading.Thread.CurrentPrincipal%2A> property.</span></span> <span data-ttu-id="00ac4-106">Cette rubrique illustre le scénario lorsque <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> est utilisé en association avec une stratégie d'autorisation personnalisée et une principal de sécurité personnalisée.</span><span class="sxs-lookup"><span data-stu-id="00ac4-106">This topic illustrates the scenario when <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> is used in combination with a custom authorization policy and a custom principal.</span></span>  
  
 <span data-ttu-id="00ac4-107">Pour plus d’informations sur l’utilisation de <xref:System.Security.Permissions.PrincipalPermissionAttribute> , consultez [Comment : restreindre l’accès avec la classe PrincipalPermissionAttribute](../how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="00ac4-107">For more information about using the <xref:System.Security.Permissions.PrincipalPermissionAttribute>, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="00ac4-108"> Exemple</span><span class="sxs-lookup"><span data-stu-id="00ac4-108">Example</span></span>  

 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="00ac4-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="00ac4-109">Compiling the Code</span></span>  

 <span data-ttu-id="00ac4-110">Des références aux espaces de noms suivants sont exigées pour compiler le code :</span><span class="sxs-lookup"><span data-stu-id="00ac4-110">References to the following namespaces are needed to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.Collections.Generic>  
  
- <xref:System.Security.Permissions>  
  
- <xref:System.Security.Principal>  
  
- <xref:System.Threading>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Description>  
  
- <xref:System.IdentityModel.Claims>  
  
- <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a><span data-ttu-id="00ac4-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00ac4-111">See also</span></span>

- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [<span data-ttu-id="00ac4-112">Procédure : utiliser le fournisseur de rôle ASP.NET avec un service</span><span class="sxs-lookup"><span data-stu-id="00ac4-112">How to: Use the ASP.NET Role Provider with a Service</span></span>](../feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="00ac4-113">Procédure : restreindre l’accès à la classe PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="00ac4-113">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)
