---
title: 'Procédure : créer un SecurityBindingElement pour un mode d’authentification spécifié'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
ms.openlocfilehash: 6466d218ca21e7d2ee4f01f079f308348469fd97
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934341"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a><span data-ttu-id="dc8e1-102">Procédure : créer un SecurityBindingElement pour un mode d’authentification spécifié</span><span class="sxs-lookup"><span data-stu-id="dc8e1-102">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>
<span data-ttu-id="dc8e1-103">Windows Communication Foundation (WCF) fournit plusieurs modes par lesquels les clients et les services s’authentifient l’un l’autre.</span><span class="sxs-lookup"><span data-stu-id="dc8e1-103">Windows Communication Foundation (WCF) provides several modes by which clients and services authenticate to one another.</span></span> <span data-ttu-id="dc8e1-104">Vous pouvez créer des éléments de liaison de sécurité pour ces modes d'authentification en utilisant des méthodes statiques sur la classe <xref:System.ServiceModel.Channels.SecurityBindingElement> ou par la configuration, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="dc8e1-104">You can create security binding elements for these authentication modes by using static methods on the <xref:System.ServiceModel.Channels.SecurityBindingElement> class or through configuration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="dc8e1-105">Pour plus d’informations sur les 18 modes d’authentification, consultez [modes d’authentification SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="dc8e1-105">For more information about the 18 authentication modes, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc8e1-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="dc8e1-106">Example</span></span>  
 <span data-ttu-id="dc8e1-107">L’exemple de code suivant présente des méthodes pour créer des liaisons pour les divers modes d’authentification.</span><span class="sxs-lookup"><span data-stu-id="dc8e1-107">The following code example shows methods for creating bindings for the various authentication modes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc8e1-108">Une fois qu'une instance de l'objet <xref:System.ServiceModel.Channels.SecurityBindingElement> est créée, plusieurs propriétés sont immuables, telles que <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> et <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="dc8e1-108">Once an instance of the <xref:System.ServiceModel.Channels.SecurityBindingElement> object is created, a number of properties are immutable, such as <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> and <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span></span> <span data-ttu-id="dc8e1-109">L'appel de `set` sur de telles propriétés ne les modifie pas.</span><span class="sxs-lookup"><span data-stu-id="dc8e1-109">Calling `set` on such properties does not change them.</span></span>  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="dc8e1-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc8e1-110">See also</span></span>

- [<span data-ttu-id="dc8e1-111">Modes d’authentification SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="dc8e1-111">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
- [<span data-ttu-id="dc8e1-112">Guide pratique pour Créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="dc8e1-112">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
