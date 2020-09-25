---
title: Confidentialité et sécurité des données
ms.date: 03/30/2017
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
ms.openlocfilehash: b0721cbc4957dfe64627f3a18064110f96a26f2b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177382"
---
# <a name="privacy-and-data-security"></a>Confidentialité et sécurité des données

La protection et la gestion d'informations sensibles dans une application ADO.NET dépendent des produits et des technologies sous-jacents, utilisés pour les créer. ADO.NET ne fournit pas directement de services pour la sécurisation ou le chiffrement des données.  
  
## <a name="cryptography-and-hash-codes"></a>Chiffrement et codes de hachage  

 Les classes figurant dans l'espace de noms .NET Framework <xref:System.Security.Cryptography> peuvent être utilisées à partir de vos applications ADO.NET pour empêcher la lecture et la modification des données par des tiers non autorisés. Certaines classes sont des wrappers pour l'interface Microsoft CryptoAPI non managée, tandis que d'autres sont des implémentations managées. La rubrique [services de chiffrement](../../../standard/security/cryptographic-services.md) fournit une vue d’ensemble du chiffrement dans le .NET Framework, décrit comment dont le chiffrement est implémenté et comment vous pouvez effectuer des tâches de chiffrement spécifiques.  
  
 À la différence du chiffrement qui permet de chiffrer, puis de déchiffrer des données, le hachage des données est un processus à sens unique. Le hachage des données est utile lorsque vous souhaitez empêcher la falsification en vérifiant que les données n'ont pas été altérées : à partir de chaînes d'entrée identiques, les algorithmes de hachage produisent toujours des valeurs de sortie courtes identiques qui peuvent être facilement comparées. [Garantir l’intégrité des données avec des codes de hachage](../../../standard/security/ensuring-data-integrity-with-hash-codes.md) explique comment générer et vérifier des valeurs de hachage.  
  
## <a name="encrypting-configuration-files"></a>Chiffrement des fichiers de configuration  

 La protection de l'accès à votre source de données représente l'un de vos principaux objectifs lorsque vous sécurisez une application. Une chaîne de connexion présente une vulnérabilité potentielle si elle n'est pas sécurisée. Les chaînes de connexion enregistrées dans les fichiers de configuration sont stockées dans des fichiers XML standard pour lesquels le .NET Framework a défini un ensemble commun d'éléments. La configuration protégée vous permet de chiffrer les informations sensibles dans un fichier de configuration. Bien qu'elle ait été conçu à l'origine pour les applications ASP.NET, la configuration protégée peut également servir à chiffrer les sections des fichiers de configuration dans les applications Windows. Pour plus d’informations, consultez [Protection des informations de connexion](protecting-connection-information.md).  
  
## <a name="securing-string-values-in-memory"></a>Sécurisation de valeurs de chaîne en mémoire  

 Si un objet <xref:System.String> contient des informations sensibles, telles qu'un mot de passe, un numéro de carte de crédit ou des données personnelles, il existe un risque que ces informations soient révélées après leur utilisation car l'application ne peut pas supprimer les données de la mémoire de l'ordinateur.  
  
 Un objet <xref:System.String> est immuable ; sa valeur ne peut pas être modifiée une fois que l'objet a été créé. Les modifications qui semblent modifier la valeur de chaîne créent en fait une nouvelle instance d'un objet <xref:System.String> en mémoire, stockant les données sous forme de texte brut. En outre, il n'est pas possible de prédire quand les instances de chaîne seront supprimées de la mémoire. La récupération de la mémoire avec des chaînes n'est pas déterministe avec le garbage collection .NET. Vous devez éviter d'utiliser les classes <xref:System.String> et <xref:System.Text.StringBuilder> si vos données sont réellement sensibles.  
  
 La classe <xref:System.Security.SecureString> fournit des méthodes pour le chiffrement du texte à l'aide de l'API de protection des données (DPAPI) en mémoire. La chaîne est ensuite supprimée de la mémoire lorsqu'elle n'est plus utile. Il n'existe aucune méthode `ToString` pour lire rapidement le contenu d'une classe <xref:System.Security.SecureString>. Vous pouvez initialiser une nouvelle instance de `SecureString` sans valeur ou en lui passant un pointeur vers un tableau d'objets <xref:System.Char>. Vous pouvez ensuite utiliser les différentes méthodes de la classe pour travailler avec la chaîne.
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](securing-ado-net-applications.md)
- [Sécurité SQL Server](./sql/sql-server-security.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
