---
title: Protocole d'échange de contexte
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: ba613a2d12843ad00034057f8bbf08d5357d7f04
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237818"
---
# <a name="context-exchange-protocol"></a>Protocole d'échange de contexte

Cette section décrit le protocole d’échange de contexte introduit dans Windows Communication Foundation (WCF) version .NET Framework version 3,5. Ce protocole permet au canal client d'accepter un contexte fourni par un service et de l'appliquer à toutes les demandes ultérieures à ce service envoyées sur la même instance de canal client. L'implémentation du protocole d'échange de contexte peut utiliser l'un des deux mécanismes suivants pour propager le contexte entre le serveur et le client : les cookies HTTP ou un en-tête SOAP.  
  
 Le protocole d'échange de contexte est implémenté dans une couche de canal personnalisée. Le canal communique le contexte depuis et vers la couche d'application à l'aide d'une propriété <xref:System.ServiceModel.Channels.ContextMessageProperty>. Pour la transmission entre des points de terminaison, la valeur du contexte est soit sérialisée comme un en-tête SOAP à la couche du canal, soit convertie depuis ou vers des propriétés de message qui représentent une réponse et une demande HTTP. Dans le dernier cas, l'une des couches du canal sous-jacents convertie les propriétés de message de réponse et de demande HTTP vers et depuis des cookies HTTP, respectivement. Le choix du mécanisme utilisé pour échanger le contexte s'effectue à l'aide de la propriété <xref:System.ServiceModel.Channels.ContextExchangeMechanism> sur le <xref:System.ServiceModel.Channels.ContextBindingElement>. Les valeurs valides sont `HttpCookie` ou `SoapHeader`.  
  
 Sur le client, une instance d'un canal peut fonctionner selon deux modes basés sur les paramètres de la propriété de canal, <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>.  
  
## <a name="mode-1-channel-context-management"></a>Mode 1 : gestion du contexte de canal  

 Il s'agit du mode par défaut lorsque <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> a la valeur `true`. Dans ce mode, le canal de contexte gère le contexte et met en cache celui-ci pendant sa durée de vie. Le contexte peut être récupéré à partir du canal par le biais de la propriété de canal `IContextManager` en appelant la méthode `GetContext`. Le canal peut également être pré-initialisé avec un contexte spécifique avant d'être ouvert en appelant la méthode `SetContext` sur la propriété de canal. Une fois le canal initialisé avec le contexte, celui-ci ne peut pas être réinitialisé.  
  
 Les éléments suivants sont une liste d'invariants dans ce mode :  
  
- Toute tentative de réinitialisation du contexte à l'aide de `SetContext` après l'ouverture du canal lève une <xref:System.InvalidOperationException>.  
  
- Toute tentative d'envoi du contexte à l'aide du <xref:System.ServiceModel.Channels.ContextMessageProperty> dans un message sortant lève une <xref:System.InvalidOperationException>.  
  
- Si un message est reçu du serveur avec un contexte spécifique, lorsque le canal a déjà été initialisé avec un contexte spécifique, cela lève une <xref:System.ServiceModel.ProtocolException>.  
  
    > [!NOTE]
    > Il est recommandé de recevoir du serveur un contexte initial uniquement si le canal est ouvert sans qu'un contexte soit défini explicitement.  
  
- Le <xref:System.ServiceModel.Channels.ContextMessageProperty> sur le message entrant est toujours null.  
  
## <a name="mode-2-application-context-management"></a>Mode 2 : gestion du contexte d'application  

 Il s'agit du mode dans lequel <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> a la valeur `false`. Dans ce mode, le canal de contexte ne gère pas de contexte. C'est la responsabilité de l'application de récupérer, de gérer et d'appliquer le contexte à l'aide de <xref:System.ServiceModel.Channels.ContextMessageProperty>. Toute tentative d'appel de `GetContext` ou de `SetContext` lève une <xref:System.InvalidOperationException>.  
  
 Quel que soit le mode choisi, la fabrication de canal du client prend en charge les modèles d'échange de messages <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel> et <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.  
  
 Sur le service, une instance du canal est chargée de convertir le contexte fourni par le client sur les messages entrants en <xref:System.ServiceModel.Channels.ContextMessageProperty>. Puis la propriété de message peut être accédée par la couche d'application ou d'autres canaux plus loin dans la pile d'appel. Les canaux de service permettent aussi à la couche d'application de spécifier une nouvelle valeur de contexte à propager en retour au client en joignant un <xref:System.ServiceModel.Channels.ContextMessageProperty> au message de réponse. Cette propriété est convertie en en-tête SOAP ou cookie HTTP qui contient le contexte, ce qui dépend de la configuration de la liaison. L'écouteur de canal de service prend en charge <xref:System.ServiceModel.Channels.IReplyChannel>, <xref:System.ServiceModel.Channels.IReplySessionChannel> et les modèles d'échange de messages <xref:System.ServiceModel.Channels.IReplySessionChannel>.  
  
 Le protocole d'échange de contexte introduit un nouvel en-tête SOAP `wsc:Context` pour représenter les informations de contexte lorsque les cookies HTTP ne sont pas utilisés pour propager le contexte. Le schéma d'en-tête de contexte permet un nombre illimité d'éléments enfants, chacun avec une clé de chaîne et un contenu de chaîne. Les éléments suivants sont un exemple d'un en-tête de contexte.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 En mode `HttpCookie`, les cookies sont définis à l'aide de l'en-tête `SetCookie`. Le nom du cookie est `WscContext`. La valeur du cookie est l'encodage Base64 de l'en-tête `wsc:Context`. Cette valeur est mise entre guillemets.  
  
 La valeur du contexte doit être protégée des changements au cours du transit pour les mêmes raisons  que les en-têtes WS-Addressing sont protégés. L'en-tête est utilisé pour déterminer vers où distribuer la demande sur le service. L’en-tête `wsc:Context` est requis par conséquent pour être signé numériquement ou signé et chiffré au niveau du transport ou de SOAP lorsque la liaison offre une fonction de protection des messages. Lorsque les cookies HTTP sont utilisés pour propager le contexte, ils doivent être protégés à l'aide de la sécurité de transport.  
  
 Les points de terminaison de service qui requièrent la prise en charge du protocole de l'échange de contexte peuvent l'indiquer explicitement dans la stratégie publiée. Deux nouvelles assertions de stratégie ont été introduites pour représenter la spécification de la prise en charge du protocole d'échange de contexte par le client au niveau de SOAP ou pour activer la prise en charge des cookies HTTP. La génération de ces assertions dans la stratégie sur le service est contrôlée par la valeur de la propriété <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> de la façon suivante :  
  
- Pour <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>, l'assertion suivante est générée :  
  
    ```xml  
    <IncludeContext
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
- Pour <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>, l'assertion suivante est générée :  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Guide de l'interopérabilité des protocoles de services Web](web-services-protocols-interoperability-guide.md)
