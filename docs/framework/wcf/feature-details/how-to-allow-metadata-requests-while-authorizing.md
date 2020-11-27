---
title: 'Procédure : autoriser les requêtes de métadonnées pendant l’autorisation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 9acc007ea7837f7b8e6c958fa81547fe4fa5b2c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257611"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="e671f-102">Procédure : autoriser les requêtes de métadonnées pendant l’autorisation</span><span class="sxs-lookup"><span data-stu-id="e671f-102">How To: Allow Metadata Requests While Authorizing</span></span>

<span data-ttu-id="e671f-103">Pendant l'autorisation personnalisée, il peut être nécessaire d'autoriser le traitement d'une demande de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e671f-103">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="e671f-104">La rubrique suivante présente les étapes de validation d'une telle demande.</span><span class="sxs-lookup"><span data-stu-id="e671f-104">The following topic walks through the steps to validate such a request.</span></span>  
  
 <span data-ttu-id="e671f-105">Pour plus d’informations sur l’autorisation Windows Communication Foundation (WCF), consultez [authorization](authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="e671f-105">For more information about Windows Communication Foundation (WCF) authorization, see [Authorization](authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="e671f-106">Pour autoriser les demandes de métadonnées pendant l'autorisation</span><span class="sxs-lookup"><span data-stu-id="e671f-106">To allow metadata requests during authorization</span></span>  
  
1. <span data-ttu-id="e671f-107">Créez une extension de la classe <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="e671f-107">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2. <span data-ttu-id="e671f-108">Remplacez la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> .</span><span class="sxs-lookup"><span data-stu-id="e671f-108">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="e671f-109">La méthode retourne la valeur `true` ou `false` selon que l'autorisation est accordée ou non.</span><span class="sxs-lookup"><span data-stu-id="e671f-109">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="e671f-110">Les informations relatives à la procédure en cours se trouvent dans le <xref:System.ServiceModel.OperationContext> passé comme paramètre à la méthode.</span><span class="sxs-lookup"><span data-stu-id="e671f-110">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3. <span data-ttu-id="e671f-111">Dans la substitution, vérifiez le nom de contrat, l'espace de noms et l'action comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e671f-111">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="e671f-112">Si les conditions sont valides, retournez `true.`</span><span class="sxs-lookup"><span data-stu-id="e671f-112">If the conditions are valid, then return `true.`</span></span>  
  
4. <span data-ttu-id="e671f-113">Utilisez le point d'extensibilité pour employer la classe.</span><span class="sxs-lookup"><span data-stu-id="e671f-113">Use the extensibility point to employ the class.</span></span> <span data-ttu-id="e671f-114">Pour plus d’informations, consultez [Comment : créer un gestionnaire d’autorisations personnalisé pour un service](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="e671f-114">For more information, see [How to: Create a Custom Authorization Manager for a Service](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e671f-115"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e671f-115">Example</span></span>  

 <span data-ttu-id="e671f-116">L'exemple suivant illustre une substitution de la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>.</span><span class="sxs-lookup"><span data-stu-id="e671f-116">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e671f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e671f-117">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="e671f-118">Autorisation</span><span class="sxs-lookup"><span data-stu-id="e671f-118">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="e671f-119">Gestion des revendications et autorisation avec le modèle d'identité</span><span class="sxs-lookup"><span data-stu-id="e671f-119">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
