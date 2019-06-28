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
# <a name="how-to-set-up-a-signature-confirmation"></a>Procédure : configurer une confirmation de signature

*Confirmation de signature* est un mécanisme pour un initiateur de message pour vous assurer qu’une réponse reçue a été générée en réponse au message d’origine de l’expéditeur. La confirmation de signature est définie dans la spécification WS-Security 1.1. Si un point de terminaison prend en charge WS-Security 1.0, vous ne pouvez pas utiliser la confirmation de signature.

Les procédures suivantes spécifient comment activer la confirmation de signature à l'aide de <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Vous pouvez utiliser la même procédure avec <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. La procédure repose sur les étapes de base indiquées dans [Comment : Créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).

### <a name="to-enable-signature-confirmation-in-code"></a>Pour activer la confirmation de signature dans le code

1. Créez une instance de la classe <xref:System.ServiceModel.Channels.BindingElementCollection>.

2. Créez une instance de la <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> classe.

3. Affectez <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> à `true`.

4. Ajoutez l’élément de sécurité à la collection de liaisons.

5. Créer une liaison personnalisée, tel que spécifié dans [Comment : Créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).

### <a name="to-enable-signature-confirmation-in-configuration"></a>Pour activer la confirmation de signature dans la configuration

1. Ajoutez un élément `<customBinding>` à la section `<bindings>` du fichier de configuration.

2. Ajoutez un élément `<binding>` et affectez une valeur appropriée à l'attribut de nom.

3. Ajoutez un élément d'encodage approprié. L'exemple suivant ajoute un élément `<TextMessageEncoding>`.

4. Ajoutez un élément enfant `<security>` et affectez `requireSignatureConfirmation` à l'attribut `true`.

5. Facultatif. Pour activer la confirmation de signature pendant le démarrage, ajoutez un [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément enfant et définissez le `requireSignatureConfirmation` attribut `true`.

6. Ajoutez un élément de transport approprié. L’exemple suivant ajoute un [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):

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

## <a name="example"></a>Exemple

Le code suivant crée une instance de <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> et affecte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> à la propriété `true`. Notez que cet exemple n'utilise pas l'élément `<secureConversationBootstrap>` indiqué dans l'exemple précédent. Cet exemple présente la confirmation de signature lors de l'utilisation d'un jeton Windows (protocole Kerberos). Dans ce cas, la signature du client est retournée dans toutes les réponses du service et est confirmée par le client.

[!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
[!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [Guide pratique pour Créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Guide pratique pour Créer un SecurityBindingElement pour un Mode d’authentification spécifié](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
