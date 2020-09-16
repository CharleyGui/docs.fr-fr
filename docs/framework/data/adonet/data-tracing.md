---
title: Traçage de données
ms.date: 03/30/2017
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
ms.openlocfilehash: 5fe04d6b6146079db7d4e110a94ced361949998c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557108"
---
# <a name="data-tracing-in-adonet"></a>Traçage de données dans ADO.NET

ADO.NET intègre une fonctionnalité de traçage de données intégrée qui est prise en charge par les fournisseurs de données .NET pour SQL Server, Oracle, OLE DB et ODBC, ainsi que les <xref:System.Data.DataSet> protocoles de réseau SQL Server et de ADO.net.

Le traçage d'appels API d'accès aux données peut aider à diagnostiquer les problèmes suivants :

- discordance de schéma entre le programme client et la base de données ;

- problèmes d'indisponibilité de base de données ou de bibliothèque réseau ;

- SQL incorrect qu'il soit en codage dur ou généré par une application ;

- logique de programmation incorrecte ;

- problèmes résultant de l'interaction entre plusieurs composants ADO.NET ou entre ADO.NET et vos propres composants.

Pour prendre en charge plusieurs technologies de traçage, le traçage est extensible, de sorte qu'un développeur peut tracer un problème à tout niveau de la pile d'applications. Bien que le traçage ne soit pas une fonctionnalité purement ADO.NET, les fournisseurs Microsoft tirent parti des API de suivi et d’instrumentation généralisées.

Pour plus d’informations sur la définition et la configuration du suivi managé dans ADO.NET, consultez [suivi de l’accès aux données](/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10)).

## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Accès aux informations de diagnostic dans le journal des événements étendus

Dans la Fournisseur de données .NET Framework pour SQL Server, le suivi de l’accès aux données ([suivi d’accès aux données](/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10))) a été mis à jour pour faciliter la corrélation des événements clients avec les informations de diagnostic, telles que les échecs de connexion, à partir de la mémoire tampon en anneau de connectivité du serveur et des informations de performances de l’application dans le journal des événements étendus. Pour plus d’informations sur la lecture du journal des événements étendus, consultez [Afficher des données de session d’événements](/previous-versions/sql/sql-server-2012/hh710068(v=sql.110)).

Pour les opérations de connexion, ADO.NET envoie un ID de connexion client. Si la connexion échoue, vous pouvez accéder à la mémoire tampon en anneau de connectivité ([résolution des problèmes de connectivité dans SQL Server 2008 avec la mémoire tampon en anneau de connectivité](/archive/blogs/sql_protocols/connectivity-troubleshooting-in-sql-server-2008-with-the-connectivity-ring-buffer)) et rechercher le `ClientConnectionID` champ et obtenir des informations de diagnostic sur l’échec de la connexion. Les ID de connexion du client sont enregistrés dans la mémoire tampon en anneau uniquement en cas d'erreur. (Si une connexion échoue avant d'envoyer le paquet de préconnexion, un ID de connexion client ne sera pas généré.) L'ID de connexion client est un GUID à 16 octets. Vous pouvez également rechercher l'ID de connexion client dans la sortie cible d'événements étendus, si l'action `client_connection_id` est ajoutée aux événements dans une session d'événements étendus. Vous pouvez activer le traçage d'accès aux données, réexécuter la commande de connexion et observer le champ `ClientConnectionID` dans la trace d'accès aux données, si vous avez besoin d'obtenir une aide supplémentaire pour le diagnostic du pilote client.

Vous pouvez obtenir l'ID de connexion client par programme à l'aide de la propriété `SqlConnection.ClientConnectionID`.

`ClientConnectionID` est disponible pour un objet <xref:System.Data.SqlClient.SqlConnection> qui établit une connexion. Si une tentative de connexion échoue, `ClientConnectionID` peut être disponible via `SqlException.ToString`.

ADO.NET envoie également un ID d'activité propre au thread L’ID d’activité est capturé dans les sessions événements étendus si les sessions sont démarrées avec l’option TRACK_CAUSALITY activée. En cas de problèmes de performances avec une connexion active, vous pouvez obtenir l'ID d'activité de la trace d'accès aux données du client (champ `ActivityID`), puis rechercher l'ID d'activité dans la sortie des événements étendus. L'ID d'activité dans des événements étendus est un GUID de 16 octets (différent du GUID de l'ID de connexion client) ajouté à un numéro séquentiel à quatre octets. Le numéro séquentiel représente l'ordre d'une demande dans un thread et indique l'ordre relatif du traitement par lot et des instructions RPC pour le thread. `ActivityID` est actuellement éventuellement envoyé pour les instructions par lots SQL et les demandes RPC lorsque le suivi de l'accès aux données est activé et le 18e bit dans le mot de configuration de suivi d'accès aux données est activé.

Voici un exemple qui utilise Transact-SQL pour démarrer une session d’événements étendus qui sera stockée dans une mémoire tampon en anneau et enregistrera l’ID d’activité envoyé par un client sur les opérations de traitement par lots et RPC.

```sql
create event session MySession on server
add event connectivity_ring_buffer_recorded,
add event sql_statement_starting (action (client_connection_id)),
add event sql_statement_completed (action (client_connection_id)),
add event rpc_starting (action (client_connection_id)),
add event rpc_completed (action (client_connection_id))
add target ring_buffer with (track_causality=on)
```

## <a name="see-also"></a>Voir aussi

- [Traçage réseau dans le .NET Framework](../../network-programming/network-tracing.md)
- [Traçage et instrumentation d’applications](../../debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
