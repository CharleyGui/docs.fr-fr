---
title: 'Procédure : spécifier le type d’informations d’identification de client'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: b45d7b58d8a1fe79f9d7a8cff6e328b46633985c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293674"
---
# <a name="how-to-specify-the-client-credential-type"></a>Procédure : spécifier le type d’informations d’identification de client

Après avoir défini un mode de sécurité (transport ou message), vous avez pouvez définir le type d'informations d'identification du client. Cette propriété spécifie le type d'informations d'identification que le client doit fournir au service dans le cadre de l'authentification. Pour plus d’informations sur la définition du mode de sécurité (étape nécessaire avant de définir le type d’informations d’identification du client), consultez [Comment : définir le mode de sécurité](how-to-set-the-security-mode.md).  
  
### <a name="to-set-the-client-credential-type-in-code"></a>Pour définir le type d'informations d'identification du client dans le code  
  
1. Créez une instance de la liaison que le service utilisera. Cet exemple utilise la liaison <xref:System.ServiceModel.WSHttpBinding>.  
  
2. Affectez à la propriété <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> une valeur appropriée. Cet exemple utilise le mode de message.  
  
3. Affectez à la propriété <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> une valeur appropriée. Dans notre exemple, la propriété est définie de sorte à utiliser l'authentification Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>Pour définir le type d'informations d'identification du client dans la configuration  
  
1. Ajoutez un [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) élément au fichier de configuration.  
  
2. En tant qu’élément enfant, ajoutez un [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) élément.  
  
3. Ajoutez une liaison appropriée. Cet exemple utilise l' [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) élément.  
  
4. Ajoutez un [\<binding>](../configure-apps/file-schema/wcf/bindings.md) élément et affectez `name` à l’attribut une valeur appropriée. Cet exemple utilise le nom « SecureBinding ».  
  
5. Ajoutez une liaison `<security>`. Affectez la valeur appropriée à l'attribut `mode`. Cet exemple lui affecte la valeur `"Message"`.  
  
6. Ajoutez un élément `<message>` ou un élément `<transport>` comme requis par le mode de sécurité. Affectez la valeur appropriée à l'attribut `clientCredentialType`. Cet exemple utilise `"Windows"`.  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation de services](securing-services.md)
- [Procédure : définir le mode de sécurité](how-to-set-the-security-mode.md)
