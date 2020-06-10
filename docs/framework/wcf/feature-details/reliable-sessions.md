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
# <a name="reliable-sessions"></a><span data-ttu-id="a6c5f-102">Sessions fiables</span><span class="sxs-lookup"><span data-stu-id="a6c5f-102">Reliable Sessions</span></span>

<span data-ttu-id="a6c5f-103">Cette section décrit la session fiable Windows Communication Foundation (WCF), son utilisation, comment et quand l’utiliser, les configurations de liaison qui la prennent en charge et les pointeurs sur les meilleures pratiques.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-103">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="a6c5f-104">Le tableau suivant résume les détails sur les points essentiels et les rubriques connexes de cette section.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="a6c5f-105">La session fiable WCF offre des fonctionnalités qui garantissent que les messages envoyés entre les points de terminaison sont transférés sur des intermédiaires SOAP ou de transport et ne sont remis qu’une seule fois et, éventuellement, dans l’ordre dans lequel ils ont été envoyés.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-105">The reliable session WCF provides features ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="a6c5f-106">Pour utiliser une session fiable avec une application WCF, utilisez l’une des liaisons fournies par le système dans WCF qui prennent en charge une session fiable par défaut ou en tant qu’option, ou créez votre propre liaison personnalisée qui prend en charge la session.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-106">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a6c5f-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a6c5f-107">In This Section</span></span>

<span data-ttu-id="a6c5f-108">[Vue d’ensemble des sessions fiables](reliable-sessions-overview.md) Décrit les sessions fiables, quand les utiliser, les différentes liaisons qui prennent en charge des sessions fiables et comment elles fonctionnent.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-108">[Reliable Sessions Overview](reliable-sessions-overview.md) Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="a6c5f-109">[Comment : échanger des messages au sein d’une session fiable](how-to-exchange-messages-within-a-reliable-session.md) Décrit comment créer une session fiable sur HTTP à l’aide d’une liaison personnalisée spécifiée dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-109">[How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md) Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="a6c5f-110">[Comment : sécuriser des messages dans des sessions fiables](how-to-secure-messages-within-reliable-sessions.md) Décrit comment sécuriser une session fiable.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-110">[How to: Secure Messages within Reliable Sessions](how-to-secure-messages-within-reliable-sessions.md) Describes how to secure a reliable session.</span></span>

<span data-ttu-id="a6c5f-111">[Comment : créer une liaison de session fiable personnalisée avec HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Décrit comment créer une session fiable sur HTTPs.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-111">[How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="a6c5f-112">[Meilleures pratiques pour les sessions fiables](best-practices-for-reliable-sessions.md) Décrit quelques-unes des meilleures pratiques associées à l’utilisation d’une session fiable.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-112">[Best Practices for Reliable Sessions](best-practices-for-reliable-sessions.md) Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="a6c5f-113">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="a6c5f-113">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="a6c5f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6c5f-114">See also</span></span>

- [<span data-ttu-id="a6c5f-115">Files d'attente et sessions fiables</span><span class="sxs-lookup"><span data-stu-id="a6c5f-115">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
- [<span data-ttu-id="a6c5f-116">Sessions, instanciation et concurrence</span><span class="sxs-lookup"><span data-stu-id="a6c5f-116">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)
