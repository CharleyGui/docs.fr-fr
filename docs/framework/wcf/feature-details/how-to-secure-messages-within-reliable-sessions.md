---
title: 'Procédure : sécuriser des messages au sein de sessions fiables'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: cec9356467886be022d05ead55d5cb6ccddcd838
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558678"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Procédure : sécuriser des messages au sein de sessions fiables

Cette rubrique décrit les étapes requises pour activer la sécurité au niveau du message pour les messages échangés dans une session fiable utilisant l’une des liaisons fournies par le système qui prennent en charge une telle session, mais pas par défaut. Activez une session sécurisée et fiable soit de manière impérative en utilisant le code, soit de façon déclarative dans le fichier de configuration. Cette procédure utilise le client et les fichiers de configuration du service pour activer la session fiable sécurisée.

La procédure inclut les trois tâches clés suivantes :

1. Spécifiez que le client et le service échangent des messages dans une session fiable.

1. Requérez la sécurité au niveau du message dans la session fiable.

1. Spécifiez le type d'informations d'identification que le client doit utiliser pour être authentifié auprès du service.

Il est important, dans la première tâche, que l’élément de configuration de point de terminaison contienne un `bindingConfiguration` attribut qui référence une configuration de liaison nommée (dans cet exemple) `MessageSecurity` . L' [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) élément de configuration référence ensuite ce nom pour activer des sessions fiables en affectant `enabled` à l’attribut de l’élément la valeur [**\<reliableSession>**](/previous-versions/ms731375(v=vs.90)) `true` . Vous pouvez requérir que les assurances de remise ordonnée soient disponibles dans une session fiable en affectant à l'attribut `ordered` la valeur `true`.

Pour obtenir la copie source de l’exemple sur lequel cette procédure de configuration est basée, consultez la [session WS Reliable](../samples/ws-reliable-session.md).

Les éléments essentiels de la deuxième tâche sont atteints en affectant `mode` à l’attribut de l' **\<security>** élément contenu dans l' **\<binding>** élément du client et du service la valeur `Message` .

Les éléments essentiels de la troisième tâche sont atteints en affectant `clientCredentialType` à l’attribut de l' **\<message>** élément contenu dans l' **\<security>** élément du client et du service la valeur `Certificate` .

> [!NOTE]
> Lors de l’utilisation de la sécurité de message avec des sessions fiables, la messagerie fiable tente d’authentifier un client non authentifié jusqu’à ce qu’un délai d’attente se produise au lieu de lever une exception lors du premier échec.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Configurer le service avec une liaison WSHttpBinding pour utiliser une session fiable

Cette procédure est décrite dans [Comment : échanger des messages au sein d’une session fiable](how-to-exchange-messages-within-a-reliable-session.md).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Configurer le client avec une liaison WSHttpBinding pour utiliser une session fiable

Cette procédure est décrite dans [Comment : échanger des messages au sein d’une session fiable](how-to-exchange-messages-within-a-reliable-session.md).

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Définir le mode et ClientCredentialType dans la configuration

1. Ajoutez un élément de liaison approprié à l' [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) élément du fichier de configuration. L’exemple suivant ajoute un [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) élément.

1. Ajoutez un **\<binding>** élément et affectez `name` à son attribut une valeur appropriée. L’exemple utilise le nom `MessageSecurity` .

1. Ajoutez un **\<security>** élément et affectez `mode` à l’attribut la valeur `Message` .

1. Dans l' **\<security>** élément, ajoutez un **\<message>** élément et affectez `clientCredentialType` à l’attribut la valeur `Certificate` .

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
