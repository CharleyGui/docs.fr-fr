---
title: Substitution de l'identité d'un service pour l'authentification
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: 3ac2d48962dd96535e1a08310570212121eca986
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555417"
---
# <a name="override-the-identity-of-a-service-for-authentication"></a>Remplacer l’identité d’un service pour l’authentification

Généralement, vous n'avez pas besoin de définir l'identité sur un service car la sélection d'un type d'informations d'identification du client impose le type d'identité exposé dans les métadonnées du service. Par exemple, le code de configuration suivant utilise l' [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) élément et affecte `clientCredentialType` à l’attribut la valeur Windows.  

 Le fragment WSDL (Web Services Description Language) suivant affiche l'identité du point de terminaison défini précédemment. Dans cet exemple, le service s’exécute en tant que service auto-hébergé sous un compte d’utilisateur particulier ( username@contoso.com ) et, par conséquent, l’identité UPN (nom d’utilisateur principal) contient le nom du compte. L’UPN est également appelé nom de connexion de l’utilisateur dans un domaine Windows.  

 Pour obtenir un exemple d’application illustrant le paramètre d’identité, consultez [exemple d’identité de service](../samples/service-identity-sample.md). Pour plus d’informations sur l’identité du service, consultez [identité du service et authentification](../feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Authentification et identité Kerberos  
 Par défaut, lorsqu’un service est configuré pour utiliser des informations d’identification Windows, un [\<identity>](../../configure-apps/file-schema/wcf/identity.md) élément qui contient un [\<userPrincipalName>](../../configure-apps/file-schema/wcf/userprincipalname.md) [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) élément ou est généré dans le WSDL. Si le service s’exécute sous le `LocalSystem` `LocalService` compte, ou `NetworkService` , un nom de principal du service (SPN) est généré par défaut sous la forme, `host/` \<*hostname*> car ces comptes ont accès aux données SPN de l’ordinateur. Si le service s’exécute sous un compte différent, Windows Communication Foundation (WCF) génère un UPN au format \<*username*> @< *nom_domaine* `>` . Cela est dû au fait que l'authentification Kerberos requiert qu'un UPN ou SPN soit fourni au client pour authentifier le service.  
  
 Vous pouvez également utiliser l’outil [setspn](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731241(v=ws.10)) pour enregistrer un SPN supplémentaire avec le compte d’un service dans un domaine. Vous pouvez ensuite utiliser le SPN comme identité du service. Pour plus d’informations sur l’outil, consultez [vue d’ensemble de setspn](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).  
  
> [!NOTE]
> Pour utiliser le type d'informations d'identification Windows sans négociation, le compte d'utilisateur du service doit avoir accès au SPN inscrit avec le domaine Active Directory. Pour ce faire, vous pouvez procéder de différentes façons :  
  
- Utilisez le compte NetworkService ou LocalSystem pour exécuter votre service. Étant donné que ces comptes ont accès au SPN de l’ordinateur qui est établi lorsque l’ordinateur rejoint le domaine Active Directory, WCF génère automatiquement l’élément SPN approprié à l’intérieur du point de terminaison du service dans les métadonnées du service (WSDL).  
  
- Utilisez un compte de domaine Active Directory arbitraire pour exécuter votre service. Dans ce cas, établissez un SPN pour ce compte de domaine, pour cela vous pouvez vous servir de l'utilitaire Setspn.exe. Une fois que vous avez créé le SPN pour le compte du service, configurez WCF pour publier ce SPN sur les clients du service par le biais de ses métadonnées (WSDL). Pour cela, il suffit de définir l'identité du point de terminaison exposé, à l'aide d'un fichier de configuration d'application ou du code.  
  
 Pour plus d’informations sur les noms de principal du service, le protocole Kerberos et Active Directory, consultez [supplément technique Kerberos pour Windows](/previous-versions/msp-n-p/ff649429(v=pandp.10)).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Lorsque SPN ou UPN équivaut à une chaîne vide  
 Si vous attribuez une valeur de chaîne vide à SPN ou UPN, plusieurs choses se produisent, en fonction du niveau de sécurité et du mode d'authentification utilisés :  
  
- Si vous utilisez la sécurité de niveau transport, l'authentification NTLM (NT LanMan) est choisie.  
  
- Si vous utilisez la sécurité de niveau message, l'authentification peut échouer, en fonction du mode d'authentification.  
  
- Si vous utilisez `spnego` le mode et que l' `AllowNtlm` attribut a la valeur `false` , l’authentification échoue.  
  
- Si vous utilisez `spnego` le mode et que l' `AllowNtlm` attribut a la valeur `true` , l’authentification échoue si le nom d’utilisateur principal est vide mais réussit si le SPN est vide.  
  
- Si vous utilisez Kerberos direct (également appelé « one-shot »), l'authentification échoue.  
  
### <a name="use-the-identity-element-in-configuration"></a>Utiliser l' \<identity> élément dans la configuration  
 Si vous modifiez le type d’informations d’identification du client dans la liaison précédemment indiquée à `Certificate` , alors le WSDL généré contient un certificat X. 509 sérialisé en base64 pour la valeur d’identité, comme indiqué dans le code suivant. Il s'agit de la valeur par défaut pour tous les types d'informations d'identification du client autres que Windows.  

 Vous pouvez modifier la valeur de l’identité de service par défaut ou modifier le type de l’identité à l’aide de l' `identity` élément <> dans la configuration ou en définissant l’identité dans le code. Le code de configuration suivant affecte à une identité DNS (Domain Name System) la valeur `contoso.com`.  

### <a name="set-identity-programmatically"></a>Définir l’identité par programmation  
 Votre service n’a pas besoin de spécifier explicitement une identité, car WCF le détermine automatiquement. Toutefois, WCF vous permet de spécifier une identité sur un point de terminaison, si nécessaire. Le code suivant ajoute un point de terminaison de service avec une identité DNS spécifique.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : créer un vérificateur d’identité du client personnalisé](how-to-create-a-custom-client-identity-verifier.md)
- [Identité du service et authentification](../feature-details/service-identity-and-authentication.md)
