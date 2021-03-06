---
title: WCF et WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: 2ee27eef015ee8c2fbee8360b444343a1c757097
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281584"
---
# <a name="wcf-and-websockets"></a>WCF et WebSockets

.NET Framework 4.5 introduit la prise en charge de WebSockets dans Windows Communication Foundation.  WebSockets est une technologie efficace basée sur des normes qui permet la communication bidirectionnelle sur les ports HTTP standard 80 et 443. L'utilisation des ports HTTP standard permet à WebSockets de communiquer sur le Web via des intermédiaires.  Deux nouvelles liaisons standard ont été ajoutées pour prendre en charge les communications via un transport WebSocket. Voir <xref:System.ServiceModel.NetHttpBinding> et <xref:System.ServiceModel.NetHttpsBinding>. Les paramètres spécifiques à WebSocket peuvent être configurés sur le <xref:System.ServiceModel.Channels.HttpTransportBindingElement> en accédant à la <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> propriété.
  
## <a name="in-this-section"></a>Dans cette section  

 [Utilisation de NetHttpBinding](using-the-nethttpbinding.md)  
 Décrit <xref:System.ServiceModel.NetHttpBinding> et la façon de le configurer.  
  
 [Procédure : créer un service WCF qui communique sur WebSockets](how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 Décrit comment créer un service WCF qui communique sur WebSockets  
  
## <a name="reference"></a>Informations de référence  
  
## <a name="related-sections"></a>Sections connexes
