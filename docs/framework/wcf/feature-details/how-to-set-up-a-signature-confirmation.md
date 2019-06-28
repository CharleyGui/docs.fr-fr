---
title: 'Procédure : configurer une confirmation de signature'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 6f44ae5e3615df7f529a25f4097ef042feba544d
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425434"
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="7eea3-102">Procédure : configurer une confirmation de signature</span><span class="sxs-lookup"><span data-stu-id="7eea3-102">How to: Set Up a Signature Confirmation</span></span>

<span data-ttu-id="7eea3-103">*Confirmation de signature* est un mécanisme pour un initiateur de message pour vous assurer qu’une réponse reçue a été générée en réponse au message d’origine de l’expéditeur.</span><span class="sxs-lookup"><span data-stu-id="7eea3-103">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="7eea3-104">La confirmation de signature est définie dans la spécification WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="7eea3-104">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="7eea3-105">Si un point de terminaison prend en charge WS-Security 1.0, vous ne pouvez pas utiliser la confirmation de signature.</span><span class="sxs-lookup"><span data-stu-id="7eea3-105">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>

<span data-ttu-id="7eea3-106">Les procédures suivantes spécifient comment activer la confirmation de signature à l'aide de <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="7eea3-106">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="7eea3-107">Vous pouvez utiliser la même procédure avec <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="7eea3-107">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="7eea3-108">La procédure repose sur les étapes de base indiquées dans [Comment : Créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="7eea3-108">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="7eea3-109">Pour activer la confirmation de signature dans le code</span><span class="sxs-lookup"><span data-stu-id="7eea3-109">To enable signature confirmation in code</span></span>

1. <span data-ttu-id="7eea3-110">Créez une instance de la classe <xref:System.ServiceModel.Channels.BindingElementCollection>.</span><span class="sxs-lookup"><span data-stu-id="7eea3-110">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>

2. <span data-ttu-id="7eea3-111">Créez une instance de la <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> classe.</span><span class="sxs-lookup"><span data-stu-id="7eea3-111">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>

3. <span data-ttu-id="7eea3-112">Affectez <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> à `true`.</span><span class="sxs-lookup"><span data-stu-id="7eea3-112">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>

4. <span data-ttu-id="7eea3-113">Ajoutez l’élément de sécurité à la collection de liaisons.</span><span class="sxs-lookup"><span data-stu-id="7eea3-113">Add the security element to the binding collection.</span></span>

5. <span data-ttu-id="7eea3-114">Créer une liaison personnalisée, tel que spécifié dans [Comment : Créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="7eea3-114">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="7eea3-115">Pour activer la confirmation de signature dans la configuration</span><span class="sxs-lookup"><span data-stu-id="7eea3-115">To enable signature confirmation in configuration</span></span>

1. <span data-ttu-id="7eea3-116">Ajoutez un élément `<customBinding>` à la section `<bindings>` du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="7eea3-116">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>

2. <span data-ttu-id="7eea3-117">Ajoutez un élément `<binding>` et affectez une valeur appropriée à l'attribut de nom.</span><span class="sxs-lookup"><span data-stu-id="7eea3-117">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>

3. <span data-ttu-id="7eea3-118">Ajoutez un élément d'encodage approprié.</span><span class="sxs-lookup"><span data-stu-id="7eea3-118">Add an appropriate encoding element.</span></span> <span data-ttu-id="7eea3-119">L'exemple suivant ajoute un élément `<TextMessageEncoding>`.</span><span class="sxs-lookup"><span data-stu-id="7eea3-119">The following example adds a `<TextMessageEncoding>` element.</span></span>

4. <span data-ttu-id="7eea3-120">Ajoutez un élément enfant `<security>` et affectez `requireSignatureConfirmation` à l'attribut `true`.</span><span class="sxs-lookup"><span data-stu-id="7eea3-120">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>

5. <span data-ttu-id="7eea3-121">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7eea3-121">Optional.</span></span> <span data-ttu-id="7eea3-122">Pour activer la confirmation de signature pendant le démarrage, ajoutez un [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément enfant et définissez le `requireSignatureConfirmation` attribut `true`.</span><span class="sxs-lookup"><span data-stu-id="7eea3-122">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>

6. <span data-ttu-id="7eea3-123">Ajoutez un élément de transport approprié.</span><span class="sxs-lookup"><span data-stu-id="7eea3-123">Add an appropriate transport element.</span></span> <span data-ttu-id="7eea3-124">L’exemple suivant ajoute un [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span><span class="sxs-lookup"><span data-stu-id="7eea3-124">The following example adds an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span></span>

    ```xml
    <bindings>
      <customBinding>
        <binding name="SignatureConfirmationBinding">
          <security requireSignatureConfirmation="true">
            <secureConversationBootstrap requireSignatureConfirmation="true" />
              </security>
           <textMessageEncoding />
             <httpTransport />
        </binding>
      </customBinding>
    </bindings>
    ```

## <a name="example"></a><span data-ttu-id="7eea3-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="7eea3-125">Example</span></span>

<span data-ttu-id="7eea3-126">Le code suivant crée une instance de <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> et affecte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> à la propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="7eea3-126">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="7eea3-127">Notez que cet exemple n'utilise pas l'élément `<secureConversationBootstrap>` indiqué dans l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="7eea3-127">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="7eea3-128">Cet exemple présente la confirmation de signature lors de l'utilisation d'un jeton Windows (protocole Kerberos).</span><span class="sxs-lookup"><span data-stu-id="7eea3-128">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="7eea3-129">Dans ce cas, la signature du client est retournée dans toutes les réponses du service et est confirmée par le client.</span><span class="sxs-lookup"><span data-stu-id="7eea3-129">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>

[!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
[!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]

## <a name="see-also"></a><span data-ttu-id="7eea3-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7eea3-130">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [<span data-ttu-id="7eea3-131">Guide pratique pour Créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="7eea3-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="7eea3-132">Guide pratique pour Créer un SecurityBindingElement pour un Mode d’authentification spécifié</span><span class="sxs-lookup"><span data-stu-id="7eea3-132">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
