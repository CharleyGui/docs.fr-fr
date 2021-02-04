---
title: 'Modification avec rupture : Kestrel : les attributs du message de journal ont été modifiés'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 6,0 intitulée Kestrel : attributs de message de journal modifiés'
author: scottaddie
ms.author: scaddie
ms.date: 02/01/2021
ms.openlocfilehash: 30b03c22a6c85623fec7db14b58b169f887395a0
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99551559"
---
# <a name="kestrel-log-message-attributes-changed"></a>Kestrel : les attributs de message de journal ont été modifiés

Les ID et les noms des messages du journal Kestrel sont associés. Ces attributs identifient de manière unique différents types de messages de journal. Certains de ces ID et noms n’ont pas été dupliqués correctement. Ce problème de duplication est résolu dans ASP.NET Core 6,0.

## <a name="version-introduced"></a>Version introduite

6.0

## <a name="old-behavior"></a>Ancien comportement

Le tableau suivant indique l’état des messages du journal affectés avant ASP.NET Core 6,0.

| Description du message                   | Nom                    | id |
|---------------------------------------|-------------------------|----|
| Messages du journal des connexions HTTP/2 fermées | `Http2ConnectionClosed` | 36 |
| Images HTTP/2 envoyant des messages de journal     | `Http2FrameReceived`    | 37 |

## <a name="new-behavior"></a>Nouveau comportement

Le tableau suivant indique l’état des messages de journal affectés dans ASP.NET Core 6,0.

| Description du message                   | Nom                    | id |
|---------------------------------------|-------------------------|----|
| Messages du journal des connexions HTTP/2 fermées | `Http2ConnectionClosed` | 48 |
| Images HTTP/2 envoyant des messages de journal     | `Http2FrameSending`     | 49 |

## <a name="reason-for-change"></a>Motif de modification

Les ID de journal et les noms doivent être uniques afin que différents types de messages puissent être identifiés.

## <a name="recommended-action"></a>Action recommandée

Si vous avez du code ou une configuration qui fait référence aux anciens ID et noms, mettez à jour ces références pour utiliser les nouveaux ID et noms.

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
