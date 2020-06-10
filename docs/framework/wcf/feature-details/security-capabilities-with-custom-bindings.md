---
title: Fonctionnalités de sécurité avec des liaisons personnalisées
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 48d17543f2b133c74bcfa82cfe1a2a0de28b1d01
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595191"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="91484-102">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="91484-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="91484-103">Vous pouvez effectuer la plupart des tâches de sécurité courantes en utilisant l'une des liaisons fournies par le système.</span><span class="sxs-lookup"><span data-stu-id="91484-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="91484-104">Toutefois, si vous avez besoin de plus de contrôle, vous pouvez créer une liaison personnalisée à l'aide de <xref:System.ServiceModel.Channels.SecurityBindingElement>, comme expliqué dans les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="91484-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="91484-105">Pour plus d’informations sur les liaisons personnalisées, consultez [liaisons personnalisées](../extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="91484-105">For more information about custom bindings, see [Custom Bindings](../extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91484-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="91484-106">In This Section</span></span>  
 [<span data-ttu-id="91484-107">Modes d'authentification SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="91484-107">SecurityBindingElement Authentication Modes</span></span>](securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="91484-108">Décrit les modes d’authentification possibles avec une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="91484-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="91484-109">Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="91484-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="91484-110">Décrit les étapes de base pour créer une liaison personnalisée avec un élément de sécurité.</span><span class="sxs-lookup"><span data-stu-id="91484-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="91484-111">Comment : créer un SecurityBindingElement pour un mode d'authentification spécifié</span><span class="sxs-lookup"><span data-stu-id="91484-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="91484-112">Décrit comment créer un élément de sécurité pour un mode d'authentification spécifié.</span><span class="sxs-lookup"><span data-stu-id="91484-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="91484-113">Comment : désactiver des sessions sécurisées sur une classe WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="91484-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="91484-114">Décrit comment désactiver des sessions sécurisées lors de la création d'un service FS.</span><span class="sxs-lookup"><span data-stu-id="91484-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="91484-115">Comment : activer la détection de relecture des messages</span><span class="sxs-lookup"><span data-stu-id="91484-115">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="91484-116">Décrit comment déterminer le moment où une attaque par relecture se produit.</span><span class="sxs-lookup"><span data-stu-id="91484-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="91484-117">Comment : créer une information d'identification de prise en charge</span><span class="sxs-lookup"><span data-stu-id="91484-117">How to: Create a Supporting Credential</span></span>](how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="91484-118">Décrit comment fournir des informations d'identification de prise en charge à un service, si ce dernier en a besoin.</span><span class="sxs-lookup"><span data-stu-id="91484-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="91484-119">Comment : configurer une confirmation de signature</span><span class="sxs-lookup"><span data-stu-id="91484-119">How to: Set Up a Signature Confirmation</span></span>](how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="91484-120">Décrit les étapes permettant de confirmer des signatures lors de la signature numérique de messages.</span><span class="sxs-lookup"><span data-stu-id="91484-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="91484-121">Comment : définir une inclinaison de l'horloge maximale</span><span class="sxs-lookup"><span data-stu-id="91484-121">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="91484-122">Décrit comment définir la différence de temps maximale autorisée entre un service et un client.</span><span class="sxs-lookup"><span data-stu-id="91484-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="91484-123">Comment : désactiver le chiffrement des signatures numériques</span><span class="sxs-lookup"><span data-stu-id="91484-123">How to: Disable Encryption of Digital Signatures</span></span>](how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="91484-124">Décrit les avantages de la désactivation du chiffrement des signatures numériques en matière de performances.</span><span class="sxs-lookup"><span data-stu-id="91484-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="91484-125">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="91484-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="91484-126">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="91484-126">Related Sections</span></span>  
 [<span data-ttu-id="91484-127">Fonctionnement des niveaux de protection</span><span class="sxs-lookup"><span data-stu-id="91484-127">Understanding Protection Level</span></span>](../understanding-protection-level.md)  
  
 [<span data-ttu-id="91484-128">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="91484-128">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="91484-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91484-129">See also</span></span>

- [<span data-ttu-id="91484-130">Liaisons et sécurité</span><span class="sxs-lookup"><span data-stu-id="91484-130">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="91484-131">Présentation de la sécurité</span><span class="sxs-lookup"><span data-stu-id="91484-131">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="91484-132">Liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="91484-132">System-Provided Bindings</span></span>](../system-provided-bindings.md)
