---
title: Fonctionnement des niveaux de protection
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 0c034608-a1ac-4007-8287-b1382eaa8bf2
ms.openlocfilehash: 896b75d3dfb5ebace9bef0c410e4a86dfb765bd8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321526"
---
# <a name="understanding-protection-level"></a>Fonctionnement des niveaux de protection

La propriété `ProtectionLevel` est partagée par de nombreuses classes différentes, par exemple par les classes <xref:System.ServiceModel.ServiceContractAttribute> et <xref:System.ServiceModel.OperationContractAttribute>. Cette propriété contrôle tout ou partie des modalités de protection d'un message. Cette rubrique décrit la fonctionnalité de Windows Communication Foundation (WCF) et son fonctionnement.

Pour obtenir des instructions sur la définition du niveau de protection, consultez [Comment : définir la propriété ProtectionLevel](how-to-set-the-protectionlevel-property.md).

> [!NOTE]
> Les niveaux de protection peuvent uniquement être définis dans le code et non dans la configuration.

## <a name="basics"></a>Principes de base

Le fonctionnement des niveaux de protection ne peut être correctement appréhendé sans comprendre au préalable les principes de base les régissant :

- Il existe trois niveaux de base de protection pour les différentes parties d'un message. La propriété (où qu'elle intervienne) a la valeur de l'une des valeurs d'énumération <xref:System.Net.Security.ProtectionLevel>. Ces valeurs sont (par niveau de protection croissant) :

  - `None`.,

  - `Sign`., La partie protégée est signée numériquement. Cette signature numérique garantit la détection de toute tentative de falsification de la partie protégée d'un message.

  - `EncryptAndSign`., La partie du message est chiffrée pour garantir sa confidentialité avant signature.

- Vous pouvez définir des exigences de protection uniquement pour les *données d’application* avec cette fonctionnalité. Par exemple, les en-têtes WS-Addressing correspondent à des données d'infrastructure, elles ne sont, par conséquent, pas affectées par la propriété `ProtectionLevel`.

- Lorsque le mode de sécurité a la valeur `Transport`, le message est protégé dans sa totalité par les mécanismes de transport. Par conséquent, la définition de niveaux de protection distincts pour ses différentes parties est sans effet.

- La `ProtectionLevel` est un moyen pour le développeur de définir le *niveau minimal* auquel une liaison doit se conformer. Lors du déploiement d'un service, la liaison réelle spécifiée dans la configuration peut ou non prendre en charge ce niveau minimum. Par exemple, la classe <xref:System.ServiceModel.BasicHttpBinding> n'offre, par défaut, aucune sécurité (bien que le système de sécurité puisse être activé). Par conséquent, l'utilisation d'un contrat ayant une valeur autre que `None` provoquera la levée d'une exception.

- Si le service exige que la valeur minimale `ProtectionLevel` pour tous les messages soit `Sign`, un client (peut-être créé par une technologie non-WCF) peut chiffrer et signer tous les messages (ce qui est supérieur au minimum requis). Dans ce cas, WCF ne lèvera pas d’exception, car le client a effectué plus que la valeur minimale. Notez, toutefois, que les applications WCF (services ou clients) ne dépassent pas la sécurité d’une partie de message si possible mais sont conformes au niveau minimal. Notez également que lorsque le paramètre `Transport` est utilisé comme mode de sécurité, celui-ci risque de sur-sécuriser le flux des messages, car, de part sa nature il n'est pas en mesure de les sécuriser à un niveau plus granulaire.

- Si vous affectez explicitement `ProtectionLevel` ou `Sign` à la propriété `EncryptAndSign`, vous devrez alors utiliser une liaison dont la sécurité est activée, faute de quoi une exception sera levée.

- Si vous sélectionnez une liaison qui active la sécurité et que vous ne définissez pas la propriété `ProtectionLevel` à quelque endroit du contrat, toutes les données d’application seront chiffrées et signées.

- Si vous sélectionnez une liaison dont la sécurité n'est pas activée (par exemple, la sécurité de la classe `BasicHttpBinding` est désactivée par défaut) et que la propriété `ProtectionLevel` n'est pas définie explicitement, alors aucune des données d'application ne sera protégée.

- Si vous utilisez une liaison qui applique la sécurité au niveau du transport, toutes les données d’application seront sécurisées en fonction des paramètres de sécurité du transport.

- Si vous utilisez une liaison qui applique la sécurité au niveau du message, les données d’application seront sécurisées en fonction des niveaux de protection définis sur le contrat. Si vous ne spécifiez aucun niveau de protection, toutes les données d'application figurant dans les messages seront chiffrées et signées.

- Des niveaux de portée différents peuvent être affectés à la propriété `ProtectionLevel`. Il existe en effet une hiérarchie dans les niveaux de portée. Cette hiérarchie est abordée en détail dans la section suivante.

## <a name="scoping"></a>Portée

