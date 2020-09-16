---
title: 'Procédure : verrouiller des points de terminaison dans l’entreprise'
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: 68a7b80a01d9b1a8c5243331e63a1b82996e8ee6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558145"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Procédure : verrouiller des points de terminaison dans l’entreprise

Les entreprises de grande taille exigent souvent que les applications soient développées conformément à leurs stratégies de sécurité. La rubrique suivante explique comment développer et installer un validateur de point de terminaison client qui peut être utilisé pour valider toutes les applications clientes Windows Communication Foundation (WCF) installées sur les ordinateurs.

Dans ce cas, le validateur est un validateur client, car ce comportement de point de terminaison est ajouté à la [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) section client dans le fichier machine.config. WCF charge uniquement les comportements de point de terminaison communs pour les applications clientes et charge uniquement les comportements de service communs pour les applications de service. Pour installer ce même validateur pour les applications de service, le validateur doit être un comportement de service. Pour plus d’informations, consultez la [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) section.

> [!IMPORTANT]
> Les comportements de service ou de point de terminaison non marqués avec l' <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribut (APTCA) qui sont ajoutés à la [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) section d’un fichier de configuration ne sont pas exécutés quand l’application s’exécute dans un environnement de confiance partielle, et aucune exception n’est levée lorsque cela se produit. Pour appliquer l'exécution des comportements courants tels que les validateurs, vous devez effectuer l'une des actions suivantes :
>
> - Marquez votre comportement courant avec l' <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribut afin qu’il puisse s’exécuter lorsqu’il est déployé comme une application de confiance partielle. Notez qu'une entrée de Registre peut être définie sur l'ordinateur pour interdire l'exécution des assemblys marqués avec l'attribut APTCA.
>
> - Assurez-vous que si l’application est déployée comme une application de confiance totale, les utilisateurs ne peuvent pas modifier les paramètres de sécurité d’accès du code pour exécuter l’application dans un environnement de confiance partielle. S'ils peuvent le faire, le validateur personnalisé ne s'exécute pas et aucune exception n'est levée. Pour une façon de procéder, consultez l' `levelfinal` option à l’aide de l' [outil stratégie de sécurité d’accès du Code (Caspol.exe)](../../tools/caspol-exe-code-access-security-policy-tool.md).
>
> Pour plus d’informations, consultez [meilleures pratiques de confiance partielle](../feature-details/partial-trust-best-practices.md) et [scénarios de déploiement pris en charge](../feature-details/supported-deployment-scenarios.md).

### <a name="to-create-the-endpoint-validator"></a>Pour créer le validateur de point de terminaison

1. Créez un objet <xref:System.ServiceModel.Description.IEndpointBehavior> avec les étapes de validation souhaitées dans la méthode <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A>. Le code suivant montre un exemple. ( `InternetClientValidatorBehavior` Est extrait de l’exemple [Security validation](../samples/security-validation.md) .)

    [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]

2. Créez un objet <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> qui enregistre le validateur de point de terminaison créé à l'étape 1. L'exemple de code suivant illustre ce point. (Le code d’origine de cet exemple se trouve dans l’exemple [Security validation](../samples/security-validation.md) .)

    [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]

3. Assurez-vous que l'assembly compilé est signé avec un nom fort. Pour plus d’informations, consultez l' [outil Strong Name Tool (SN.EXE)](../../tools/sn-exe-strong-name-tool.md) et les commandes du compilateur pour votre langage.

### <a name="to-install-the-validator-into-the-target-computer"></a>Pour installer le validateur dans l'ordinateur cible

1. Installez le validateur de point de terminaison à l'aide du mécanisme approprié. Dans une entreprise, cela peut s'effectuer en utilisant la stratégie de groupe ou SMS (Systems Management Server).

2. Installez l’assembly avec nom fort dans le Global Assembly Cache à l’aide de la [Gacutil.exe (outil global assembly cache)](../../tools/gacutil-exe-gac-tool.md).

3. Utilisez les types d'espaces de noms <xref:System.Configuration?displayProperty=nameWithType> pour :

    1. Ajoutez l’extension à la [\<behaviorExtensions>](../../configure-apps/file-schema/wcf/behaviorextensions.md) section à l’aide d’un nom de type qualifié complet et verrouillez l’élément.

         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]

    2. Ajoutez l’élément de comportement à la `EndpointBehaviors` propriété de la [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) section et verrouillez l’élément. (Pour installer le validateur sur le service, le validateur doit être un <xref:System.ServiceModel.Description.IServiceBehavior> et être ajouté à la `ServiceBehaviors` propriété.) L’exemple de code suivant montre la configuration appropriée après les étapes a. et b., à la seule exception qu'il n'y a pas de nom fort.

        [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]

    3. Enregistrez le fichier machine.config. L'exemple de code suivant exécute l'ensemble des tâches dans l'étape 3, mais enregistre une copie du fichier machine.config modifié localement.

        [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]

## <a name="example"></a> Exemple

L'exemple de code suivant indique comment ajouter un comportement commun au fichier machine.config et enregistrer une copie sur le disque. `InternetClientValidatorBehavior`Est extrait de l’exemple [Security validation](../samples/security-validation.md) .

[!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]

## <a name="net-framework-security"></a>Sécurité du .NET Framework

Vous pouvez également chiffrer les éléments du fichier de configuration. Pour plus d'informations, consultez la section Voir aussi.

## <a name="see-also"></a>Voir aussi

- [Chiffrement des éléments de fichier de configuration à l'aide de DPAPI](/previous-versions/msp-n-p/ff647398(v=pandp.10))
- [Chiffrement des éléments de fichier de configuration à l'aide de RSA](/previous-versions/msp-n-p/ff650304(v=pandp.10))
