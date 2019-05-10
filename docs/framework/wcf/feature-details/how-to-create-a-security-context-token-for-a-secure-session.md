---
title: 'Procédure : créer un jeton de contexte de sécurité pour une session sécurisée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: e425db792a2aec562eb0c4f90463eb861eb80f63
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650266"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="4bdfa-102">Procédure : créer un jeton de contexte de sécurité pour une session sécurisée</span><span class="sxs-lookup"><span data-stu-id="4bdfa-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="4bdfa-103">En utilisant un jeton de contexte de sécurité avec état (SCT) dans une session sécurisée, la session peut résister au service qui est recyclé.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="4bdfa-104">Par exemple, lorsqu'un SCT sans état est utilisé dans une session sécurisée et que les services IIS (Internet Information Services) sont réinitialisés, les données de session associées au service sont perdues.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="4bdfa-105">Ces données de session incluent un cache du jeton SCT.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="4bdfa-106">Ainsi, la prochaine fois qu'un client enverra au service un SCT sans état, une erreur sera retournée, parce que la clé associée au SCT ne peut pas être récupérée.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="4bdfa-107">Toutefois, si un SCT avec état est utilisé, la clé associée au SCT est contenue dans le SCT.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="4bdfa-108">Étant donné que la clé est contenue dans le SCT et donc contenue dans le message, la session sécurisée n'est pas affectée par le service qui est recyclé.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="4bdfa-109">Par défaut, Windows Communication Foundation (WCF) utilise des SCT sans état dans une session sécurisée.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="4bdfa-110">Cette rubrique détaille la manière d’utiliser des SCT avec état dans une session sécurisée.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bdfa-111">Les SCT avec état ne peuvent pas être utilisés dans une session sécurisée qui implique un contrat dérivé de <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bdfa-112">Pour les applications qui utilisent des SCT avec état dans une session sécurisée, l’identité de thread pour le service doit être un compte d’utilisateur ayant un profil utilisateur associé.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="4bdfa-113">Lorsque le service est exécuté sous un compte qui n'a pas de profil utilisateur, tel qu'un `Local Service`, une exception peut être levée.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bdfa-114">Lorsque l’emprunt d’identité est requis sur Windows XP, utilisez une session sécurisée sans SCT avec état.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="4bdfa-115">Lorsque des SCT avec état sont utilisés avec l’emprunt d’identité, une <xref:System.InvalidOperationException> est levée.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="4bdfa-116">Pour plus d’informations, consultez [scénarios non pris en charge](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="4bdfa-116">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="4bdfa-117">Pour utiliser des SCT avec état dans une session sécurisée</span><span class="sxs-lookup"><span data-stu-id="4bdfa-117">To use stateful SCTs in a secure session</span></span>  
  
- <span data-ttu-id="4bdfa-118">Créez une liaison personnalisée qui spécifie que les messages SOAP sont protégés par une session sécurisée qui utilise un SCT avec état.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1. <span data-ttu-id="4bdfa-119">Définissez une liaison personnalisée, en ajoutant un [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) au fichier de configuration pour le service.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-119">Define a custom binding, by adding a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        ```  
  
    2. <span data-ttu-id="4bdfa-120">Ajouter un [ \<liaison >](../../../../docs/framework/misc/binding.md) élément enfant à la [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="4bdfa-120">Add a [\<binding>](../../../../docs/framework/misc/binding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="4bdfa-121">Spécifiez un nom de liaison en affectant à l'attribut `name` un nom unique dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3. <span data-ttu-id="4bdfa-122">Spécifiez le mode d’authentification pour les messages envoyés vers et à partir de ce service en ajoutant un [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) élément enfant à la [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="4bdfa-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="4bdfa-123">Spécifiez qu'une session sécurisée est utilisée en affectant à l'attribut `authenticationMode` la valeur `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="4bdfa-124">Spécifiez que des SCT avec état sont utilisés en affectant à l'attribut `requireSecurityContextCancellation` la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4. <span data-ttu-id="4bdfa-125">Spécifiez comment le client est authentifié pendant que la session sécurisée est établie en ajoutant un [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément enfant à la [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="4bdfa-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="4bdfa-126">Spécifiez comment le client est authentifié en définissant l'attribut `authenticationMode`.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. <span data-ttu-id="4bdfa-127">Spécifier l’encodage de message en ajoutant un élément d’encodage, tel que [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="4bdfa-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. <span data-ttu-id="4bdfa-128">Spécifier le transport en ajoutant un élément de transport, tel que le [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="4bdfa-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="4bdfa-129">L’exemple de code suivant utilise la configuration pour spécifier une liaison personnalisée que les messages peuvent utiliser avec des SCT avec état dans une session sécurisée.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="StatefulSCTSecureSession">  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
          <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        </security>  
        <textMessageEncoding />  
        <httpTransport />  
      </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="4bdfa-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="4bdfa-130">Example</span></span>  
 <span data-ttu-id="4bdfa-131">L’exemple de code suivant crée une liaison personnalisée qui utilise le mode d’authentification <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> pour démarrer une session sécurisée.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="4bdfa-132">Lorsque l’authentification Windows est utilisée en association avec un SCT avec état, WCF ne remplit pas la <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> propriété avec l’appelant réel de l’identité, mais au lieu de cela affecte à la propriété anonyme.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="4bdfa-133">Étant donné que la sécurité WCF doit recréer le contenu du contexte de sécurité du service pour chaque demande du SCT entrant, le serveur de ne pas un suivi de la session de sécurité dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="4bdfa-134">Comme il est impossible de sérialiser l'instance <xref:System.Security.Principal.WindowsIdentity> dans le SCT, la propriété <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> retourne une identité anonyme.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="4bdfa-135">La configuration suivante expose ce comportement.</span><span class="sxs-lookup"><span data-stu-id="4bdfa-135">The following configuration exhibits this behavior.</span></span>  
  
```xml  
<customBinding>  
  <binding name="Cancellation">  
       <textMessageEncoding />  
        <security   
            requireSecurityContextCancellation="false">  
              <secureConversationBootstrap />  
      </security>  
    <httpTransport />  
  </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4bdfa-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bdfa-136">See also</span></span>

- [<span data-ttu-id="4bdfa-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4bdfa-137">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
