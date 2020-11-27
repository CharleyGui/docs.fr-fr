---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: 97f22a01df84c39915f74fa7677e5dd18154b952
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256220"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a>System.ServiceModel.Channels.HttpChannelMessageReceiveFailed

Échec de la réception d'un message sur un canal HTTP.  
  
## <a name="description"></a>Description  

 Ce suivi peut être émis comme avertissement ou erreur. Dans les deux cas, le suivi est émis lorsqu'un écouteur compatible est introuvable pour une demande HTTP entrante et que la demande est rejetée. Cela peut se produire si le verbe HTTP de la demande n'a pas été reconnu pas un écouteur HTTP ou si aucun écouteur n'écoutait sur l'adresse à laquelle la demande était destinée. Le suivi est émis comme avertissement en cas d'auto-hébergement et comme erreur lorsque le service est hébergé dans IIS.  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../index.md)
