---
title: Comparaison des services Web ASP.NET et de WCF en fonction de l'objectif et des normes utilisées
ms.date: 03/30/2017
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
ms.openlocfilehash: 62917d7a188d0863f6ebcb7dd3531ef2dd6a5132
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295065"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>Comparaison des services Web ASP.NET et de WCF en fonction de l'objectif et des normes utilisées

Les services Web ASP.NET ont été développés pour générer des applications qui envoient et reçoivent des messages à l'aide du protocole SOAP (Simple Object Access Protocol) sur HTTP. La structure des messages peut être définie à l'aide d'un schéma XML et un outil est fourni pour faciliter la sérialisation des messages vers et à partir d'objets .NET Framework. La technologie peut générer automatiquement des métadonnées afin de décrire des services Web dans le langage WSDL (Web Services Description Language) et un deuxième outil est fourni pour générer des clients pour les services Web à partir du WSDL.  
  
 WCF permet à .NET Framework applications d’échanger des messages avec d’autres entités logicielles. SOAP est utilisé par défaut, mais les messages peuvent se présenter sous tout format et sont acheminés en utilisant tout protocole de transport. La structure des messages peut être définie à l'aide d'un schéma XML et il existe plusieurs options de sérialisation des messages vers et à partir d'objets .NET Framework. WCF peut générer automatiquement des métadonnées pour décrire les applications générées à l’aide de la technologie dans WSDL, et il fournit également un outil pour générer des clients pour ces applications à partir du WSDL.  
  
 Les normes prises en charge par les services Web ASP.NET sont documentées dans les [avantages des services Web XML créés à l’aide de ASP.net](/previous-versions/dotnet/netframework-4.0/0859ebft(v=vs.100)). La liste la plus complète de normes prises en charge par WCF est répertoriée dans les [protocoles de services Web pris en charge par System-Provided liaisons d’interopérabilité](web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
## <a name="see-also"></a>Voir aussi

- [Comparaison des services Web ASP.NET et de WCF du point de vue du développement](comparing-aspnet-web-services-to-wcf-based-on-development.md)
