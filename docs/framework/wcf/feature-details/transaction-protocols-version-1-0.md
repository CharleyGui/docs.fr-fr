---
title: Protocoles de transaction version 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: 7b1cfc21a1361cee3027fd5a61ec61a4a0a998b7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246236"
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="ad698-102">Protocoles de transaction version 1.0</span><span class="sxs-lookup"><span data-stu-id="ad698-102">Transaction Protocols version 1.0</span></span>

<span data-ttu-id="ad698-103">Windows Communication Foundation (WCF) version 1 implémente la version 1,0 de la transaction WS-Atomic et des protocoles de WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="ad698-103">Windows Communication Foundation (WCF) version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="ad698-104">Pour plus d’informations sur la version 1,1, consultez [protocoles de transaction](transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="ad698-104">For more information about version 1.1, see [Transaction Protocols](transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="ad698-105">Spécification/Document</span><span class="sxs-lookup"><span data-stu-id="ad698-105">Specification/Document</span></span>|<span data-ttu-id="ad698-106">Lien</span><span class="sxs-lookup"><span data-stu-id="ad698-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="ad698-107">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="ad698-107">WS-Coordination</span></span>|<http://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|<span data-ttu-id="ad698-108">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="ad698-108">WS-AtomicTransaction</span></span>|<http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 <span data-ttu-id="ad698-109">L’interopérabilité sur ces spécifications de protocole est requise à deux niveaux : entre les applications et entre les gestionnaires de transactions (consultez la figure suivante).</span><span class="sxs-lookup"><span data-stu-id="ad698-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="ad698-110">Les spécifications décrivent de manière très détaillée les formats de message et l'échange de messages pour les deux niveaux d'interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="ad698-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="ad698-111">Une certain niveau de sécurité, de fiabilité et des encodages pour l'échange interapplication s'appliquent de la même manière que pour l'échange entre applications normal.</span><span class="sxs-lookup"><span data-stu-id="ad698-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="ad698-112">Toutefois, l'interopérabilité réussie entre les gestionnaires de transactions requiert un contrat sur la liaison spécifique, car il n'est généralement pas configuré par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ad698-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="ad698-113">Cette rubrique décrit une composition de la spécification WS-AT (WS-Atomic Transaction) avec sécurité et décrit la liaison sécurisée utilisée pour la communication entre les gestionnaires de transactions.</span><span class="sxs-lookup"><span data-stu-id="ad698-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="ad698-114">L'approche décrite dans ce document a été testée avec succès avec d'autres implémentations de WS-AT et WS-Coordination, dont IBM, IONA, Sun Microsystems, etc.</span><span class="sxs-lookup"><span data-stu-id="ad698-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="ad698-115">La figure suivante illustre l’interopérabilité entre deux gestionnaires de transactions, le gestionnaire de transactions 1 et le gestionnaire de transactions 2, ainsi que deux applications, application 1 et application 2 :</span><span class="sxs-lookup"><span data-stu-id="ad698-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![Capture d’écran montrant l’interaction entre les gestionnaires de transactions.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="ad698-117">Examinons un scénario WS-Coordination/WS-Atomic Transaction classique avec un Initiateur (I) et un Participant (P).</span><span class="sxs-lookup"><span data-stu-id="ad698-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="ad698-118">L’Initiateur et le Participant ont des Gestionnaires de transactions (ITM et PTM, respectivement).</span><span class="sxs-lookup"><span data-stu-id="ad698-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="ad698-119">La validation en deux phases est désignée sous le terme « 2PC » dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ad698-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad698-120">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="ad698-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="ad698-121">12. réponse aux messages d’application</span><span class="sxs-lookup"><span data-stu-id="ad698-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="ad698-122">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="ad698-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="ad698-123">13. validation (achèvement)</span><span class="sxs-lookup"><span data-stu-id="ad698-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="ad698-124">3. inscrire (achèvement)</span><span class="sxs-lookup"><span data-stu-id="ad698-124">3. Register (Completion)</span></span>|<span data-ttu-id="ad698-125">14. Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="ad698-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="ad698-126">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="ad698-126">4. RegisterResponse</span></span>|<span data-ttu-id="ad698-127">15. Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="ad698-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="ad698-128">5. message de l’application</span><span class="sxs-lookup"><span data-stu-id="ad698-128">5. Application Message</span></span>|<span data-ttu-id="ad698-129">16. préparé (2PC)</span><span class="sxs-lookup"><span data-stu-id="ad698-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="ad698-130">6. CreateCoordinationContext avec contexte</span><span class="sxs-lookup"><span data-stu-id="ad698-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="ad698-131">17. Prepared (2PC)</span><span class="sxs-lookup"><span data-stu-id="ad698-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="ad698-132">7. inscrire (durable)</span><span class="sxs-lookup"><span data-stu-id="ad698-132">7. Register (Durable)</span></span>|<span data-ttu-id="ad698-133">18. validé (achèvement)</span><span class="sxs-lookup"><span data-stu-id="ad698-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="ad698-134">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="ad698-134">8. RegisterResponse</span></span>|<span data-ttu-id="ad698-135">19. Commit (2PC)</span><span class="sxs-lookup"><span data-stu-id="ad698-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="ad698-136">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="ad698-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="ad698-137">20. Commit (2PC)</span><span class="sxs-lookup"><span data-stu-id="ad698-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="ad698-138">10. Register (durable)</span><span class="sxs-lookup"><span data-stu-id="ad698-138">10. Register (Durable)</span></span>|<span data-ttu-id="ad698-139">21. validé (2PC)</span><span class="sxs-lookup"><span data-stu-id="ad698-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="ad698-140">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="ad698-140">11. RegisterResponse</span></span>|<span data-ttu-id="ad698-141">22. validé (2PC)</span><span class="sxs-lookup"><span data-stu-id="ad698-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="ad698-142">Ce document décrit une composition de la spécification WS-AtomicTransaction avec sécurité et décrit la liaison sécurisée utilisée pour la communication entre les gestionnaires de transactions.</span><span class="sxs-lookup"><span data-stu-id="ad698-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="ad698-143">L'approche décrite dans ce document a été testée avec succès avec d'autres implémentations de WS-AT et WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="ad698-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="ad698-144">La figure et le tableau présentent quatre classes de messages du point de vue de sécurité :</span><span class="sxs-lookup"><span data-stu-id="ad698-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="ad698-145">Messages d'activation (CreateCoordinationContext et CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="ad698-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="ad698-146">Messages d'inscription (Register et RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="ad698-146">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="ad698-147">Messages de protocole (Prepare, Rollback, Commit, Aborted, etc).</span><span class="sxs-lookup"><span data-stu-id="ad698-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="ad698-148">Messages d'application</span><span class="sxs-lookup"><span data-stu-id="ad698-148">Application messages.</span></span>  
  
 <span data-ttu-id="ad698-149">Les trois premières classes de message sont considérées comme des messages de gestionnaire de transactions et leur configuration de liaison est décrite dans la section « Échange de messages d’application » développée ultérieurement dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ad698-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="ad698-150">La quatrième classe de message concerne les messages interapplication et est décrite dans la section « Exemples de message » développée ultérieurement dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ad698-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="ad698-151">Cette section décrit les liaisons de protocole utilisées pour chacune de ces classes par WCF.</span><span class="sxs-lookup"><span data-stu-id="ad698-151">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="ad698-152">Les espaces de noms XML suivants et préfixes associés sont utilisés dans l'ensemble de ce document.</span><span class="sxs-lookup"><span data-stu-id="ad698-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="ad698-153">Préfixe</span><span class="sxs-lookup"><span data-stu-id="ad698-153">Prefix</span></span>|<span data-ttu-id="ad698-154">URI d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="ad698-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="ad698-155">s11</span><span class="sxs-lookup"><span data-stu-id="ad698-155">s11</span></span>|`http://schemas.xmlsoap.org/soap/envelope`|  
|<span data-ttu-id="ad698-156">wsa</span><span class="sxs-lookup"><span data-stu-id="ad698-156">wsa</span></span>|`http://www.w3.org/2004/08/addressing`|  
|<span data-ttu-id="ad698-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="ad698-157">wscoor</span></span>|`http://schemas.xmlsoap.org/ws/2004/10/wscoor`|  
|<span data-ttu-id="ad698-158">wsat</span><span class="sxs-lookup"><span data-stu-id="ad698-158">wsat</span></span>|`http://schemas.xmlsoap.org/ws/2004/10/wsat`|  
|<span data-ttu-id="ad698-159">t</span><span class="sxs-lookup"><span data-stu-id="ad698-159">t</span></span>|`http://schemas.xmlsoap.org/ws/2005/02/trust`|  
|<span data-ttu-id="ad698-160">o</span><span class="sxs-lookup"><span data-stu-id="ad698-160">o</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd`|  
|<span data-ttu-id="ad698-161">xsd</span><span class="sxs-lookup"><span data-stu-id="ad698-161">xsd</span></span>|`http://www.w3.org/2001/XMLSchema`|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="ad698-162">Liaisons de gestionnaire de transactions</span><span class="sxs-lookup"><span data-stu-id="ad698-162">Transaction Manager Bindings</span></span>  

 <span data-ttu-id="ad698-163">R1001 : les gestionnaires de transactions doivent utiliser SOAP 1.1 et WS-Addressing 2004/08 pour les échanges de message WS-Atomic Transaction et WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="ad698-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="ad698-164">Les messages d’application ne sont pas contraints à ces liaisons et sont décrits ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="ad698-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="ad698-165">Liaison HTTPS de gestionnaire de transactions</span><span class="sxs-lookup"><span data-stu-id="ad698-165">Transaction Manager HTTPS Binding</span></span>  

 <span data-ttu-id="ad698-166">La liaison HTTPS de gestionnaire de transactions s'appuie uniquement sur le transport de sécurité pour assurer la sécurité et établir la confiance entre chaque paire expéditeur-récepteur dans l'arborescence de transactions.</span><span class="sxs-lookup"><span data-stu-id="ad698-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="ad698-167">Configuration du transport HTTPS</span><span class="sxs-lookup"><span data-stu-id="ad698-167">HTTPS Transport Configuration</span></span>  

 <span data-ttu-id="ad698-168">Les certificats X.509 permettent d'établir l'identité de gestionnaire de transactions.</span><span class="sxs-lookup"><span data-stu-id="ad698-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="ad698-169">L'authentification client/serveur est requise, et l'autorisation client/serveur est considérée comme un détail d'implémentation :</span><span class="sxs-lookup"><span data-stu-id="ad698-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="ad698-170">R1111 : les certificats X.509 présentés sur le câble doivent avoir un nom de sujet qui correspond au nom de domaine complet de l'ordinateur d'origine.</span><span class="sxs-lookup"><span data-stu-id="ad698-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="ad698-171">B1112 : le DNS doit être fonctionnel entre chaque paire expéditeur-récepteur du système pour que les vérifications du nom de sujet X.509 réussissent.</span><span class="sxs-lookup"><span data-stu-id="ad698-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="ad698-172">Configuration de liaison d'activation et d'inscription</span><span class="sxs-lookup"><span data-stu-id="ad698-172">Activation and Registration Binding Configuration</span></span>  

 <span data-ttu-id="ad698-173">WCF requiert une liaison duplex de demande/réponse avec corrélation sur HTTPs.</span><span class="sxs-lookup"><span data-stu-id="ad698-173">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="ad698-174">(Pour plus d'informations sur la corrélation et les descriptions des modèles d'échange de messages demande/réponse, consultez WS-Atomic Transaction, section 8.)</span><span class="sxs-lookup"><span data-stu-id="ad698-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="ad698-175">Configuration de liaison de protocole 2PC</span><span class="sxs-lookup"><span data-stu-id="ad698-175">2PC Protocol Binding Configuration</span></span>  

 <span data-ttu-id="ad698-176">WCF prend en charge les messages unidirectionnels (datagrammes) sur HTTPs.</span><span class="sxs-lookup"><span data-stu-id="ad698-176">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="ad698-177">La corrélation au sein des messages est considérée comme un détail d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="ad698-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="ad698-178">B2131 : les implémentations doivent prendre en charge `wsa:ReferenceParameters` comme décrit dans WS-Addressing pour obtenir la corrélation des messages 2PC de WCF.</span><span class="sxs-lookup"><span data-stu-id="ad698-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="ad698-179">Liaison de sécurité mixte de gestionnaire de transactions</span><span class="sxs-lookup"><span data-stu-id="ad698-179">Transaction Manager Mixed Security Binding</span></span>  

 <span data-ttu-id="ad698-180">Il s’agit d’une liaison alternative (en mode mixte) qui utilise la sécurité de transport associée à l' WS-Coordination modèle de jeton émis à des fins d’établissement d’identité.</span><span class="sxs-lookup"><span data-stu-id="ad698-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="ad698-181">L’activation et l’inscription sont les seuls éléments qui diffèrent entre les deux liaisons.</span><span class="sxs-lookup"><span data-stu-id="ad698-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="ad698-182">Configuration du transport HTTPS</span><span class="sxs-lookup"><span data-stu-id="ad698-182">HTTPS Transport Configuration</span></span>  

 <span data-ttu-id="ad698-183">Les certificats X.509 permettent d'établir l'identité de gestionnaire de transactions.</span><span class="sxs-lookup"><span data-stu-id="ad698-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="ad698-184">L'authentification client/serveur est requise, et l'autorisation client/serveur est considérée comme un détail d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="ad698-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="ad698-185">Configuration de liaison de message d’activation</span><span class="sxs-lookup"><span data-stu-id="ad698-185">Activation Message Binding Configuration</span></span>  

 <span data-ttu-id="ad698-186">En général, les messages d’activation ne participent pas à l’interopérabilité car ils se produisent habituellement entre une application et son gestionnaire de transactions local.</span><span class="sxs-lookup"><span data-stu-id="ad698-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="ad698-187">B1221 : WCF utilise la liaison HTTPs duplex (décrite dans [protocoles de messagerie](messaging-protocols.md)) pour les messages d’activation.</span><span class="sxs-lookup"><span data-stu-id="ad698-187">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="ad698-188">Les messages de demande et de réponse sont corrélés à l'aide de WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="ad698-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="ad698-189">La spécification WS-Atomic Transaction, section 8, fournit des informations supplémentaires sur la corrélation et les modèles d'échange de messages.</span><span class="sxs-lookup"><span data-stu-id="ad698-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="ad698-190">R1222 : après réception de `CreateCoordinationContext`, le coordinateur doit émettre `SecurityContextToken` avec le `STx` secret associé.</span><span class="sxs-lookup"><span data-stu-id="ad698-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="ad698-191">Ce jeton est retourné à l'intérieur d'un en-tête `t:IssuedTokens` selon la spécification WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="ad698-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="ad698-192">R1223 : si l'activation se produit dans un contexte de coordination existant, l'en-tête `t:IssuedTokens` avec `SecurityContextToken` associé au contexte existant doit transmettre sur le message `CreateCoordinationContext`.</span><span class="sxs-lookup"><span data-stu-id="ad698-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="ad698-193">Un nouvel `t:IssuedTokens` en-tête doit être généré pour être attaché au `wscoor:CreateCoordinationContextResponse` message sortant.</span><span class="sxs-lookup"><span data-stu-id="ad698-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="ad698-194">Configuration de liaison de message d'inscription</span><span class="sxs-lookup"><span data-stu-id="ad698-194">Registration Message Binding Configuration</span></span>  

 <span data-ttu-id="ad698-195">B1231 : WCF utilise la liaison HTTPs duplex (décrite dans [protocoles de messagerie](messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="ad698-195">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](messaging-protocols.md)).</span></span> <span data-ttu-id="ad698-196">Les messages de demande et de réponse sont corrélés à l'aide de WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="ad698-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="ad698-197">WS-AtomicTransaction, section 8, fournit des informations supplémentaires sur la corrélation et des descriptions des modèles d’échange de messages.</span><span class="sxs-lookup"><span data-stu-id="ad698-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="ad698-198">R1232 : `wscoor:Register` les messages sortants doivent utiliser le `IssuedTokenOverTransport` mode d’authentification décrit dans [protocoles de sécurité](security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="ad698-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](security-protocols.md).</span></span>  
  
 <span data-ttu-id="ad698-199">L' `wsse:Timestamp` élément doit être signé à l’aide du `SecurityContextToken STx` émis.</span><span class="sxs-lookup"><span data-stu-id="ad698-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="ad698-200">Cette signature est une preuve de possession du jeton associée à une transaction spécifique et est utilisée pour authentifier un participant qui s’inscrit à la transaction.</span><span class="sxs-lookup"><span data-stu-id="ad698-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="ad698-201">Le message RegistrationResponse est renvoyé sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ad698-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="ad698-202">Configuration de liaison de protocole 2PC</span><span class="sxs-lookup"><span data-stu-id="ad698-202">2PC Protocol Binding Configuration</span></span>  

 <span data-ttu-id="ad698-203">WCF prend en charge les messages unidirectionnels (datagrammes) sur HTTPs.</span><span class="sxs-lookup"><span data-stu-id="ad698-203">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="ad698-204">La corrélation au sein des messages est considérée comme un détail d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="ad698-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="ad698-205">B2131 : les implémentations doivent prendre en charge `wsa:ReferenceParameters` comme décrit dans WS-Addressing pour obtenir la corrélation des messages 2PC de WCF.</span><span class="sxs-lookup"><span data-stu-id="ad698-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="ad698-206">Échange de messages d'application</span><span class="sxs-lookup"><span data-stu-id="ad698-206">Application Message Exchange</span></span>  

 <span data-ttu-id="ad698-207">Les applications sont libres d’utiliser n’importe quelle liaison spécifique pour les messages interapplication, tant que la liaison satisfait aux exigences de sécurité suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad698-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="ad698-208">R2001 : les messages interapplication doivent transmettre l'en-tête `t:IssuedTokens` avec `CoordinationContext` dans l'en-tête du message.</span><span class="sxs-lookup"><span data-stu-id="ad698-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="ad698-209">R2002 : l'intégrité et la confidentialité de `t:IssuedToken` doivent être assurées.</span><span class="sxs-lookup"><span data-stu-id="ad698-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="ad698-210">L'en-tête `CoordinationContext` contient `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="ad698-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="ad698-211">Bien que la définition de `xsd:AnyURI` autorise l’utilisation d’URI absolus et relatifs, WCF prend uniquement en charge `wscoor:Identifiers` , qui sont des URI absolus.</span><span class="sxs-lookup"><span data-stu-id="ad698-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="ad698-212">Si le `wscoor:Identifier` du `wscoor:CoordinationContext` est un URI relatif, les erreurs sont retournées à partir des services WCF transactionnels.</span><span class="sxs-lookup"><span data-stu-id="ad698-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="ad698-213">Exemples de message</span><span class="sxs-lookup"><span data-stu-id="ad698-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="ad698-214">Messages de demande/réponse CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="ad698-214">CreateCoordinationContext Request/Response Messages</span></span>  

 <span data-ttu-id="ad698-215">Les messages suivants suivent un modèle de demande/réponse.</span><span class="sxs-lookup"><span data-stu-id="ad698-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="ad698-216">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="ad698-216">CreateCoordinationContext</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="ad698-217">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="ad698-217">CreateCoordinationContextResponse</span></span>  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="ad698-218">Messages d'inscription</span><span class="sxs-lookup"><span data-stu-id="ad698-218">Registration Messages</span></span>  

 <span data-ttu-id="ad698-219">Les messages suivants sont des messages d'inscription.</span><span class="sxs-lookup"><span data-stu-id="ad698-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="ad698-220">S’inscrire</span><span class="sxs-lookup"><span data-stu-id="ad698-220">Register</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response"></a><span data-ttu-id="ad698-221">Register Response</span><span class="sxs-lookup"><span data-stu-id="ad698-221">Register Response</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="ad698-222">Messages de protocole de validation à deux phases</span><span class="sxs-lookup"><span data-stu-id="ad698-222">Two Phase Commit Protocol Messages</span></span>  

 <span data-ttu-id="ad698-223">Le message suivant concerne le protocole de validation en deux phases (2PC).</span><span class="sxs-lookup"><span data-stu-id="ad698-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="ad698-224">Commit</span><span class="sxs-lookup"><span data-stu-id="ad698-224">Commit</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="application-messages"></a><span data-ttu-id="ad698-225">Messages d'application</span><span class="sxs-lookup"><span data-stu-id="ad698-225">Application Messages</span></span>  

 <span data-ttu-id="ad698-226">Les messages suivants sont des messages d'application.</span><span class="sxs-lookup"><span data-stu-id="ad698-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="ad698-227">Message d'application - demande</span><span class="sxs-lookup"><span data-stu-id="ad698-227">Application message-Request</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken
          wssu:Id="IA_Certificate"
          ValueType="...#X509v3"
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader>  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader>
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->
    <e:EncryptedData Id="encrypted_body"
           Type="http://www.w3.org/2001/04/xmlenc#Content"
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```
