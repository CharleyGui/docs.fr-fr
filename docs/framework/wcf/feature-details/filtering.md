---
title: Filtrage
ms.date: 03/30/2017
ms.assetid: 4002946c-e34a-4356-8cfb-e25912a4be63
ms.openlocfilehash: cc95852a5eb191befe7e3cd563939c340ef16e06
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268480"
---
# <a name="filtering"></a>Filtrage

Le système de filtrage Windows Communication Foundation (WCF) peut utiliser des filtres déclaratifs pour faire correspondre des messages et prendre des décisions opérationnelles. Vous pouvez utiliser des filtres pour déterminer ce qu'il faut faire d'un message en examinant une partie du message. Par exemple, un processus de mise en file d’attente peut utiliser une requête XPath 1.0 pour vérifier l’élément prioritaire d’un en-tête connu afin de déterminer s’il faut déplacer un message au début de la file d’attente.  
  
 Le système de filtrage est constitué d’un ensemble de classes qui permettent de déterminer efficacement le jeu de filtres `true` pour un message WCF particulier.  
  
 Le système de filtrage est un composant principal de la messagerie WCF. Il est conçu pour être extrêmement rapide. Chaque implémentation de filtre a été optimisée pour un type particulier de correspondance avec les messages WCF.  
  
 Le système de filtrage n'est pas thread-safe. L'application doit gérer toute sémantique de verrouillage. Toutefois, elle prend en charge les sémantiques writer unique/lecteurs multiples.  
  
## <a name="where-filtering-fits"></a>Cas dans lesquels le filtrage est applicable  

 Le filtrage est exécuté après qu'un message a été reçu et fait partie du processus de la distribution du message au composant d'application qui convient. La conception du système de filtrage répond aux besoins de plusieurs sous-systèmes WCF, y compris la messagerie, le routage, la sécurité, la gestion des événements et la gestion du système.  
  
## <a name="filters"></a>Filtres  

 Le moteur de filtre comporte deux composants principaux, les filtres et les tables de filtres. Un filtre prend des décisions booléennes à propos d'un message selon des conditions logiques spécifiées par l'utilisateur. Les filtres implémentent la classe <xref:System.ServiceModel.Dispatcher.MessageFilter>.  
  
 Les méthodes <xref:System.ServiceModel.Dispatcher.MessageFilter.Match%2A> sont utilisées pour déterminer si un message correspond à un filtre. L'une des méthodes teste l'en-tête du message, mais ne peut pas inspecter le corps du message. L’autre méthode prend un *tampon de messages* comme paramètre d’entrée et peut inspecter le corps du message.  
  
 Les filtres ne sont généralement pas testés individuellement mais en tant que parties d'une table de filtres, c'est-à-dire une classe générique créée par la méthode <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601.CreateFilterTable%2A>.  
  
 Chaque type de filtre correspond à un type particulier de condition booléenne. Une fois un filtre construit, vous ne pouvez pas modifier les critères qu'il utilise ; pour modifier les critère d'un filtre, construisez-en un nouveau et supprimez le filtre existant.  
  
### <a name="action-filters"></a>Filtres d'action  

 Le <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> contient une liste de chaînes d'action. Si l'une des actions dans la liste du filtre correspond à l'en-tête Action dans le message ou le tampon de messages, la méthode `Match` retourne la valeur `true`. Si la liste est vide, le filtre est considéré un filtre de correspondance totale et tous les messages ou tampons de messages correspondent, et `Match` retourne la valeur `true`. Si aucune des actions dans la liste du filtre ne correspond à l'en-tête Action dans le message ou le tampon de messages, la méthode `Match` retourne la valeur `false`. S'il n'y a aucune action dans le message et si la liste du filtre n'est pas vide, alors `Match` retourne la valeur `false`.  
  
### <a name="endpoint-address-filters"></a>Filtres de l'adresse du point de terminaison  

 Le <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> filtre les messages et les tampons de messages en fonction d'une adresse de point de terminaison, telle que représentée dans leur collection d'en-têtes. Pour qu'un message passe un tel filtre, les conditions suivantes doivent être remplies :  
  
- L'URI de l'adresse du filtre doit être le même que celui de l'en-tête To du message.  
  
- Chaque paramètre de point de terminaison dans l'adresse du filtre (collection `address.Headers` ) doit trouver un en-tête dans le message à mapper. Des en-tête supplémentaires dans le message ou le tampon de messages sont acceptables pour que la correspondance reste `true`.  
  
### <a name="prefix-endpoint-address-filters"></a>Filtres du préfixe de l'adresse du point de terminaison  
  
1. Le <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> fonctionne comme le filtre <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>, mais la correspondance peut se faire avec le préfixe de l'URI du message. Par exemple, un filtre spécifiant l’adresse `http://www.adatum.com` correspond aux messages adressés à `http://www.adatum.com/userA` .  
  
### <a name="xpath-message-filters"></a>Filtres de message XPath  

 Un <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> utilise une expression XPath pour déterminer si un document XML contient des éléments, des attributs, du texte ou d'autre constructions syntaxiques XML spécifiques. Le filtre se révèle extrêmement efficace pour les sous-ensembles stricts de XPath. Le langage XML Path est décrit dans la [spécification W3C XML Path language 1,0](https://www.w3.org/TR/xpath/all/).  
  
 En général, une application utilise un <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> à un point de terminaison pour interroger le contenu d'un message SOAP puis prend la mesure appropriée en fonction des résultats de cette requête. Par exemple, un processus de mise en file d’attente peut utiliser une requête XPath pour inspecter l’élément de priorité d’un en-tête connu afin de décider s’il faut déplacer un message en haut de la file d’attente.  
  
