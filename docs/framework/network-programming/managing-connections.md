---
title: Gestion des connexions
description: Découvrez comment les applications qui utilisent HTTP pour les ressources de données peuvent utiliser les classes .NET Framework ServicePoint et ServicePointManager pour gérer les connexions.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, connections
- HTTP, classes for connecting
- requesting data from Internet, connections
- sending data, connections
- receiving data, connections
- ServicePoint class, about ServicePoint class
- response to Internet request, connections
- connections [.NET Framework], classes
- network resources, connections
- downloading Internet resources, connections
- ServicePointManager class, about ServicePointManager class
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
ms.openlocfilehash: 124dff1b104e323b929d13f73cf17d740e747c32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502286"
---
# <a name="managing-connections"></a>Gestion des connexions
Les applications qui utilisent HTTP pour se connecter aux ressources de données peuvent utiliser les classes <xref:System.Net.ServicePoint> et <xref:System.Net.ServicePointManager> du .NET Framework pour gérer les connexions à Internet et les aider à atteindre des performances et une évolutivité optimales.  
  
 La classe **ServicePoint** fournit une application avec un point de terminaison auquel l’application peut se connecter pour accéder aux ressources Internet. Chaque **ServicePoint** contient des informations qui vous aident à optimiser les connexions à un serveur Internet en partageant les informations d’optimisation entre les connexions pour améliorer les performances.  
  
 Chaque **ServicePoint** est identifié par un URI et est classé selon l’identificateur du schéma et les fragments d’hôte de l’URI. Par exemple, une même instance **ServicePoint** peut envoyer des requêtes aux URI `http://www.contoso.com/index.htm` et `http://www.contoso.com/news.htm?date=today`, car ces requêtes ont le même identificateur de schéma (http) et les mêmes fragments d’hôte (`www.contoso.com`). Si l’application a déjà une connexion permanente au serveur `www.contoso.com`, elle utilise cette connexion pour récupérer les deux requêtes, ce qui lui évite de créer deux connexions.  
  
 **ServicePointManager** est une classe statique qui gère la création et la destruction des instances **ServicePoint**. **ServicePointManager** crée un **ServicePoint** lorsque l’application demande une ressource Internet qui ne figure pas dans la collection existante d’instances **ServicePoint**. Les instances **ServicePoint** sont détruites lorsqu’elles ont dépassé leur durée d’inactivité maximale ou lorsque le nombre d’instances **ServicePoint** existantes dépasse le nombre maximal d’instances **ServicePoint** de l’application. Vous pouvez contrôler la durée d’inactivité maximale par défaut et le nombre maximal d’instances **ServicePoint** en définissant les propriétés <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> et <xref:System.Net.ServicePointManager.MaxServicePoints%2A> du **ServicePointManager**.  
  
 Le nombre de connexions entre un client et un serveur peut avoir un impact considérable sur le débit de l’application. Par défaut, une application qui utilise la classe <xref:System.Net.HttpWebRequest> utilise au maximum deux connexions persistantes à un serveur donné. Toutefois, vous pouvez définir le nombre maximal de connexions sur chaque application.  
  
> [!NOTE]
> La spécification HTTP/1.1 limite le nombre de connexions d’une application à deux connexions par serveur.  
  
 Le nombre optimal de connexions dépend des conditions réelles dans lesquelles l’application s’exécute. L’augmentation du nombre de connexions disponibles pour l’application n’affecte pas nécessairement les performances de l’application. Pour déterminer l’impact d’un plus grand nombre de connexions, exécutez des tests de performances avec différents nombres de connexions. Vous pouvez modifier le nombre de connexions qu’utilise une application en modifiant la propriété statique <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> dans la classe **ServicePointManager** lors de l’initialisation de l’application, comme indiqué dans l’exemple de code suivant.  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 La modification de la propriété **ServicePointManager.DefaultConnectionLimit** n’affecte pas les instances de **ServicePoint** précédemment initialisées. Le code suivant change le nombre limite de connexions d’un **ServicePoint** existant pour le serveur `http://www.contoso.com` par la valeur stockée dans `newLimit`.  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## <a name="see-also"></a>Voir aussi

- [Regroupement de connexions](connection-grouping.md)
- [Utilisation de protocoles d’application](using-application-protocols.md)