La définition de la propriété `ProtectionLevel` à partir de l'API la plus élevée détermine le niveau de protection pour toutes les interfaces API figurant en dessous. Si une valeur différente est affectée à la propriété `ProtectionLevel` à un niveau inférieur, toutes les API figurant en dessous de ce niveau sont initialisées sur cette nouvelle valeur. En revanche, toutes les API se trouvant au-dessus conservent la valeur affectée à l'API la plus élevée dans la hiérarchie. Cette hiérarchie se présente comme suit : Les attributs au même niveau sont des homologues.

- <xref:System.ServiceModel.ServiceContractAttribute>

- <xref:System.ServiceModel.OperationContractAttribute>

- <xref:System.ServiceModel.FaultContractAttribute>

- <xref:System.ServiceModel.MessageContractAttribute>

- <xref:System.ServiceModel.MessageHeaderAttribute>

- <xref:System.ServiceModel.MessageBodyMemberAttribute>

## <a name="programming-protectionlevel"></a>Programmation de la propriété ProtectionLevel

Pour programmer `ProtectionLevel` à un quelconque niveau de la hiérarchie, il vous suffit d'affecter à la propriété une valeur adéquate lors de l'application de l'attribut. Pour obtenir des exemples, consultez [Comment : définir la propriété ProtectionLevel](how-to-set-the-protectionlevel-property.md).

> [!NOTE]
> La définition de la propriété sur les erreurs et les contrats de message nécessite de comprendre au préalable le fonctionnement de ces fonctionnalités. Pour plus d’informations, consultez [Comment : définir la propriété ProtectionLevel](how-to-set-the-protectionlevel-property.md) et [à l’aide de contrats de message](./feature-details/using-message-contracts.md).

## <a name="ws-addressing-dependency"></a>Dépendance WS-Addressing

Dans la plupart des cas, l’utilisation de l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer un client garantit que les contrats de client et de service sont identiques. Toutefois, des contrats apparemment identiques peuvent provoquer la levée d'une exception de la part du client. Cela se produit lorsqu'une liaison ne prend pas en charge la spécification WS-Addressing et que plusieurs niveaux de protection sont spécifiés sur le contrat. Par exemple, la classe <xref:System.ServiceModel.BasicHttpBinding> ne prend pas en charge cette spécification ni la création de liaisons personnalisées non compatibles avec WS-Addressing. La fonctionnalité `ProtectionLevel` utilise la spécification WS-Addressing pour activer des niveaux de protection différents sur un contrat unique. Si la liaison ne prend pas en charge la spécification WS-Addressing, le même niveau de protection sera affecté à tous les niveaux. Le niveau de protection le plus élevé du contrat sera celui de toutes les portées figurant sur ce dernier.

Un problème, à première vue difficile à résoudre, peut en découler. Il est possible de créer un contrat client (une interface) contenant des méthodes destinées à plusieurs services. Cela signifie que la même interface sera utilisée pour créer le client qui communiquera avec un grand nombre de services et que cette même et seule interface contiendra l'ensemble des méthodes destinées à l'ensemble des services. Dans cette situation peu courante, les développeurs doivent faire attention à utiliser uniquement des méthodes compatibles avec les différents services. Si la liaison correspond à la classe <xref:System.ServiceModel.BasicHttpBinding>, la prise en charge de plusieurs niveaux de protection ne sera pas possible. Toutefois, lorsqu'un service répond à un client, il peut le faire en respectant un niveau de protection inférieur à celui requis. Dans ce cas, le client lèvera une exception, celui-ci s'attendant en effet à un niveau de protection plus élevé.

Un exemple du code illustre ce problème. Un exemple de contrat de service et de client est donné ci-dessous. Supposons que la liaison est l’élément [\<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) . Toutes les opérations figurant sur un contrat disposent alors du même niveau de protection. Ce niveau de protection uniforme est défini comme étant le niveau de protection maximal appliqué à l'ensemble des opérations.

Le contrat de service est :

[!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
[!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]

Le code suivant donne un exemple d'interface de contrat client. Remarque : ce code contient une méthode `Tax` conçue pour être utilisée avec un service différent :

[!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
[!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]

Lorsque le client appelle la méthode `Price`, il lève une exception lorsqu'il reçoit une réponse du service. Cela se produit parce que le client ne spécifie pas de `ProtectionLevel` sur le `ServiceContractAttribute`. Par conséquent, le client utilise la valeur par défaut (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>) pour toutes les méthodes, y compris pour la méthode `Price`. Toutefois, le service retourne la valeur à l'aide du niveau <xref:System.Net.Security.ProtectionLevel.Sign>, le contrat de service définissant une seule méthode dont le niveau de protection a la valeur <xref:System.Net.Security.ProtectionLevel.Sign>. Dans ce cas, le client générera une erreur lors de la validation de la réponse émanant du service.

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageHeaderAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- <xref:System.Net.Security.ProtectionLevel>
- [Sécurisation de services](securing-services.md)
- [Guide pratique pour définir la propriété ProtectionLevel](how-to-set-the-protectionlevel-property.md)
- [Spécification et gestion des erreurs dans les contrats et les services](specifying-and-handling-faults-in-contracts-and-services.md)
- [Utilisation de contrats de message](./feature-details/using-message-contracts.md)