## <a name="filter-tables"></a>Tables de filtres  

 Les tables de filtres sont utilisées pour stocker des paires clé-valeur, où la clé est un filtre et certaines données associées sont la valeur. Les données du filtre peuvent être utilisées pour indiquer quelles actions doivent être effectuées si un message correspond au filtre et si le type des données du filtre correspond au paramètre générique pour la classe de la table de filtres. Les données de filtre peuvent se composer de règles de routage, de l'état de la sécurité de la session, d'écouteurs sur un canal, et ainsi de suite. Les données peuvent être utilisées là où le contrôle du flux de données est nécessaire.  
  
 Les tables de filtres implémentent l'interface générique <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>.  
  
 Les tables de filtres comprennent plusieurs méthodes qui font correspondre un message à tous les filtres de la table et retournent une collection non ordonnée de filtres ou de données correspondants. Certaines des méthodes de correspondance acceptent plusieurs correspondances et retournent tous les éléments correspondants. D'autres n'acceptent qu'une correspondance unique, ne retournent qu'un seul élément et lèvent une <xref:System.ServiceModel.Dispatcher.MultipleFilterMatchesException> si plusieurs filtres correspondent.  
  
### <a name="message-filter-table"></a>Table de filtres de messages  

 La <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> est l'implémentation la plus générale de <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>. Vous pouvez stocker des filtres de tous les types dans la table.  
  
 Vous pouvez assigner des priorités numériques aux filtres, où la priorité plus élevée est signifiée par le nombre plus élevé. Plusieurs types de filtres peuvent avoir la même priorité. Un type particulier de filtre peut apparaître dans plusieurs niveaux de priorité.  
  
 La correspondance s'effectue en commençant par la priorité la plus élevée, et une fois que les filtres correspondant à une priorité donnée sont trouvés, aucun filtre avec une priorité plus faible n'est examiné. Par conséquent, si vous utilisez une méthode de correspondance à filtre unique, et si plusieurs filtres correspondent à un message, mais que chaque filtre correspondant a une priorité différente, alors aucune exception n'est levée et le filtre avec la priorité la plus élevée est retourné. De la même façon, une méthode de correspondance à filtres multiples retourne uniquement les filtres correspondants avec la priorité la plus élevée.  
  
### <a name="xpath-message-filter-table"></a>Table de filtres de messages XPath  

 La <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> est optimisée pour les filtres XPath déclaratifs ; la clé de la table est donc un <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.  
  
 La classe <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> optimise la correspondance pour un sous-ensemble de XPath qui couvre la plupart des scénarios de messagerie et prend également en charge la grammaire XPath 1.0 complète. Elle comprend des algorithmes optimisés pour une correspondance parallèle efficace.  
  
 Cette table a plusieurs méthodes `Match` spécialisées qui fonctionnent sur un <xref:System.Xml.XPath.XPathNavigator> et un <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator>. Un <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> étend la classe <xref:System.Xml.XPath.XPathNavigator> en ajoutant une propriété <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator.CurrentPosition%2A>. Cette propriété permet d'enregistrer et de charger rapidement des positions dans le document XML sans devoir cloner le navigateur, ce qui représente une allocation de mémoire importante requise par le <xref:System.Xml.XPath.XPathNavigator> pour une telle opération. Le moteur XPath WCF doit fréquemment enregistrer la position du curseur au cours de l’exécution de requêtes sur des documents XML, de sorte que le <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> fournit une optimisation importante pour le traitement des messages.  
  
## <a name="customer-scenarios"></a>Scénarios de client  

 Vous pouvez utiliser le filtrage à chaque fois que vous souhaitez envoyer un message à différents modules de traitement en fonction des données contenues dans le message. Deux scénarios typiques transmettent un message en fonction de son code d'action et démultiplexent un flux de messages en fonction de l'adresse de point de terminaison des messages.  
  
### <a name="routing"></a>Routage  

 L'écouteur d'un point de terminaison écoute les messages qui présentent un ou plusieurs codes d'action dans l'en-tête SOAP du message. Implémentez ceci en créant un <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> en passant un tableau qui contient les codes d'action à son constructeur. Il utilise ce filtre pour s'enregistrer dans `ListenerFactory`, donc seuls les messages dont l'action correspond à l'une des actions du filtre arrivent à ce point de terminaison particulier.  
  
### <a name="de-multiplexing"></a>Démultiplexage  

 Lorsque plusieurs points de terminaison se déploient du même `ServiceListener` provenant du câble, la seule manière de démultiplexer les messages et de savoir s'ils appartiennent à une certaine adresse de point de terminaison est d'utiliser des <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>, qui sélectionnent les messages vers les points de terminaison enregistrés en exécutant une recherche sur les informations stockées dans les en-têtes. Dans ces filtres, les seuls messages qui passent sont ceux qui ont tous les en-têtes correspondants à la fois à :  
  
- L'URI de l'`EndpointAddress`.  
  
- Le reste des paramètres de point de terminaison dans l'`EndpointAddress` comme spécifié dans le <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>.  
  
## <a name="see-also"></a>Voir aussi

- [Transfert de données et sérialisation](data-transfer-and-serialization.md)
