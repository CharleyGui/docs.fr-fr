---
title: Sessions fiables
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 910ad952192243c6aa8a79417ad711d8c2a4ba2e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590538"
---
# <a name="reliable-sessions"></a>Sessions fiables

Cette section décrit la session fiable Windows Communication Foundation (WCF), son utilisation, comment et quand l’utiliser, les configurations de liaison qui la prennent en charge et les pointeurs sur les meilleures pratiques. Le tableau suivant résume les détails sur les points essentiels et les rubriques connexes de cette section.

La session fiable WCF offre des fonctionnalités qui garantissent que les messages envoyés entre les points de terminaison sont transférés sur des intermédiaires SOAP ou de transport et ne sont remis qu’une seule fois et, éventuellement, dans l’ordre dans lequel ils ont été envoyés.

Pour utiliser une session fiable avec une application WCF, utilisez l’une des liaisons fournies par le système dans WCF qui prennent en charge une session fiable par défaut ou en tant qu’option, ou créez votre propre liaison personnalisée qui prend en charge la session.

## <a name="in-this-section"></a>Dans cette section

[Vue d’ensemble des sessions fiables](reliable-sessions-overview.md) Décrit les sessions fiables, quand les utiliser, les différentes liaisons qui prennent en charge des sessions fiables et comment elles fonctionnent.

[Comment : échanger des messages au sein d’une session fiable](how-to-exchange-messages-within-a-reliable-session.md) Décrit comment créer une session fiable sur HTTP à l’aide d’une liaison personnalisée spécifiée dans la configuration.

[Comment : sécuriser des messages dans des sessions fiables](how-to-secure-messages-within-reliable-sessions.md) Décrit comment sécuriser une session fiable.

[Comment : créer une liaison de session fiable personnalisée avec HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Décrit comment créer une session fiable sur HTTPs.

[Meilleures pratiques pour les sessions fiables](best-practices-for-reliable-sessions.md) Décrit quelques-unes des meilleures pratiques associées à l’utilisation d’une session fiable.

## <a name="reference"></a>Informations de référence

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>Voir aussi

- [Files d'attente et sessions fiables](queues-and-reliable-sessions.md)
- [Sessions, instanciation et concurrence](sessions-instancing-and-concurrency.md)
