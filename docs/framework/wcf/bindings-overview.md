---
title: Vue d’ensemble des liaisons Windows Communication Foundation
description: En savoir plus sur les liaisons, qui spécifient comment se connecter à un service WCF, y compris les éléments d’une liaison et comment spécifier une liaison pour un point de terminaison de service.
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
ms.openlocfilehash: e918844342a20e7b6c22ef6a9fd3c01fe27db059
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272473"
---
# <a name="windows-communication-foundation-bindings-overview"></a>Vue d’ensemble des liaisons Windows Communication Foundation

Les liaisons sont des objets utilisés pour spécifier les détails de communication requis pour se connecter au point de terminaison d’un service Windows Communication Foundation (WCF). Chaque point de terminaison d'un service WCF requiert la définition correcte d'une liaison. Cette rubrique décrit les types de détails de communication définis par les liaisons, les éléments d’une liaison, les liaisons incluses dans WCF et comment une liaison peut être spécifiée pour un point de terminaison.  
  
## <a name="what-a-binding-defines"></a>Ce que définit une liaison  

 Les informations contenues dans une liaison peuvent être basiques ou très complexes. La liaison la plus basique spécifie uniquement le protocole de transport (par exemple HTTP) qui doit être utilisé pour se connecter au point de terminaison. Plus généralement, les informations qu’une liaison contient concernant la connexion à un point de terminaison appartiennent à l’une des catégories suivantes :  
  
 **Protocoles**  
 Détermine le mécanisme de sécurité utilisé : soit une fonction de messagerie fiable, soit des paramètres de flux de contexte de transaction.  
  
 **Encodage**  
 Détermine l'encodage de message (par exemple, texte ou binaire).  
  
 **Transport**  
 Détermine le protocole de transport sous-jacent à utiliser (par exemple, TCP ou HTTP).  
  
## <a name="the-elements-of-a-binding"></a>Les éléments d’une liaison  

 Une liaison est constituée fondamentalement d’une pile ordonnée d’éléments de liaison, chacun spécifiant une partie des informations de communication requises pour se connecter à un point de terminaison de service. Les deux couches inférieures de la pile sont requises. À la base de la pile se trouve l'élément de liaison de transport, et juste au-dessus de celui-ci se trouve l'élément qui contient les spécifications d'encodage de message. Les éléments de liaison facultatifs qui spécifient les autres protocoles de communication sont disposés en couches sur ces deux éléments requis. Pour plus d’informations sur ces éléments de liaison et leur classement correct, consultez [liaisons personnalisées](./extending/custom-bindings.md).  
  
## <a name="system-provided-bindings"></a>Liaisons fournies par le système  

 Les informations contenues dans une liaison peuvent être complexes et certains paramètres peuvent ne pas être compatibles avec d’autres. Pour cette raison, WCF comprend un ensemble de liaisons fournies par le système. Ces liaisons sont conçues pour couvrir la plupart des exigences d’applications. Les classes suivantes représentent quelques exemples de liaisons fournies par le système :  
  
- <xref:System.ServiceModel.BasicHttpBinding> : une liaison de protocole HTTP adaptée à la connexion à des services Web conformes à la spécification WS-I Basic Profile (par exemple, services basés sur les services Web ASP.NET).  
  
- <xref:System.ServiceModel.WSHttpBinding>: une liaison interopérable adaptée à la connexion à des points de terminaison conformes aux protocoles WS-*.  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>: Utilise la .NET Framework pour se connecter à d’autres points de terminaison WCF sur le même ordinateur.  
  
- <xref:System.ServiceModel.NetMsmqBinding>: Utilise la .NET Framework pour créer des connexions de message en file d’attente avec d’autres points de terminaison WCF.  

- <xref:System.ServiceModel.NetTcpBinding>: Cette liaison offre des performances supérieures à celles des liaisons HTTP et est idéale pour une utilisation dans un réseau local.
  
 Pour obtenir une liste complète, avec des descriptions, de toutes les liaisons fournies par WCF, consultez [liaisons fournies](system-provided-bindings.md)par le système.  
  
## <a name="using-your-own-bindings"></a>Utilisation de vos propres liaisons  

 Si aucune des liaisons fournies par le système ne possède la bonne combinaison de fonctionnalités requise par une application de service, vous pouvez créer votre propre liaison. Il existe deux façons d'effectuer cette opération. Vous pouvez soit créer une liaison à partir d'éléments de liaison préexistants à l'aide d'un objet <xref:System.ServiceModel.Channels.CustomBinding>, soit créer une liaison entièrement définie par l'utilisateur en dérivant de la liaison <xref:System.ServiceModel.Channels.Binding>. Pour plus d’informations sur la création de votre propre liaison à l’aide de ces deux approches, consultez [liaisons personnalisées](./extending/custom-bindings.md) et [création de liaisons de User-Defined](./extending/creating-user-defined-bindings.md).  
  
## <a name="using-bindings"></a>Utilisation des liaisons  

 L’utilisation des liaisons implique deux étapes simples :  
  
1. Sélectionner ou définir une liaison. La méthode la plus simple consiste à choisir l’une des liaisons fournies par le système incluses avec WCF et à l’utiliser avec ses paramètres par défaut. Vous pouvez également choisir une liaison fournie par le système et réinitialiser ses valeurs de propriété en fonction de vos spécifications. En guise d’alternative, vous pouvez créer une liaison personnalisée ou une liaison définie par l’utilisateur afin de disposer d’un degré de contrôle et de personnalisation plus élevé.  
  
2. Créer un point de terminaison qui utilise la liaison sélectionnée ou définie.  
  
## <a name="code-and-configuration"></a>Code et configuration  

 Vous pouvez définir des liaisons de deux manières : par le biais de code ou par configuration. Ces deux approches ne dépendent pas du fait que vous utilisez une liaison fournie par le système ou une liaison personnalisée. En général, l’utilisation de code procure un contrôle total sur la définition d’une liaison au moment du design. L’utilisation de la configuration, en revanche, permet à un administrateur système ou à l’utilisateur d’un service ou client WCF de modifier les paramètres d’une liaison sans devoir recompiler l’application de service. Cette souplesse est souvent souhaitable, car il n’existe aucun moyen de prédire des besoins spécifiques de l’ordinateur sur lesquels une application WCF doit être déployée. Le fait de conserver les informations de liaison (et d’adressage) hors du code leur permet de changer sans nécessiter de recompilation ou de redéploiement de l’application. Notez que les liaisons définies dans le code sont créées après les liaisons spécifiées dans la configuration, ce qui permet aux liaisons définies dans le code de remplacer celles définies par configuration.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de liaisons pour configurer des services et des clients](using-bindings-to-configure-services-and-clients.md)
