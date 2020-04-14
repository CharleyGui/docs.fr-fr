---
title: Substitution de l'identité d'un service pour l'authentification
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: 5649ef4cc05c9c16b1f8f626ba5e2e584b0e52eb
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278910"
---
# <a name="override-the-identity-of-a-service-for-authentication"></a>Remplacer l’identité d’un service d’authentification

Généralement, vous n'avez pas besoin de définir l'identité sur un service car la sélection d'un type d'informations d'identification du client impose le type d'identité exposé dans les métadonnées du service. Par exemple, le code de configuration suivant utilise [ \<l’élément wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) et définit l’attribut `clientCredentialType` à Windows.  

 Le fragment WSDL (Web Services Description Language) suivant affiche l'identité du point de terminaison défini précédemment. Dans cet exemple, le service fonctionne comme un service auto-hébergé sous un compte utilisateur particulier (username@contoso.com) et donc le nom principal de l’utilisateur (UPN) identité contient le nom du compte. L’UPN est également connu sous le nom de l’utilisateur dans un domaine Windows.  

 Pour une application d’échantillon qui démontre le réglage d’identité, voir [l’échantillon d’identité de service](../samples/service-identity-sample.md). Pour plus d’informations sur l’identité du service, voir [Identité de service et authentification](../feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Authentification et identité Kerberos  
 Par défaut, lorsqu’un service est configuré pour utiliser un identifiant Windows, un élément [ \<>d’identité](../../configure-apps/file-schema/wcf/identity.md) qui contient un [ \<utilisateurPrincipalName>](../../configure-apps/file-schema/wcf/userprincipalname.md) ou [ \<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) élément est généré dans le WSDL. Si le service est `LocalSystem` `LocalService`en `NetworkService` cours d’exécution sous le , , ou le `host/` \<compte, un nom principal de service (SPN) est généré par défaut sous la forme de nom *d’hôte*> parce que ces comptes ont accès aux données SPN de l’ordinateur. Si le service fonctionne sous un compte différent, Windows Communication Foundation (WCF) génère un UPN sous la forme de \< *nom d’utilisateur*>@<*domainName*`>`. Cela est dû au fait que l'authentification Kerberos requiert qu'un UPN ou SPN soit fourni au client pour authentifier le service.  
  
 Vous pouvez également utiliser l’outil [Setspn](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731241(v=ws.10)?redirectedfrom=MSDN) pour enregistrer un SPN supplémentaire avec le compte d’un service dans un domaine. Vous pouvez ensuite utiliser le SPN comme identité du service. Pour plus d’informations sur l’outil, voir [Setspn Aperçu](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).  
  
> [!NOTE]
> Pour utiliser le type d'informations d'identification Windows sans négociation, le compte d'utilisateur du service doit avoir accès au SPN inscrit avec le domaine Active Directory. Pour ce faire, vous pouvez procéder de différentes façons :  
  
- Utilisez le compte NetworkService ou LocalSystem pour exécuter votre service. Étant donné que ces comptes ont accès à la machine SPN qui est établie lorsque la machine rejoint le domaine Active Directory, WCF génère automatiquement l’élément SPN approprié à l’intérieur du point de terminaison du service dans les métadonnées du service (WSDL).  
  
- Utilisez un compte de domaine Active Directory arbitraire pour exécuter votre service. Dans ce cas, établissez un SPN pour ce compte de domaine, pour cela vous pouvez vous servir de l'utilitaire Setspn.exe. Une fois que vous avez créé le SPN pour le compte du service, configurez WCF pour publier ce SPN aux clients du service par le biais de ses métadonnées (WSDL). Pour cela, il suffit de définir l'identité du point de terminaison exposé, à l'aide d'un fichier de configuration d'application ou du code.  
  
 Pour plus d’informations sur les SN, le protocole Kerberos, et Active Directory, voir [Supplément technique Kerberos pour Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Lorsque SPN ou UPN équivaut à une chaîne vide  
 Si vous attribuez une valeur de chaîne vide à SPN ou UPN, plusieurs choses se produisent, en fonction du niveau de sécurité et du mode d'authentification utilisés :  
  
- Si vous utilisez la sécurité de niveau transport, l'authentification NTLM (NT LanMan) est choisie.  
  
- Si vous utilisez la sécurité de niveau message, l'authentification peut échouer, en fonction du mode d'authentification.  
  
- Si vous `spnego` utilisez le `AllowNtlm` mode et `false`l’attribut est configuré, l’authentification échoue.  
  
- Si vous `spnego` utilisez le `AllowNtlm` mode et `true`l’attribut est configuré, l’authentification échoue si l’UPN est vide mais réussit si le SPN est vide.  
  
- Si vous utilisez Kerberos direct (également appelé « one-shot »), l'authentification échoue.  
  
### <a name="use-the-identity-element-in-configuration"></a>Utilisez \<l’identité> Element dans la configuration  
 Si vous modifiez le type d’identification du client dans la liaison précédemment indiquée, `Certificate`alors le WSDL généré contient un certificat X.509 sérialisé Base64 pour la valeur d’identité comme indiqué dans le code suivant. Il s'agit de la valeur par défaut pour tous les types d'informations d'identification du client autres que Windows.  

 Vous pouvez modifier la valeur de l’identité du service par défaut `identity` ou modifier le type d’identité en utilisant l’élément <> dans la configuration ou en définissant l’identité dans le code. Le code de configuration suivant affecte à une identité DNS (Domain Name System) la valeur `contoso.com`.  

### <a name="set-identity-programmatically"></a>Définir l’identité de façon programmatique  
 Votre service n’a pas à spécifier explicitement une identité, car WCF la détermine automatiquement. Cependant, WCF vous permet de spécifier une identité sur un point de terminaison, si nécessaire. Le code suivant ajoute un point de terminaison de service avec une identité DNS spécifique.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer un vérificateur d’identité du client personnalisé](how-to-create-a-custom-client-identity-verifier.md)
- [Identité du service et authentification](../feature-details/service-identity-and-authentication.md)
