---
title: 'Procédure : créer un SecurityBindingElement pour un mode d’authentification spécifié'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
ms.openlocfilehash: 7b71224c74d7e9e766fb17101219dc5718d5d6a6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286433"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a><span data-ttu-id="81666-102">Procédure : créer un SecurityBindingElement pour un mode d’authentification spécifié</span><span class="sxs-lookup"><span data-stu-id="81666-102">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>

<span data-ttu-id="81666-103">Windows Communication Foundation (WCF) fournit plusieurs modes par lesquels les clients et les services s’authentifient l’un l’autre.</span><span class="sxs-lookup"><span data-stu-id="81666-103">Windows Communication Foundation (WCF) provides several modes by which clients and services authenticate to one another.</span></span> <span data-ttu-id="81666-104">Vous pouvez créer des éléments de liaison de sécurité pour ces modes d'authentification en utilisant des méthodes statiques sur la classe <xref:System.ServiceModel.Channels.SecurityBindingElement> ou par la configuration, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="81666-104">You can create security binding elements for these authentication modes by using static methods on the <xref:System.ServiceModel.Channels.SecurityBindingElement> class or through configuration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="81666-105">Pour plus d’informations sur les 18 modes d’authentification, consultez [modes d’authentification SecurityBindingElement](securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="81666-105">For more information about the 18 authentication modes, see [SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81666-106"> Exemple</span><span class="sxs-lookup"><span data-stu-id="81666-106">Example</span></span>  

 <span data-ttu-id="81666-107">L’exemple de code suivant présente des méthodes pour créer des liaisons pour les divers modes d’authentification.</span><span class="sxs-lookup"><span data-stu-id="81666-107">The following code example shows methods for creating bindings for the various authentication modes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81666-108">Une fois qu'une instance de l'objet <xref:System.ServiceModel.Channels.SecurityBindingElement> est créée, plusieurs propriétés sont immuables, telles que <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> et <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="81666-108">Once an instance of the <xref:System.ServiceModel.Channels.SecurityBindingElement> object is created, a number of properties are immutable, such as <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> and <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span></span> <span data-ttu-id="81666-109">L'appel de `set` sur de telles propriétés ne les modifie pas.</span><span class="sxs-lookup"><span data-stu-id="81666-109">Calling `set` on such properties does not change them.</span></span>  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="81666-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81666-110">See also</span></span>

- [<span data-ttu-id="81666-111">Modes d'authentification SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="81666-111">SecurityBindingElement Authentication Modes</span></span>](securitybindingelement-authentication-modes.md)
- [<span data-ttu-id="81666-112">Procédure : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="81666-112">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
