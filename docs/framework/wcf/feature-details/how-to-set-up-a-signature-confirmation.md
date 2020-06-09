---
title: 'Comment : configurer une confirmation de signature'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 9423922753efee7aac32e430f97307c715e43464
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586913"
---
# <a name="how-to-set-up-a-signature-confirmation"></a>Comment : configurer une confirmation de signature

La *confirmation de signature* est un mécanisme permettant à un initiateur de message de s’assurer qu’une réponse reçue a été générée en réponse au message d’origine de l’expéditeur. La confirmation de signature est définie dans la spécification WS-Security 1.1. Si un point de terminaison prend en charge WS-Security 1.0, vous ne pouvez pas utiliser la confirmation de signature.

Les procédures suivantes spécifient comment activer la confirmation de signature à l'aide de <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Vous pouvez utiliser la même procédure avec <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. La procédure s’appuie sur les étapes de base de la procédure [: créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).

### <a name="to-enable-signature-confirmation-in-code"></a>Pour activer la confirmation de signature dans le code

1. Créez une instance de la classe <xref:System.ServiceModel.Channels.BindingElementCollection>.

2. Créez une instance de la <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> classe.

3. Définissez <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> sur `true`.

4. Ajoutez l’élément de sécurité à la collection de liaisons.

5. Créez une liaison personnalisée, comme indiqué dans [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).

### <a name="to-enable-signature-confirmation-in-configuration"></a>Pour activer la confirmation de signature dans la configuration

1. Ajoutez un élément `<customBinding>` à la section `<bindings>` du fichier de configuration.

2. Ajoutez un élément `<binding>` et affectez une valeur appropriée à l'attribut de nom.

3. Ajoutez un élément d'encodage approprié. L'exemple suivant ajoute un élément `<TextMessageEncoding>`.

4. Ajoutez un élément enfant `<security>` et affectez `requireSignatureConfirmation` à l'attribut `true`.

5. Facultatif. Pour activer la confirmation de signature pendant le démarrage, ajoutez un [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément enfant et affectez à l’attribut la valeur `requireSignatureConfirmation` `true` .

6. Ajoutez un élément de transport approprié. L’exemple suivant ajoute un [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) :

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
- [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Comment : créer un SecurityBindingElement pour un mode d'authentification spécifié](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
