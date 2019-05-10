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
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Procédure : créer un jeton de contexte de sécurité pour une session sécurisée
En utilisant un jeton de contexte de sécurité avec état (SCT) dans une session sécurisée, la session peut résister au service qui est recyclé. Par exemple, lorsqu'un SCT sans état est utilisé dans une session sécurisée et que les services IIS (Internet Information Services) sont réinitialisés, les données de session associées au service sont perdues. Ces données de session incluent un cache du jeton SCT. Ainsi, la prochaine fois qu'un client enverra au service un SCT sans état, une erreur sera retournée, parce que la clé associée au SCT ne peut pas être récupérée. Toutefois, si un SCT avec état est utilisé, la clé associée au SCT est contenue dans le SCT. Étant donné que la clé est contenue dans le SCT et donc contenue dans le message, la session sécurisée n'est pas affectée par le service qui est recyclé. Par défaut, Windows Communication Foundation (WCF) utilise des SCT sans état dans une session sécurisée. Cette rubrique détaille la manière d’utiliser des SCT avec état dans une session sécurisée.  
  
> [!NOTE]
>  Les SCT avec état ne peuvent pas être utilisés dans une session sécurisée qui implique un contrat dérivé de <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
> [!NOTE]
>  Pour les applications qui utilisent des SCT avec état dans une session sécurisée, l’identité de thread pour le service doit être un compte d’utilisateur ayant un profil utilisateur associé. Lorsque le service est exécuté sous un compte qui n'a pas de profil utilisateur, tel qu'un `Local Service`, une exception peut être levée.  
  
> [!NOTE]
>  Lorsque l’emprunt d’identité est requis sur Windows XP, utilisez une session sécurisée sans SCT avec état. Lorsque des SCT avec état sont utilisés avec l’emprunt d’identité, une <xref:System.InvalidOperationException> est levée. Pour plus d’informations, consultez [scénarios non pris en charge](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Pour utiliser des SCT avec état dans une session sécurisée  
  
- Créez une liaison personnalisée qui spécifie que les messages SOAP sont protégés par une session sécurisée qui utilise un SCT avec état.  
  
    1. Définissez une liaison personnalisée, en ajoutant un [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) au fichier de configuration pour le service.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2. Ajouter un [ \<liaison >](../../../../docs/framework/misc/binding.md) élément enfant à la [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Spécifiez un nom de liaison en affectant à l'attribut `name` un nom unique dans le fichier de configuration.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3. Spécifiez le mode d’authentification pour les messages envoyés vers et à partir de ce service en ajoutant un [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) élément enfant à la [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Spécifiez qu'une session sécurisée est utilisée en affectant à l'attribut `authenticationMode` la valeur `SecureConversation`. Spécifiez que des SCT avec état sont utilisés en affectant à l'attribut `requireSecurityContextCancellation` la valeur `false`.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4. Spécifiez comment le client est authentifié pendant que la session sécurisée est établie en ajoutant un [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément enfant à la [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Spécifiez comment le client est authentifié en définissant l'attribut `authenticationMode`.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. Spécifier l’encodage de message en ajoutant un élément d’encodage, tel que [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. Spécifier le transport en ajoutant un élément de transport, tel que le [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```xml  
        <httpTransport />  
        ```  
  
     L’exemple de code suivant utilise la configuration pour spécifier une liaison personnalisée que les messages peuvent utiliser avec des SCT avec état dans une session sécurisée.  
  
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
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant crée une liaison personnalisée qui utilise le mode d’authentification <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> pour démarrer une session sécurisée.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Lorsque l’authentification Windows est utilisée en association avec un SCT avec état, WCF ne remplit pas la <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> propriété avec l’appelant réel de l’identité, mais au lieu de cela affecte à la propriété anonyme. Étant donné que la sécurité WCF doit recréer le contenu du contexte de sécurité du service pour chaque demande du SCT entrant, le serveur de ne pas un suivi de la session de sécurité dans la mémoire. Comme il est impossible de sérialiser l'instance <xref:System.Security.Principal.WindowsIdentity> dans le SCT, la propriété <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> retourne une identité anonyme.  
  
 La configuration suivante expose ce comportement.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
