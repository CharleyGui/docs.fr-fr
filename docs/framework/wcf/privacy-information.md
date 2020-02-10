---
title: Informations de confidentialité relatives à Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: b724ff1ce85442f64980fdc972188705992d5a4f
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094980"
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="524ad-102">Informations de confidentialité relatives à Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="524ad-102">Windows Communication Foundation Privacy Information</span></span>
<span data-ttu-id="524ad-103">Microsoft s’engage à protéger la confidentialité de l’utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="524ad-103">Microsoft is committed to protecting end user privacy.</span></span> <span data-ttu-id="524ad-104">Lorsque vous générez une application à l’aide de Windows Communication Foundation (WCF), version 3,0, votre application peut avoir un impact sur la confidentialité de vos utilisateurs finaux.</span><span class="sxs-lookup"><span data-stu-id="524ad-104">When you build an application using Windows Communication Foundation (WCF), version 3.0, your application may impact your end users' privacy.</span></span> <span data-ttu-id="524ad-105">Par exemple, votre application peut recueillir des informations de contact utilisateur de manière explicite ou elle peut demander ou envoyer des informations sur Internet à votre site Web.</span><span class="sxs-lookup"><span data-stu-id="524ad-105">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="524ad-106">Si vous incorporez la technologie Microsoft dans votre application, cette technologie peut avoir son propre comportement qui peut affecter la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="524ad-106">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> <span data-ttu-id="524ad-107">WCF n’envoie pas d’informations à Microsoft à partir de votre application, à moins que vous ou l’utilisateur final ne choisissiez de nous l’envoyer.</span><span class="sxs-lookup"><span data-stu-id="524ad-107">WCF does not send any information to Microsoft from your application unless you or the end user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="524ad-108">WCF en bref</span><span class="sxs-lookup"><span data-stu-id="524ad-108">WCF in Brief</span></span>  
 <span data-ttu-id="524ad-109">WCF est une infrastructure de messagerie distribuée utilisant l’infrastructure de Microsoft .NET qui permet aux développeurs de créer des applications distribuées.</span><span class="sxs-lookup"><span data-stu-id="524ad-109">WCF is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="524ad-110">Les messages transmis entre deux applications contiennent des informations d'en-tête et de corps.</span><span class="sxs-lookup"><span data-stu-id="524ad-110">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="524ad-111">Les en-têtes peuvent contenir le routage des messages, des informations de sécurité, des transactions et d’autres éléments, en fonction des services utilisés par l’application.</span><span class="sxs-lookup"><span data-stu-id="524ad-111">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="524ad-112">Les messages sont en général chiffrés par défaut.</span><span class="sxs-lookup"><span data-stu-id="524ad-112">Messages are typically encrypted by default.</span></span> <span data-ttu-id="524ad-113">L'unique exception concerne l'utilisation du `BasicHttpBinding`, qui a été conçu pour une utilisation avec des services Web hérités non sécurisés.</span><span class="sxs-lookup"><span data-stu-id="524ad-113">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="524ad-114">En tant que concepteur d'applications, vous êtes responsable de la conception finale.</span><span class="sxs-lookup"><span data-stu-id="524ad-114">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="524ad-115">Les messages dans le corps SOAP contiennent des données spécifiques à l’application ; Toutefois, ces données, telles que les informations personnelles définies par l’application, peuvent être sécurisées à l’aide des fonctionnalités de chiffrement ou de confidentialité WCF.</span><span class="sxs-lookup"><span data-stu-id="524ad-115">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using WCF encryption or confidentiality features.</span></span> <span data-ttu-id="524ad-116">Les sections suivantes décrivent les fonctionnalités qui peuvent avoir un impact sur la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="524ad-116">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="524ad-117">Messagerie</span><span class="sxs-lookup"><span data-stu-id="524ad-117">Messaging</span></span>  
 <span data-ttu-id="524ad-118">Chaque message WCF possède un en-tête d’adresse qui spécifie la destination du message et l’emplacement où la réponse doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="524ad-118">Each WCF message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="524ad-119">Le composant adresse d'une adresse de point de terminaison est un URI (Uniform Resource Identifier) qui identifie le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="524ad-119">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="524ad-120">L'adresse peut être une adresse réseau ou une adresse logique.</span><span class="sxs-lookup"><span data-stu-id="524ad-120">The address can be a network address or a logical address.</span></span> <span data-ttu-id="524ad-121">L'adresse peut inclure le nom de l'ordinateur (nom d'hôte, nom de domaine complet) et une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="524ad-121">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="524ad-122">L’adresse de point de terminaison peut également contenir un identificateur global unique (GUID) ou une collection de GUID pour l’adressage temporaire utilisé pour distinguer chaque adresse.</span><span class="sxs-lookup"><span data-stu-id="524ad-122">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="524ad-123">Chaque message contient un ID de message qui est un GUID.</span><span class="sxs-lookup"><span data-stu-id="524ad-123">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="524ad-124">Cette fonctionnalité respecte la norme de référence WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="524ad-124">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="524ad-125">La couche de messagerie WCF n’écrit aucune information personnelle sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="524ad-125">The WCF messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="524ad-126">Toutefois, elle peut propager des informations personnelles au niveau du réseau si un développeur de service a créé un service qui expose de telles informations (par exemple, en utilisant le nom d'une personne dans un nom de point de terminaison, ou en incluant des informations personnelles dans le Web Services Description Language du point de terminaison sans exiger que les clients utilisent https pour accéder au WSDL).</span><span class="sxs-lookup"><span data-stu-id="524ad-126">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="524ad-127">En outre, si un développeur exécute l’outil [ServiceModel Metadata Utility Tool (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) sur un point de terminaison qui expose des informations personnelles, la sortie de l’outil peut contenir ces informations et le fichier de sortie est écrit sur le disque dur local.</span><span class="sxs-lookup"><span data-stu-id="524ad-127">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="524ad-128">Hébergement</span><span class="sxs-lookup"><span data-stu-id="524ad-128">Hosting</span></span>  
 <span data-ttu-id="524ad-129">La fonctionnalité d’hébergement de WCF permet aux applications de démarrer à la demande ou d’activer le partage de port entre plusieurs applications.</span><span class="sxs-lookup"><span data-stu-id="524ad-129">The hosting feature in WCF allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="524ad-130">Une application WCF peut être hébergée dans Internet Information Services (IIS), similaire à ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="524ad-130">A WCF application can be hosted in Internet Information Services (IIS), similar to ASP.NET.</span></span>  
  
 <span data-ttu-id="524ad-131">L'hébergement n'expose aucune information spécifique sur le réseau et ne conserve aucune donnée sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="524ad-131">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="524ad-132">Sécurité des messages</span><span class="sxs-lookup"><span data-stu-id="524ad-132">Message Security</span></span>  
 <span data-ttu-id="524ad-133">La sécurité WCF offre des fonctionnalités de sécurité pour les applications de messagerie.</span><span class="sxs-lookup"><span data-stu-id="524ad-133">WCF security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="524ad-134">Les fonctions de sécurité fournies incluent l'authentification et l'autorisation.</span><span class="sxs-lookup"><span data-stu-id="524ad-134">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="524ad-135">L'authentification est exécutée en passant des informations d'identification entre les clients et services.</span><span class="sxs-lookup"><span data-stu-id="524ad-135">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="524ad-136">L'authentification peut s'effectuer par le biais de la sécurité de niveau transport ou par le biais de la sécurité de niveau message SOAP, comme suit :</span><span class="sxs-lookup"><span data-stu-id="524ad-136">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
- <span data-ttu-id="524ad-137">Avec la sécurité des messages SOAP, l'authentification est exécutée par le biais des informations d'identification telles que nom d'utilisateur/mots de passe, certificats X.509, tickets Kerberos et jetons SAML, qui peuvent tous contenir des informations personnelles selon l'émetteur.</span><span class="sxs-lookup"><span data-stu-id="524ad-137">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
- <span data-ttu-id="524ad-138">Avec la sécurité de transport, l’authentification est effectuée par le biais des mécanismes d’authentification de transport traditionnels tels que les modèles d’authentification HTTP (De base, Digest, Négocier, Autorisation Windows Intégrée, NTLM, Aucun et Anonyme) et l’authentification par formulaire.</span><span class="sxs-lookup"><span data-stu-id="524ad-138">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="524ad-139">L'authentification peut entraîner l'établissement d'une session sécurisée entre les points de terminaison communicants.</span><span class="sxs-lookup"><span data-stu-id="524ad-139">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="524ad-140">La session est identifiée par un GUID valide pendant toute la durée de vie de la session de sécurité.</span><span class="sxs-lookup"><span data-stu-id="524ad-140">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="524ad-141">Le tableau suivant indique ce qui est conservé, et à quel emplacement.</span><span class="sxs-lookup"><span data-stu-id="524ad-141">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="524ad-142">Données</span><span class="sxs-lookup"><span data-stu-id="524ad-142">Data</span></span>|<span data-ttu-id="524ad-143">Stockage</span><span class="sxs-lookup"><span data-stu-id="524ad-143">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="524ad-144">Informations d'identification de présentation, telles que nom d'utilisateur, certificats X.509, jetons Kerberos et références aux informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="524ad-144">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="524ad-145">Mécanismes de gestion des informations d'identification Windows standard tels que le magasin de certificats Windows.</span><span class="sxs-lookup"><span data-stu-id="524ad-145">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="524ad-146">Informations d'appartenance utilisateur, telles que noms d'utilisateur et mots de passe.</span><span class="sxs-lookup"><span data-stu-id="524ad-146">User membership information, such as usernames and passwords.</span></span>|<span data-ttu-id="524ad-147">Fournisseurs d’appartenances ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="524ad-147">ASP.NET membership providers.</span></span>|  
|<span data-ttu-id="524ad-148">Informations d'identité à propos du service utilisé pour authentifier le service aux clients.</span><span class="sxs-lookup"><span data-stu-id="524ad-148">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="524ad-149">Adresse de point de terminaison du service.</span><span class="sxs-lookup"><span data-stu-id="524ad-149">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="524ad-150">Informations sur l'appelant.</span><span class="sxs-lookup"><span data-stu-id="524ad-150">Caller information.</span></span>|<span data-ttu-id="524ad-151">Journaux d'audit.</span><span class="sxs-lookup"><span data-stu-id="524ad-151">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="524ad-152">Audit</span><span class="sxs-lookup"><span data-stu-id="524ad-152">Auditing</span></span>  
 <span data-ttu-id="524ad-153">L'audit permet d'enregistrer le succès et l'échec des événements d'authentification et d'autorisation.</span><span class="sxs-lookup"><span data-stu-id="524ad-153">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="524ad-154">Les enregistrements d'audit contiennent les données suivantes : URI de service, URI d'action et identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="524ad-154">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="524ad-155">L'audit note également lorsque l'administrateur modifie la configuration d'enregistrement des messages (activation ou désactivation), car l'enregistrement des messages peut enregistrer des données spécifiques à l'application dans les en-têtes et les corps.</span><span class="sxs-lookup"><span data-stu-id="524ad-155">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="524ad-156">Pour Windows XP, un enregistrement est enregistré dans le journal des événements de l’application.</span><span class="sxs-lookup"><span data-stu-id="524ad-156">For Windows XP, a record is logged in the application event log.</span></span> <span data-ttu-id="524ad-157">Pour Windows Vista et Windows Server 2003, un enregistrement est enregistré dans le journal des événements de sécurité.</span><span class="sxs-lookup"><span data-stu-id="524ad-157">For Windows Vista and Windows Server 2003, a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="524ad-158">Transactions</span><span class="sxs-lookup"><span data-stu-id="524ad-158">Transactions</span></span>  
 <span data-ttu-id="524ad-159">La fonctionnalité transactions fournit des services transactionnels à une application WCF.</span><span class="sxs-lookup"><span data-stu-id="524ad-159">The transactions feature provides transactional services to a WCF application.</span></span>  
  
 <span data-ttu-id="524ad-160">Les en-têtes de transaction utilisés dans la propagation de transaction peuvent contenir des ID de transaction ou des ID d'inscription, qui sont des GUID.</span><span class="sxs-lookup"><span data-stu-id="524ad-160">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="524ad-161">La fonctionnalité Transactions utilise le gestionnaire de transactions Microsoft Distributed Transaction Coordinator (MSDTC) (un composant Windows) pour gérer l’état des transactions.</span><span class="sxs-lookup"><span data-stu-id="524ad-161">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="524ad-162">Par défaut, les communications entre les gestionnaires de transactions sont chiffrées.</span><span class="sxs-lookup"><span data-stu-id="524ad-162">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="524ad-163">Les gestionnaires de transactions peuvent enregistrer des références à des points de terminaison, des ID de transaction et des ID d'inscription dans le cadre de leur état durable.</span><span class="sxs-lookup"><span data-stu-id="524ad-163">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="524ad-164">La durée de vie de cet état est déterminée par la durée de vie du fichier journal du gestionnaire de transactions.</span><span class="sxs-lookup"><span data-stu-id="524ad-164">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="524ad-165">Le service MSDTC détient la propriété et assure la maintenance de ce journal.</span><span class="sxs-lookup"><span data-stu-id="524ad-165">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="524ad-166">La fonctionnalité Transactions implémente les normes WS-Coordination et WS-Atomic Transaction.</span><span class="sxs-lookup"><span data-stu-id="524ad-166">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="524ad-167">Sessions fiables</span><span class="sxs-lookup"><span data-stu-id="524ad-167">Reliable Sessions</span></span>  
 <span data-ttu-id="524ad-168">Les sessions fiables dans WCF permettent de transférer des messages en cas de défaillances de transport ou d’intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="524ad-168">Reliable sessions in WCF provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="524ad-169">Elles fournissent un transfert de message « exactly-once » même lorsque le transport sous-jacent se déconnecte (par exemple, une connexion TCP sur un réseau sans fil) ou perd un message (un proxy HTTP qui rejette un message sortant ou entrant).</span><span class="sxs-lookup"><span data-stu-id="524ad-169">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="524ad-170">Les sessions fiables récupèrent également la réorganisation des messages (comme il peut arriver dans le cas du routage multivoie), en conservant l'ordre dans lequel les messages ont été envoyés.</span><span class="sxs-lookup"><span data-stu-id="524ad-170">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="524ad-171">Les sessions fiables sont implémentées à l'aide du protocole WS-RM (WS-ReliableMessaging).</span><span class="sxs-lookup"><span data-stu-id="524ad-171">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="524ad-172">Elles ajoutent des en-têtes WS-RM qui contiennent des informations de session, utilisées pour identifier tous les messages associés à une session fiable particulière.</span><span class="sxs-lookup"><span data-stu-id="524ad-172">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="524ad-173">Chaque session WS-RM a un identificateur, qui est un GUID.</span><span class="sxs-lookup"><span data-stu-id="524ad-173">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="524ad-174">Aucune information personnelle n’est conservée sur l’ordinateur de l’utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="524ad-174">No personal information is retained on the end user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="524ad-175">Canaux mis en file d'attente</span><span class="sxs-lookup"><span data-stu-id="524ad-175">Queued Channels</span></span>  
 <span data-ttu-id="524ad-176">Les files d'attente stockent des messages d'une application émettrice pour le compte d'une application réceptrice et envoient ultérieurement ces messages à l'application réceptrice.</span><span class="sxs-lookup"><span data-stu-id="524ad-176">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="524ad-177">Elles aident à garantir le transfert des messages des applications émettrices aux applications réceptrices lorsque, par exemple, l'application réceptrice est transitoire.</span><span class="sxs-lookup"><span data-stu-id="524ad-177">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> <span data-ttu-id="524ad-178">WCF prend en charge la mise en file d’attente à l’aide de Microsoft Message Queuing (MSMQ) en tant que transport.</span><span class="sxs-lookup"><span data-stu-id="524ad-178">WCF provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="524ad-179">La fonctionnalité de canaux en file d'attente n'ajoute pas d'en-tête à un message.</span><span class="sxs-lookup"><span data-stu-id="524ad-179">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="524ad-180">Au lieu de cela, elle crée un message Message Queuing avec les propriétés de message Message Queuing appropriées définies et elle appelle des méthodes Message Queuing pour mettre le message dans la file d'attente Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="524ad-180">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="524ad-181">Message Queuing est un composant facultatif fourni avec Windows.</span><span class="sxs-lookup"><span data-stu-id="524ad-181">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="524ad-182">Aucune information n’est conservée sur l’ordinateur de l’utilisateur final par la fonctionnalité de canaux en file d’attente, car elle utilise Message Queuing comme infrastructure de mise en file d’attente.</span><span class="sxs-lookup"><span data-stu-id="524ad-182">No information is retained on the end user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="524ad-183">Intégration COM+</span><span class="sxs-lookup"><span data-stu-id="524ad-183">COM+ Integration</span></span>  
 <span data-ttu-id="524ad-184">Cette fonctionnalité encapsule les fonctionnalités COM et COM+ existantes pour créer des services compatibles avec les services WCF.</span><span class="sxs-lookup"><span data-stu-id="524ad-184">This feature wraps existing COM and COM+ functionality to create services that are compatible with WCF services.</span></span> <span data-ttu-id="524ad-185">Cette fonctionnalité n’utilise pas d’en-têtes spécifiques et ne conserve pas les données sur l’ordinateur de l’utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="524ad-185">This feature does not use specific headers and it does not retain data on the end user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="524ad-186">Moniker de service COM</span><span class="sxs-lookup"><span data-stu-id="524ad-186">COM Service Moniker</span></span>  
 <span data-ttu-id="524ad-187">Cela fournit un wrapper non managé à un client WCF standard.</span><span class="sxs-lookup"><span data-stu-id="524ad-187">This provides an unmanaged wrapper to a standard WCF client.</span></span> <span data-ttu-id="524ad-188">Cette fonctionnalité n’a pas d’en-têtes spécifiques sur le câble et ne conserve pas de données sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="524ad-188">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="524ad-189">Canal homologue</span><span class="sxs-lookup"><span data-stu-id="524ad-189">Peer Channel</span></span>  
 <span data-ttu-id="524ad-190">Un canal homologue permet le développement d’applications à parties égales à l’aide de WCF.</span><span class="sxs-lookup"><span data-stu-id="524ad-190">A peer channel enables development of multiparty applications using WCF.</span></span> <span data-ttu-id="524ad-191">La messagerie pluripartite se produit dans le contexte d'une maille.</span><span class="sxs-lookup"><span data-stu-id="524ad-191">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="524ad-192">Les mailles sont identifiées par un nom que les nœuds peuvent joindre.</span><span class="sxs-lookup"><span data-stu-id="524ad-192">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="524ad-193">Chaque nœud du canal homologue crée un écouteur TCP à un port spécifié par l'utilisateur et établit des connexions avec d'autres nœuds dans la maille afin de garantir la résilience.</span><span class="sxs-lookup"><span data-stu-id="524ad-193">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="524ad-194">Pour se connecter à d'autres nœuds de la maille, les nœuds échangent également certaines données, y compris l'adresse d'écouteur et les adresses IP de l'ordinateur, avec d'autres nœuds de la maille.</span><span class="sxs-lookup"><span data-stu-id="524ad-194">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="524ad-195">Les messages envoyés dans la maille peuvent contenir des informations de sécurité relatives à l'expéditeur afin d'empêcher l'usurpation et la falsification de message.</span><span class="sxs-lookup"><span data-stu-id="524ad-195">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="524ad-196">Aucune information personnelle n’est stockée sur l’ordinateur de l’utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="524ad-196">No personal information is stored on the end user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="524ad-197">Expérience professionnelle en informatique</span><span class="sxs-lookup"><span data-stu-id="524ad-197">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="524ad-198">Traçage</span><span class="sxs-lookup"><span data-stu-id="524ad-198">Tracing</span></span>  
 <span data-ttu-id="524ad-199">La fonctionnalité de diagnostic de l’infrastructure WCF journalise les messages qui passent par les couches de modèle de transport et de service, ainsi que les activités et événements associés à ces messages.</span><span class="sxs-lookup"><span data-stu-id="524ad-199">The diagnostics feature of the WCF infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="524ad-200">Cette fonctionnalité est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="524ad-200">This feature is turned off by default.</span></span> <span data-ttu-id="524ad-201">Il est activé à l’aide du fichier de configuration de l’application et le comportement de suivi peut être modifié à l’aide du fournisseur WMI WCF au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="524ad-201">It is enabled using the application’s configuration file and the tracing behavior may be modified using the WCF WMI provider at run time.</span></span> <span data-ttu-id="524ad-202">Lorsque cette fonctionnalité est activée, l'infrastructure de suivi émet un suivi de diagnostic qui contient des messages, des activités et des événements de traitement aux écouteurs configurés.</span><span class="sxs-lookup"><span data-stu-id="524ad-202">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="524ad-203">Le format et l'emplacement de la sortie sont déterminés par les choix de configuration d'écouteur de l'administrateur, mais il s'agit en général d'un fichier au format XML.</span><span class="sxs-lookup"><span data-stu-id="524ad-203">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="524ad-204">L'administrateur est chargé de définir la liste de contrôle d'accès (ACL) sur les fichiers de suivi.</span><span class="sxs-lookup"><span data-stu-id="524ad-204">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="524ad-205">En particulier, en cas d'hébergement par le système WAS (Windows Activation System), l'administrateur doit s'assurer que les fichiers ne sont pas servis depuis le répertoire racine virtuel public si cela n'est pas souhaité.</span><span class="sxs-lookup"><span data-stu-id="524ad-205">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="524ad-206">Il existe deux types de suivi : l'enregistrement des messages et le suivi du diagnostic de modèle de service, décrits dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="524ad-206">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="524ad-207">Chaque type est configuré par le biais de sa propre source de suivi : <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> et <xref:System.ServiceModel>.</span><span class="sxs-lookup"><span data-stu-id="524ad-207">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="524ad-208">Ces deux sources de suivi d'enregistrement capturent des données qui sont locales à l'application.</span><span class="sxs-lookup"><span data-stu-id="524ad-208">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="524ad-209">Journalisation des messages</span><span class="sxs-lookup"><span data-stu-id="524ad-209">Message Logging</span></span>  
 <span data-ttu-id="524ad-210">La source de suivi d'enregistrement des messages (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) permet à un administrateur d'enregistrer les messages qui sont transmis sur le système.</span><span class="sxs-lookup"><span data-stu-id="524ad-210">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="524ad-211">Par le biais de la configuration, l'utilisateur peut décider d'enregistrer uniquement des messages entiers ou des en-têtes de message, s'il faut enregistrer les couches de modèle de transport et/ou de service et s'il faut inclure les messages malformés.</span><span class="sxs-lookup"><span data-stu-id="524ad-211">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="524ad-212">En outre, l'utilisateur peut configurer le filtrage de façon à limiter les messages enregistrés.</span><span class="sxs-lookup"><span data-stu-id="524ad-212">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="524ad-213">Par défaut, l'enregistrement des messages est désactivé.</span><span class="sxs-lookup"><span data-stu-id="524ad-213">By default, message logging is disabled.</span></span> <span data-ttu-id="524ad-214">L'administrateur de l'ordinateur local peut empêcher l'administrateur au niveau de l'application d'activer l'enregistrement des messages.</span><span class="sxs-lookup"><span data-stu-id="524ad-214">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="524ad-215">Enregistrement des messages chiffrés et déchiffrés</span><span class="sxs-lookup"><span data-stu-id="524ad-215">Encrypted and Decrypted Message Logging</span></span>  
 <span data-ttu-id="524ad-216">Les messages sont enregistrés, chiffrés ou déchiffrés, comme décrit dans les termes suivants.</span><span class="sxs-lookup"><span data-stu-id="524ad-216">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="524ad-217">Enregistrement de transport</span><span class="sxs-lookup"><span data-stu-id="524ad-217">Transport Logging</span></span>  
 <span data-ttu-id="524ad-218">Enregistre les messages reçus et envoyés au niveau du transport.</span><span class="sxs-lookup"><span data-stu-id="524ad-218">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="524ad-219">Ces messages contiennent tous les en-têtes et peuvent être chiffrés avant d'être envoyés sur le câble et lors de la réception.</span><span class="sxs-lookup"><span data-stu-id="524ad-219">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="524ad-220">Si les messages sont chiffrés avant d'être envoyés sur le câble et lors de leur réception, ils sont enregistrés chiffrés également.</span><span class="sxs-lookup"><span data-stu-id="524ad-220">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="524ad-221">Une exception est lorsqu'un protocole de sécurité est utilisé (https) : ils sont alors enregistrés déchiffrés avant d'être envoyés et après avoir été reçus même s'ils sont chiffrés sur le câble.</span><span class="sxs-lookup"><span data-stu-id="524ad-221">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="524ad-222">Enregistrement de service</span><span class="sxs-lookup"><span data-stu-id="524ad-222">Service Logging</span></span>  
 <span data-ttu-id="524ad-223">Enregistre les messages reçus ou envoyés au niveau du modèle de service, après que le traitement d'en-tête de canal a eu lieu, juste avant et après l'entrée du code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="524ad-223">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="524ad-224">Les messages enregistrés à ce niveau sont déchiffrés même s'ils ont été sécurisés et chiffrés sur le câble.</span><span class="sxs-lookup"><span data-stu-id="524ad-224">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="524ad-225">Enregistrement des messages malformés</span><span class="sxs-lookup"><span data-stu-id="524ad-225">Malformed Message Logging</span></span>  
 <span data-ttu-id="524ad-226">Journalise les messages que l’infrastructure WCF ne peut pas comprendre ni traiter.</span><span class="sxs-lookup"><span data-stu-id="524ad-226">Logs messages that the WCF infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="524ad-227">Les messages sont enregistrés tels quels, autrement dit chiffrés ou non</span><span class="sxs-lookup"><span data-stu-id="524ad-227">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="524ad-228">Lorsque les messages sont consignés sous une forme déchiffrée ou non chiffrée, WCF supprime par défaut les clés de sécurité et les informations potentiellement personnelles des messages avant de les enregistrer.</span><span class="sxs-lookup"><span data-stu-id="524ad-228">When messages are logged in decrypted or unencrypted form, by default WCF removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="524ad-229">Les sections suivantes décrivent quelles informations sont supprimées, et quand.</span><span class="sxs-lookup"><span data-stu-id="524ad-229">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="524ad-230">L'administrateur de l'ordinateur et le responsable du déploiement d'applications doivent prendre certaines mesures de configuration pour modifier le comportement par défaut afin d'enregistrer les clés et les informations potentiellement personnelles.</span><span class="sxs-lookup"><span data-stu-id="524ad-230">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="524ad-231">Informations supprimées des en-têtes de messages lors de l'enregistrement des messages déchiffrés/non chiffrés</span><span class="sxs-lookup"><span data-stu-id="524ad-231">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="524ad-232">Lorsque les messages sont enregistrés sous forme déchiffrés/non chiffrés, les clés de sécurité et les informations potentiellement personnelles sont supprimées par défaut des en-têtes de messages et des corps de message avant d'être enregistrées.</span><span class="sxs-lookup"><span data-stu-id="524ad-232">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="524ad-233">La liste suivante indique ce que WCF considère comme des clés et des informations potentiellement personnelles.</span><span class="sxs-lookup"><span data-stu-id="524ad-233">The following list shows what WCF considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="524ad-234">Clés qui sont supprimées :</span><span class="sxs-lookup"><span data-stu-id="524ad-234">Keys that are removed:</span></span>  
  
 <span data-ttu-id="524ad-235">\- pour xmlns : WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" et xmlns : WST = "http://schemas.xmlsoap.org/ws/2005/02/trust"</span><span class="sxs-lookup"><span data-stu-id="524ad-235">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="524ad-236">wst:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="524ad-236">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="524ad-237">wst:Entropy</span><span class="sxs-lookup"><span data-stu-id="524ad-237">wst:Entropy</span></span>  
  
 <span data-ttu-id="524ad-238">\- pour xmlns : wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" et xmlns : wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="524ad-238">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="524ad-239">wsse:Password</span><span class="sxs-lookup"><span data-stu-id="524ad-239">wsse:Password</span></span>  
  
 <span data-ttu-id="524ad-240">wsse:Nonce</span><span class="sxs-lookup"><span data-stu-id="524ad-240">wsse:Nonce</span></span>  
  
 <span data-ttu-id="524ad-241">Informations potentiellement personnelles qui sont supprimées :</span><span class="sxs-lookup"><span data-stu-id="524ad-241">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="524ad-242">\- pour xmlns : wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" et xmlns : wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="524ad-242">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="524ad-243">wsse:Username</span><span class="sxs-lookup"><span data-stu-id="524ad-243">wsse:Username</span></span>  
  
 <span data-ttu-id="524ad-244">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="524ad-244">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="524ad-245">\- pour xmlns : SAML = "urn : Oasis : Names : TC : SAML : 1.0 : assertion" les éléments en gras (ci-dessous) sont supprimés :</span><span class="sxs-lookup"><span data-stu-id="524ad-245">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="524ad-246">Assertion de \<</span><span class="sxs-lookup"><span data-stu-id="524ad-246">\<Assertion</span></span>  
  
 <span data-ttu-id="524ad-247">MajorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="524ad-247">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="524ad-248">MinorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="524ad-248">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="524ad-249">AssertionId="[ID]"</span><span class="sxs-lookup"><span data-stu-id="524ad-249">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="524ad-250">Issuer="[chaîne]"</span><span class="sxs-lookup"><span data-stu-id="524ad-250">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="524ad-251">IssueInstant="[horodatage]"</span><span class="sxs-lookup"><span data-stu-id="524ad-251">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="524ad-252">\<conditions NotBefore = "[dateTime]" NotOnOrAfter = "[dateTime]" ></span><span class="sxs-lookup"><span data-stu-id="524ad-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span></span>  
  
 <span data-ttu-id="524ad-253">\<AudienceRestrictionCondition ></span><span class="sxs-lookup"><span data-stu-id="524ad-253">\<AudienceRestrictionCondition></span></span>  
  
 <span data-ttu-id="524ad-254">\<audience > [URI]\</audience > +</span><span class="sxs-lookup"><span data-stu-id="524ad-254">\<Audience>[uri]\</Audience>+</span></span>  
  
 <span data-ttu-id="524ad-255">\</AudienceRestrictionCondition > \*</span><span class="sxs-lookup"><span data-stu-id="524ad-255">\</AudienceRestrictionCondition>\*</span></span>  
  
 <span data-ttu-id="524ad-256">\<DoNotCacheCondition/> \*</span><span class="sxs-lookup"><span data-stu-id="524ad-256">\<DoNotCacheCondition />\*</span></span>  
  
 <span data-ttu-id="524ad-257"><\!--type de base abstrait</span><span class="sxs-lookup"><span data-stu-id="524ad-257"><\!-- abstract base type</span></span>  
  
 <span data-ttu-id="524ad-258">\<condition/> \*</span><span class="sxs-lookup"><span data-stu-id="524ad-258">\<Condition />\*</span></span>  
  
 -->  
  
 <span data-ttu-id="524ad-259">\<>/conditions ?</span><span class="sxs-lookup"><span data-stu-id="524ad-259">\</Conditions>?</span></span>  
  
 <span data-ttu-id="524ad-260">> de Conseil \<</span><span class="sxs-lookup"><span data-stu-id="524ad-260">\<Advice></span></span>  
  
 <span data-ttu-id="524ad-261">\<AssertionIDReference > [ID]\</AssertionIDReference > \*</span><span class="sxs-lookup"><span data-stu-id="524ad-261">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="524ad-262">\<assertion > [assertion]\</assertion > \*</span><span class="sxs-lookup"><span data-stu-id="524ad-262">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="524ad-263">[indifférent]\*</span><span class="sxs-lookup"><span data-stu-id="524ad-263">[any]\*</span></span>  
  
 <span data-ttu-id="524ad-264">\<>/Advice ?</span><span class="sxs-lookup"><span data-stu-id="524ad-264">\</Advice>?</span></span>  
  
 <span data-ttu-id="524ad-265"><\!--types de base abstraits</span><span class="sxs-lookup"><span data-stu-id="524ad-265"><\!-- Abstract base types</span></span>  
  
 <span data-ttu-id="524ad-266">Instruction \</> \*</span><span class="sxs-lookup"><span data-stu-id="524ad-266">\<Statement />\*</span></span>  
  
 <span data-ttu-id="524ad-267">\<SubjectStatement ></span><span class="sxs-lookup"><span data-stu-id="524ad-267">\<SubjectStatement></span></span>  
  
 <span data-ttu-id="524ad-268">\<objet ></span><span class="sxs-lookup"><span data-stu-id="524ad-268">\<Subject></span></span>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 <span data-ttu-id="524ad-269">\<SubjectConfirmation ></span><span class="sxs-lookup"><span data-stu-id="524ad-269">\<SubjectConfirmation></span></span>  
  
 <span data-ttu-id="524ad-270">\<ConfirmationMethod > [anyURI]\</ConfirmationMethod > +</span><span class="sxs-lookup"><span data-stu-id="524ad-270">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="524ad-271">\<SubjectConfirmationData > [Any]\</SubjectConfirmationData >?</span><span class="sxs-lookup"><span data-stu-id="524ad-271">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="524ad-272">\<DS : KeyInfo >...\</DS : KeyInfo >?</span><span class="sxs-lookup"><span data-stu-id="524ad-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="524ad-273">\<>/SubjectConfirmation ?</span><span class="sxs-lookup"><span data-stu-id="524ad-273">\</SubjectConfirmation>?</span></span>  
  
 <span data-ttu-id="524ad-274">\</Subject ></span><span class="sxs-lookup"><span data-stu-id="524ad-274">\</Subject></span></span>  
  
 <span data-ttu-id="524ad-275">\</SubjectStatement > \*</span><span class="sxs-lookup"><span data-stu-id="524ad-275">\</SubjectStatement>\*</span></span>  
  
 -->  
  
 <span data-ttu-id="524ad-276">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="524ad-276">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="524ad-277">AuthenticationMethod="[uri]"</span><span class="sxs-lookup"><span data-stu-id="524ad-277">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="524ad-278">AuthenticationInstant="[horodatage]"</span><span class="sxs-lookup"><span data-stu-id="524ad-278">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="524ad-279">[Objet]</span><span class="sxs-lookup"><span data-stu-id="524ad-279">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="524ad-280">< AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="524ad-280"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="524ad-281">AuthorityKind="[NomQ]"</span><span class="sxs-lookup"><span data-stu-id="524ad-281">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="524ad-282">Location="[uri]"</span><span class="sxs-lookup"><span data-stu-id="524ad-282">Location="[uri]"</span></span>  
  
 <span data-ttu-id="524ad-283">Binding="[uri]"</span><span class="sxs-lookup"><span data-stu-id="524ad-283">Binding="[uri]"</span></span>  
  
 />*  
  
 <span data-ttu-id="524ad-284">\</AuthenticationStatement > \*</span><span class="sxs-lookup"><span data-stu-id="524ad-284">\</AuthenticationStatement>\*</span></span>  
  
 <span data-ttu-id="524ad-285">\<AttributeStatement ></span><span class="sxs-lookup"><span data-stu-id="524ad-285">\<AttributeStatement></span></span>  
  
 <span data-ttu-id="524ad-286">[Objet]</span><span class="sxs-lookup"><span data-stu-id="524ad-286">[Subject]</span></span>  
  
 <span data-ttu-id="524ad-287">Attribut \<</span><span class="sxs-lookup"><span data-stu-id="524ad-287">\<Attribute</span></span>  
  
 <span data-ttu-id="524ad-288">AttributeName="[chaîne]"</span><span class="sxs-lookup"><span data-stu-id="524ad-288">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="524ad-289">AttributeNamespace="[uri]"</span><span class="sxs-lookup"><span data-stu-id="524ad-289">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 <span data-ttu-id="524ad-290">\</attribute > +</span><span class="sxs-lookup"><span data-stu-id="524ad-290">\</Attribute>+</span></span>  
  
 <span data-ttu-id="524ad-291">\</AttributeStatement > \*</span><span class="sxs-lookup"><span data-stu-id="524ad-291">\</AttributeStatement>\*</span></span>  
  
 <span data-ttu-id="524ad-292">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="524ad-292">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="524ad-293">Resource="[uri]"</span><span class="sxs-lookup"><span data-stu-id="524ad-293">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="524ad-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span><span class="sxs-lookup"><span data-stu-id="524ad-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="524ad-295">[Objet]</span><span class="sxs-lookup"><span data-stu-id="524ad-295">[Subject]</span></span>  
  
 <span data-ttu-id="524ad-296">\<action Namespace = "[URI]" > [String]\</action > +</span><span class="sxs-lookup"><span data-stu-id="524ad-296">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 <span data-ttu-id="524ad-297">> de preuve \<</span><span class="sxs-lookup"><span data-stu-id="524ad-297">\<Evidence></span></span>  
  
 <span data-ttu-id="524ad-298">\<AssertionIDReference > [ID]\</AssertionIDReference > +</span><span class="sxs-lookup"><span data-stu-id="524ad-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="524ad-299">\<assertion > [assertion]\</assertion > +</span><span class="sxs-lookup"><span data-stu-id="524ad-299">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="524ad-300">\<>/Evidence ?</span><span class="sxs-lookup"><span data-stu-id="524ad-300">\</Evidence>?</span></span>  
  
 <span data-ttu-id="524ad-301">\</AuthorizationDecisionStatement > \*</span><span class="sxs-lookup"><span data-stu-id="524ad-301">\</AuthorizationDecisionStatement>\*</span></span>  
  
 <span data-ttu-id="524ad-302">\</assertion ></span><span class="sxs-lookup"><span data-stu-id="524ad-302">\</Assertion></span></span>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="524ad-303">Informations supprimées des corps de messages lors de l'enregistrement des messages déchiffrés/non chiffrés</span><span class="sxs-lookup"><span data-stu-id="524ad-303">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="524ad-304">Comme décrit précédemment, WCF supprime les clés et les informations potentiellement personnelles connues des en-têtes de message pour les messages déchiffrés/non chiffrés.</span><span class="sxs-lookup"><span data-stu-id="524ad-304">As previously described, WCF removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="524ad-305">En outre, WCF supprime les clés et les informations potentiellement personnelles connues des corps de message pour les éléments et actions du corps de la liste suivante, qui décrivent les messages de sécurité impliqués dans l’échange de clés.</span><span class="sxs-lookup"><span data-stu-id="524ad-305">In addition, WCF removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="524ad-306">Pour les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="524ad-306">For the following namespaces:</span></span>  
  
 <span data-ttu-id="524ad-307">xmlns : WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" et xmlns : WST = "http://schemas.xmlsoap.org/ws/2005/02/trust" (par exemple, si aucune action n’est disponible)</span><span class="sxs-lookup"><span data-stu-id="524ad-307">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="524ad-308">Les informations sont supprimées pour ces éléments de corps, qui impliquent l'échange de clé :</span><span class="sxs-lookup"><span data-stu-id="524ad-308">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="524ad-309">wst:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="524ad-309">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="524ad-310">wst:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="524ad-310">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="524ad-311">wst:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="524ad-311">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="524ad-312">Les informations sont également supprimées pour chacune des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="524ad-312">Information is also removed for each of the following Actions:</span></span>  
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend`
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="524ad-313">Aucune information n'est supprimé des données de corps et en-têtes spécifiques aux applications</span><span class="sxs-lookup"><span data-stu-id="524ad-313">No Information Is Removed from Application-specific Headers and Body Data</span></span>  
 <span data-ttu-id="524ad-314">WCF n’effectue pas le suivi des informations personnelles dans les en-têtes spécifiques à l’application (par exemple, les chaînes de requête) ou les données de corps (par exemple, le numéro de carte de crédit).</span><span class="sxs-lookup"><span data-stu-id="524ad-314">WCF does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="524ad-315">Lorsque l'enregistrement des messages est activé, les informations personnelles contenues dans des en-têtes spécifiques aux application et les informations de corps peuvent être visibles dans les journaux.</span><span class="sxs-lookup"><span data-stu-id="524ad-315">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="524ad-316">Là encore, le responsable du déploiement d'applications est chargé de définir les listes ACL sur les fichiers de configuration et les fichiers journaux.</span><span class="sxs-lookup"><span data-stu-id="524ad-316">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="524ad-317">Ils peuvent également désactiver la journalisation s’ils ne souhaitent pas que ces informations soient visibles, ou filtrer ces informations à partir des fichiers journaux après leur enregistrement.</span><span class="sxs-lookup"><span data-stu-id="524ad-317">They also can turn off logging if they don't want this information to be visible, or filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="524ad-318">Suivi du modèle de service</span><span class="sxs-lookup"><span data-stu-id="524ad-318">Service Model Tracing</span></span>  
 <span data-ttu-id="524ad-319">La source de suivi de modèle de service (<xref:System.ServiceModel>) autorise le suivi des activités et événements liés au traitement des messages.</span><span class="sxs-lookup"><span data-stu-id="524ad-319">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="524ad-320">Cette fonctionnalité utilise la fonctionnalité de diagnostic du .NET Framework de <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="524ad-320">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="524ad-321">Comme avec la propriété <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>, l'emplacement et sa liste ACL sont configurables par l'utilisateur à l'aide de fichiers de configuration d'application .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="524ad-321">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="524ad-322">Comme avec l'enregistrement des messages, l'emplacement des fichiers est toujours configuré lorsque l'administrateur active le suivi ; par conséquent, l'administrateur contrôle la liste ACL.</span><span class="sxs-lookup"><span data-stu-id="524ad-322">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="524ad-323">Les suivis contiennent des en-têtes de messages lorsqu'un message est dans la portée.</span><span class="sxs-lookup"><span data-stu-id="524ad-323">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="524ad-324">On applique les mêmes règles de masquage des informations potentiellement personnelles dans les en-têtes de messages que celles décrites dans la section précédente : les informations personnelles précédemment identifiées sont supprimées par défaut des en-têtes dans les suivis.</span><span class="sxs-lookup"><span data-stu-id="524ad-324">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="524ad-325">L'administrateur d'ordinateur et le responsable du déploiement d'applications doivent modifier la configuration afin d'enregistrer les informations potentiellement personnelles.</span><span class="sxs-lookup"><span data-stu-id="524ad-325">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="524ad-326">Toutefois, les informations personnelles contenues dans les en-têtes spécifiques aux applications sont enregistrées dans les suivis.</span><span class="sxs-lookup"><span data-stu-id="524ad-326">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="524ad-327">Le responsable du déploiement d'applications est chargé de définir les listes ACL sur les fichiers de configuration et les fichiers de suivi.</span><span class="sxs-lookup"><span data-stu-id="524ad-327">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="524ad-328">Ils peuvent également désactiver le suivi pour masquer ces informations ou filtrer ces informations à partir des fichiers de trace après leur enregistrement.</span><span class="sxs-lookup"><span data-stu-id="524ad-328">They can also turn off tracing to hide this information or filter out this information from the trace files after it's logged.</span></span>  
  
 <span data-ttu-id="524ad-329">Dans le cadre du suivi ServiceModel, des ID uniques (nommés ID d'activité, et correspondant en général à un GUID) relient différentes activités à mesure qu'un message parcoure différentes parties de l'infrastructure.</span><span class="sxs-lookup"><span data-stu-id="524ad-329">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="524ad-330">Écouteurs de suivi personnalisés</span><span class="sxs-lookup"><span data-stu-id="524ad-330">Custom Trace Listeners</span></span>  
 <span data-ttu-id="524ad-331">Pour l'enregistrement des messages et le suivi, un écouteur de suivi personnalisé peut être configuré de façon à envoyer des suivis et des messages sur le câble (par exemple à une base de données distante).</span><span class="sxs-lookup"><span data-stu-id="524ad-331">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="524ad-332">Le responsable du déploiement d'applications est chargé de configurer les écouteurs personnalisés ou de déléguer cette opération aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="524ad-332">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="524ad-333">Ils sont également responsables des informations personnelles exposées à l’emplacement distant et pour l’application correcte des listes de contrôle d’accès à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="524ad-333">They are also responsible for any personal information exposed at the remote location and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="524ad-334">Autres fonctionnalités pour les professionnels de l'informatique</span><span class="sxs-lookup"><span data-stu-id="524ad-334">Other features for IT Professionals</span></span>  
 <span data-ttu-id="524ad-335">WCF dispose d’un fournisseur WMI qui expose les informations de configuration de l’infrastructure WCF par le biais de WMI (fourni avec Windows).</span><span class="sxs-lookup"><span data-stu-id="524ad-335">WCF has a WMI provider that exposes the WCF infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="524ad-336">Par défaut, l'interface WMI est accessible aux administrateurs.</span><span class="sxs-lookup"><span data-stu-id="524ad-336">By default, the WMI interface is available to administrators.</span></span>  
  
 <span data-ttu-id="524ad-337">La configuration WCF utilise le mécanisme de configuration .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="524ad-337">WCF configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="524ad-338">Les fichiers de configuration sont stockés sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="524ad-338">The configuration files are stored on the machine.</span></span> <span data-ttu-id="524ad-339">Le développeur d’applications et l’administrateur créent les fichiers de configuration et la liste ACL pour chacune des exigences de l’application.</span><span class="sxs-lookup"><span data-stu-id="524ad-339">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="524ad-340">Un fichier de configuration peut contenir des adresses de point de terminaison et des liens vers des certificats dans le magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="524ad-340">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="524ad-341">Les certificats peuvent être utilisés pour fournir des données d’application afin de configurer différentes propriétés des fonctionnalités utilisées par l’application.</span><span class="sxs-lookup"><span data-stu-id="524ad-341">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="524ad-342">WCF utilise également la fonctionnalité de vidage de processus .NET Framework en appelant la méthode <xref:System.Environment.FailFast%2A>.</span><span class="sxs-lookup"><span data-stu-id="524ad-342">WCF also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="524ad-343">Outils pour professionnels de l'informatique</span><span class="sxs-lookup"><span data-stu-id="524ad-343">IT Pro Tools</span></span>  
 <span data-ttu-id="524ad-344">WCF fournit également les outils professionnels de l’informatique suivants, qui sont fournis dans le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="524ad-344">WCF also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="524ad-345">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="524ad-345">SvcTraceViewer.exe</span></span>  
 <span data-ttu-id="524ad-346">La visionneuse affiche les fichiers de trace WCF.</span><span class="sxs-lookup"><span data-stu-id="524ad-346">The viewer displays WCF trace files.</span></span> <span data-ttu-id="524ad-347">La visionneuse affiche toutes les informations contenues dans les suivis.</span><span class="sxs-lookup"><span data-stu-id="524ad-347">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="524ad-348">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="524ad-348">SvcConfigEditor.exe</span></span>  
 <span data-ttu-id="524ad-349">L’éditeur permet à l’utilisateur de créer et de modifier des fichiers de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="524ad-349">The editor allows the user to create and edit WCF configuration files.</span></span> <span data-ttu-id="524ad-350">L'éditeur affiche toutes les informations contenues dans les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="524ad-350">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="524ad-351">La même tâche peut être accomplie avec un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="524ad-351">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodel_reg"></a><span data-ttu-id="524ad-352">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="524ad-352">ServiceModel_Reg</span></span>  
 <span data-ttu-id="524ad-353">Cet outil permet à l'utilisateur de gérer les installations de ServiceModel sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="524ad-353">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="524ad-354">L’outil affiche les messages d’État dans une fenêtre de console lorsqu’il s’exécute et, dans le processus, peut afficher des informations sur la configuration de l’installation WCF.</span><span class="sxs-lookup"><span data-stu-id="524ad-354">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the WCF installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="524ad-355">WSATConfig.exe et WSATUI.dll</span><span class="sxs-lookup"><span data-stu-id="524ad-355">WSATConfig.exe and WSATUI.dll</span></span>  
 <span data-ttu-id="524ad-356">Ces outils permettent aux professionnels de l’informatique de configurer la prise en charge du réseau WS-AtomicTransaction interopérable dans WCF.</span><span class="sxs-lookup"><span data-stu-id="524ad-356">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in WCF.</span></span> <span data-ttu-id="524ad-357">Les outils affichent et permettent aux utilisateurs de modifier les valeurs des paramètres WS-AtomicTransaction le plus couramment utilisés stockés dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="524ad-357">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="524ad-358">Fonctionnalités composites</span><span class="sxs-lookup"><span data-stu-id="524ad-358">Cross-cutting Features</span></span>  
 <span data-ttu-id="524ad-359">Les fonctionnalités suivantes sont composites.</span><span class="sxs-lookup"><span data-stu-id="524ad-359">The following features are cross-cutting.</span></span> <span data-ttu-id="524ad-360">En d’autres termes, elles peuvent être composées de n’importe lesquelles des fonctionnalités précédentes.</span><span class="sxs-lookup"><span data-stu-id="524ad-360">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="524ad-361">Infrastructure de service</span><span class="sxs-lookup"><span data-stu-id="524ad-361">Service Framework</span></span>  
 <span data-ttu-id="524ad-362">Les en-têtes peuvent contenir un ID d'instance, qui est un GUID qui associe un message à une instance d'une classe CLR.</span><span class="sxs-lookup"><span data-stu-id="524ad-362">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="524ad-363">Le langage WDSL (Web Services Description Language) contient une définition du port.</span><span class="sxs-lookup"><span data-stu-id="524ad-363">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="524ad-364">Chaque port a une adresse de point de terminaison et une liaison qui représente les services utilisés par l'application.</span><span class="sxs-lookup"><span data-stu-id="524ad-364">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="524ad-365">L'exposition du langage WSDL peut être désactivée à l'aide de la configuration.</span><span class="sxs-lookup"><span data-stu-id="524ad-365">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="524ad-366">Aucune information n'est conservée sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="524ad-366">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="524ad-367">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="524ad-367">See also</span></span>

- [<span data-ttu-id="524ad-368">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="524ad-368">Windows Communication Foundation</span></span>](index.md)
- [<span data-ttu-id="524ad-369">Sécurité</span><span class="sxs-lookup"><span data-stu-id="524ad-369">Security</span></span>](./feature-details/security.md)
