---
title: Création de requêtes Internet
description: Découvrez comment les applications créent des instances de WebRequest par le biais de la méthode WebRequest. Create, qui crée une classe dérivée basée sur le modèle d’URI qui lui est passé.
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 389c7bf5969eca4322aa680a6f28dec0b899709a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325635"
---
# <a name="create-internet-requests"></a>Créer des demandes Internet

Les applications créent des instances de <xref:System.Net.WebRequest> par le biais de la méthode <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>. <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>est une méthode statique qui crée une classe dérivée de <xref:System.Net.WebRequest> selon le schéma d’URI qui lui est passé.  
  
## <a name="web-file-and-ftp-requests"></a>Requêtes Web, de fichier et FTP

.NET Framework fournit la <xref:System.Net.HttpWebRequest> classe, dérivée de `WebRequest` , pour gérer les requêtes HTTP et HTTPS. Dans la plupart des cas, la `WebRequest` classe fournit toutes les propriétés dont vous avez besoin pour effectuer une requête. Toutefois, si nécessaire, vous pouvez convertir les `WebRequest` objets créés par la `WebRequest.Create` méthode vers le `HttpWebRequest` type pour accéder aux propriétés spécifiques à http de la demande. De même, l' `HttpWebResponse` objet gère les réponses des requêtes http et HTTPS. Pour accéder aux propriétés spécifiques à HTTP de l' `HttpWebResponse` objet, vous devez effectuer un cast des `WebResponse` objets vers le `HttpWebResponse` type.  
  
.NET Framework fournit également les <xref:System.Net.FileWebRequest> <xref:System.Net.FileWebResponse> classes et pour gérer les demandes de ressources qui utilisent le modèle d’URI « file : ». De même, les classes <xref:System.Net.FtpWebRequest> et <xref:System.Net.FtpWebResponse> sont fournies pour gérer les requêtes pour les ressources qui utilisent le schéma d’URI « ftp: ». Si votre demande concerne une ressource qui utilise l’un de ces schémas, vous pouvez utiliser la `WebRequest.Create` méthode pour obtenir un objet avec lequel effectuer votre demande.  
  
Pour gérer les requêtes qui utilisent d’autres protocoles au niveau de l’application, implémentez des classes spécifiques au protocole dérivées de `WebRequest` et `WebResponse` . Pour plus d’informations, consultez [programmation de protocoles enfichables](programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour demander des données à l’aide de la classe WebRequest](how-to-request-data-using-the-webrequest-class.md)
- [Demande de données](requesting-data.md)
