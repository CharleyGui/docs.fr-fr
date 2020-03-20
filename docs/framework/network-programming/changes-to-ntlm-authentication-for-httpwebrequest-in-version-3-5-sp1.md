---
title: Changements apportés à l’authentification NTLM pour HttpWebRequest dans la version 3.5 SP1
ms.date: 03/30/2017
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
ms.openlocfilehash: 388e6dc648e1fd68e24a852cb08de107f09f9c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "64754879"
---
# <a name="changes-to-ntlm-authentication-for-httpwebrequest-in-version-35-sp1"></a>Changements apportés à l’authentification NTLM pour HttpWebRequest dans la version 3.5 SP1

Des changements de sécurité apportés au .NET Framework version 3.5 SP1 et ultérieures affectent la manière dont l’intégration de l’authentification Windows est gérée par <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Security.NegotiateStream> et les classes associées dans l’espace de noms System.Net. Ces changements peuvent affecter les applications qui utilisent ces classes pour effectuer des requêtes web et recevoir des réponses dans lesquelles l’authentification Windows intégrée en fonction de NTLM est utilisée. Ce changement peut avoir un impact sur les serveurs web et les applications clientes configurés pour utiliser l’authentification Windows intégrée.

## <a name="overview"></a>Vue d’ensemble

La conception de l’authentification Windows intégrée permet à certaines réponses d’informations d’identification d’être universelles, ce qui signifie qu’elles peuvent être réutilisées ou transférées. Si cette fonctionnalité de conception n’est pas nécessaire, les protocoles d’authentification doivent comporter des informations propres à la cible et au canal. Les services peuvent ensuite fournir une protection étendue pour garantir que les réponses d’informations d’identification contiennent des informations propres aux services, telles qu’un nom de principal du service (SPN). Avec ces informations dans les échanges d’informations d’identification, les services peuvent offrir une meilleure protection contre toute utilisation malveillante des réponses d’informations d’identification qui pourraient avoir été obtenues de manière incorrecte.

Plusieurs composants des espaces de noms <xref:System.Net> et <xref:System.Net.Security> effectuent l’authentification Windows intégrée pour le compte d’une application appelante. Cette section décrit les modifications apportées aux composants System.Net pour ajouter une protection étendue lors de l’utilisation de l’authentification Windows intégrée.

## <a name="changes"></a>Modifications

Le processus d’authentification NTLM utilisé avec l’authentification Windows intégrée inclut une stimulation émise par l’ordinateur de destination et renvoyée à l’ordinateur client. Quand un ordinateur reçoit une stimulation qu’il a lui-même généré, l’authentification échoue, sauf si la connexion est une connexion de retour de boucle (adresse IPv4 127.0.0.1, par exemple).

Quand vous accédez à un service en cours d’exécution sur un serveur web interne, il est courant d’accéder au service à l’aide d’une URL semblable à `http://contoso/service` ou `https://contoso/service`. Le nom « contoso » est rarement le nom de l’ordinateur sur lequel le service est déployé. <xref:System.Net> et les espaces de noms associés prennent en charge l’utilisation d’Active Directory, de DNS, de NetBIOS, du fichier hosts de l’ordinateur local (généralement WINDOWS\system32\drivers\etc\hosts) ou du fichier lmhosts de l’ordinateur local (généralement WINDOWS\system32\drivers\etc\lmhosts) pour résoudre les noms en adresses. Le nom « contoso » est résolu pour que les demandes envoyées à « contoso » soient envoyées à l’ordinateur serveur approprié.

En cas de configuration pour des déploiements à grande échelle, il est également courant d’attribuer un nom de serveur virtuel unique au déploiement, sans que les noms d’ordinateurs sous-jacents ne soient jamais utilisés par les applications clientes et les utilisateurs finaux. Par exemple, vous pourriez appeler le serveur `www.contoso.com`, mais utiliser simplement « contoso » sur un réseau interne. Ce nom porte le nom d’en-tête d’hôte dans la requête web du client. Comme spécifié par le protocole HTTP, le champ d’en-tête de requête d’hôte spécifie le numéro de port et l’hôte Internet de la ressource demandée. Ces informations sont obtenues à partir de l’URI d’origine donné par l’utilisateur ou la ressource de référence (généralement une URL HTTP). Dans le .NET Framework version 4, ces informations peuvent aussi être définies par le client à l’aide de la nouvelle propriété <xref:System.Net.HttpWebRequest.Host%2A>.

La classe <xref:System.Net.AuthenticationManager> contrôle les composants d’authentification gérés (« modules ») qui sont utilisés par les classes dérivés <xref:System.Net.WebRequest> et la classe <xref:System.Net.WebClient>. La classe <xref:System.Net.AuthenticationManager> fournit une propriété qui expose un objet <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType>, indexé par chaîne d’URI, pour que les applications puissent fournir une chaîne de nom de principal du service personnalisée à utiliser lors de l’authentification.

La version 3.5 SP1 spécifie désormais par défaut le nom d’hôte utilisé dans l’URL de requête dans le SPN lors de l’échange d’authentification NTLM (NT LAN Manager) quand la propriété <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> n’est pas définie. Le nom d’hôte utilisé dans l’URL de requête peut être différent de l’en-tête d’hôte spécifié dans <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType> dans la requête du client. Le nom d’hôte utilisé dans l’URL de requête peut être différent du nom d’hôte réel du serveur, du nom d’ordinateur du serveur, de l’adresse IP de l’ordinateur ou de l’adresse de bouclage. Dans ce cas, Windows fait échouer la requête d’authentification. Pour résoudre ce problème, nous devons signaler à Windows que le nom d’hôte utilisé dans l’URL de requête dans la requête du client (par exemple « contoso ») est en fait un autre nom pour l’ordinateur local.

Il existe plusieurs manières pour une application serveur de contourner cette modification. L’approche recommandée consiste à mapper le nom d’hôte utilisé dans l’URL de requête à la clé `BackConnectionHostNames` dans le Registre sur le serveur. La clé de Registre `BackConnectionHostNames` sert normalement à mapper un nom d’hôte à une adresse de bouclage. Les étapes sont listées ci-dessous.

Pour spécifier les noms d’hôtes qui sont mappés à l’adresse de bouclage et qui peuvent se connecter à des sites web sur un ordinateur local, effectuez les étapes suivantes :

1. Cliquez sur Démarrer, sur Exécuter, tapez regedit, puis cliquez sur OK.

2. Dans l’Éditeur du Registre, recherchez la clé de Registre suivante et cliquez dessus :

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`

3. Cliquez avec le bouton droit sur MSV1_0, pointez sur Nouveau, puis cliquez sur Valeur de chaînes multiples.

4. Saisissez `BackConnectionHostNames`, puis appuyez sur ENTRÉE.

5. Cliquez avec le bouton droit sur `BackConnectionHostNames`, puis cliquez sur Modifier.

6. Dans la zone Données de la valeur, tapez les noms d’hôtes pour les sites (ceux utilisés dans l’URL de requête) qui sont sur l’ordinateur local, puis cliquez sur OK.

7. Quittez l’Éditeur du Registre, puis redémarrez le service IISAdmin et exécutez IISReset.

Une solution de contournement moins sécurisée consiste à désactiver le contrôle de retour de boucle, comme décrit dans <https://support.microsoft.com/kb/896861>. Cette opération désactive la protection contre les attaques par réflexion. Il est donc préférable de limiter l’ensemble des autres noms aux seuls noms qui seront utilisés par l’ordinateur.

## <a name="see-also"></a>Voir aussi

- <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType>
- <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=nameWithType>
